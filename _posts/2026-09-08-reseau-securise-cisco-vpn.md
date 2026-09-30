---
layout: post
title: "Réseau d'entreprise sécurisé : switches Cisco, firewalls et VPN"
context: Projet académique, Nexa Digital School
summary: Conception d'une infrastructure réseau segmentée, configuration des équipements Cisco et des firewalls, mise en place de VPN, puis audit de sécurité et documentation.
stack: [Cisco IOS, VLAN, Routage, Firewall, VPN, Audit]
---

<!-- Relis chaque ligne : garde uniquement ce que tu as réellement fait. -->

## Objectif

Concevoir un réseau d'entreprise qui sépare les usages, contrôle les flux entre zones et permet des accès distants sécurisés, puis vérifier le résultat par un audit.

## Conception

- **Segmentation** du réseau en VLAN selon les usages (utilisateurs, serveurs, administration)
- **Plan d'adressage** IP par segment
- Définition des flux autorisés entre les zones

<!-- Ajoute ta topologie (capture Packet Tracer ou GNS3) : ![Topologie](/images/topologie-reseau.png) -->

## Configuration des équipements

### Switches Cisco

Création des VLAN, configuration des ports d'accès et des liens trunk, sécurisation de l'accès d'administration.

```
! Exemple de configuration — remplace-le par un extrait anonymisé de la tienne
vlan 10
 name UTILISATEURS
vlan 20
 name SERVEURS
!
interface GigabitEthernet0/1
 switchport mode access
 switchport access vlan 10
!
interface GigabitEthernet0/24
 switchport mode trunk
 switchport trunk allowed vlan 10,20
```

### Firewalls

Filtrage des flux entre les zones : seul ce qui est nécessaire est autorisé, tout le reste est bloqué.

### VPN

Mise en place d'un accès VPN pour relier les sites ou permettre le travail à distance de façon chiffrée.

<!-- Précise le type : site à site IPsec, accès distant OpenVPN/WireGuard... -->

## Audit et documentation

- Vérification de la configuration face aux bonnes pratiques de sécurité
- Rédaction de la documentation technique de l'infrastructure

<!-- Qu'a révélé l'audit ? Une faiblesse trouvée et corrigée est un excellent exemple. -->

## Ce que j'en retiens

<!-- 2 ou 3 phrases. -->
