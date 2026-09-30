---
layout: post
title: "Infrastructure Windows sécurisée : Active Directory, VMware, Veeam et Zabbix"
context: Projet académique, Nexa Digital School
summary: Déploiement d'une infrastructure virtualisée complète, de l'annuaire Active Directory jusqu'à la sauvegarde, la supervision et le durcissement des serveurs.
stack: [VMware, Windows Server, Active Directory, GPO, Veeam, Zabbix]
---

<!-- Relis chaque ligne : garde uniquement ce que tu as réellement fait, un recruteur peut t'interroger sur n'importe quel point. -->

## Objectif

Construire une infrastructure Windows comme on la trouverait en entreprise : pas seulement une infrastructure qui fonctionne, mais une infrastructure **administrable, sauvegardée, surveillée et sécurisée**.

## Architecture

<!-- Ajoute ton schéma : ![Schéma de l'infrastructure](/images/infra-windows.png) -->

| Rôle | Solution |
|---|---|
| Virtualisation | VMware |
| Annuaire et authentification | Windows Server, Active Directory, DNS |
| Sauvegarde | Veeam |
| Supervision | Zabbix |

## Ce que j'ai mis en place

### Active Directory

- Structuration de l'annuaire en unités d'organisation, utilisateurs et groupes
- Stratégies de groupe (GPO) pour appliquer une configuration homogène et des règles de sécurité sur les postes et serveurs
- Attribution des droits d'accès aux partages (NTFS) selon le principe du moindre privilège

<!-- Donne un exemple concret de GPO : politique de mots de passe, verrouillage de session, restriction du panneau de configuration... -->

### Sauvegarde avec Veeam

- Mise en place d'une stratégie de sauvegarde des machines virtuelles
- **Tests de restauration** : une sauvegarde qui n'a jamais été restaurée ne garantit rien

### Supervision avec Zabbix

- Surveillance de la disponibilité et des ressources des serveurs (CPU, mémoire, disque)
- Alertes pour détecter un problème avant qu'il ne touche les utilisateurs

### Durcissement

- Réduction de la surface d'attaque des serveurs déployés

<!-- Précise : services inutiles désactivés, comptes administrateurs séparés, pare-feu Windows, mises à jour... -->

## Difficultés rencontrées

<!-- Raconte UN problème réel : symptôme, diagnostic, solution. C'est la partie que les recruteurs lisent le plus. -->

## Ce que j'en retiens

<!-- 2 ou 3 phrases : ce que tu sais faire maintenant que tu ne savais pas faire avant. -->
