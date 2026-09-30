---
layout: post
title: "Durcissement d'un serveur Debian 13 inspiré du guide ANSSI-BP-028"
context: Lab personnel
summary: Application sur une VM isolée des sept mesures de durcissement qui apportent le plus de sécurité, en m'appuyant sur les recommandations de l'ANSSI pour les systèmes GNU/Linux.
stack: [Debian 13, VirtualBox, SSH, nftables, fail2ban, unattended-upgrades]
---

<!-- Les extraits de configuration ci-dessous sont génériques : remplace-les par tes vrais fichiers. -->

## Objectif

Le guide **ANSSI-BP-028** regroupe les recommandations de l'ANSSI pour configurer un système GNU/Linux de façon sécurisée. Plutôt que d'appliquer tout le référentiel d'un coup, j'ai choisi de commencer par un socle de sept mesures à fort impact, que je comprends et que j'ai vérifiées une par une.

## Environnement

- VM **Debian 13 (Trixie)** isolée, sous VirtualBox
- Machine hôte sous Ubuntu

## Les sept mesures appliquées

### 1. Mettre le système à jour

```bash
sudo apt update && sudo apt full-upgrade
```

### 2. Automatiser les mises à jour de sécurité

Une faille corrigée n'est utile que si le correctif est installé.

```bash
sudo apt install unattended-upgrades
sudo dpkg-reconfigure -plow unattended-upgrades
```

### 3. Verrouiller le compte root

L'administration passe par `sudo` avec un compte nominatif, ce qui trace qui fait quoi.

```bash
sudo passwd -l root
```

### 4. SSH par clé uniquement

```
# /etc/ssh/sshd_config
PermitRootLogin no
PasswordAuthentication no
PubkeyAuthentication yes
```

### 5. Pare-feu nftables : tout refuser sauf le nécessaire

```
table inet filter {
  chain input {
    type filter hook input priority 0; policy drop;
    ct state established,related accept
    iif "lo" accept
    tcp dport 22 accept
  }
}
```

### 6. fail2ban contre le brute-force SSH

```
# /etc/fail2ban/jail.local
[sshd]
enabled  = true
maxretry = 5
bantime  = 1h
```

### 7. Vérifier l'ASLR

La randomisation de l'espace d'adressage complique l'exploitation des failles mémoire.

```bash
sysctl kernel.randomize_va_space   # doit renvoyer 2
```

## Difficulté rencontrée : l'accès root perdu

Au départ, la VM n'avait qu'un compte utilisateur, sans droits `sudo` ni mot de passe root défini. Impossible donc d'administrer le système. J'ai repris la main en démarrant en mode de récupération depuis **GRUB**, puis j'ai ajouté mon compte au groupe `sudo`.

Cette situation m'a aussi montré concrètement pourquoi l'accès physique ou console à une machine doit être protégé : c'est précisément l'une des recommandations du guide (mot de passe sur le chargeur de démarrage).

## Prochaines étapes

<!-- Par exemple : auditd pour la journalisation, AppArmor, options de montage des partitions, mesure du score avec Lynis avant/après. -->
