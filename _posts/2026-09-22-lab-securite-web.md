---
layout: post
title: "Lab de sécurité web : DVWA, Juice Shop, Burp Suite et OWASP ZAP"
context: Lab personnel
summary: Mise en place d'un environnement d'entraînement pour comprendre les vulnérabilités web du côté de l'attaquant, afin de mieux savoir les prévenir.
stack: [Kali Linux, Docker, DVWA, OWASP Juice Shop, Burp Suite, OWASP ZAP]
---

## Objectif

On défend mieux ce qu'on sait attaquer. Ce lab me sert à comprendre, sur des applications volontairement vulnérables, comment fonctionnent les failles du **Top 10 de l'OWASP** et comment les corriger.

## Environnement

| Élément | Rôle |
|---|---|
| Kali Linux (ARM64) | Machine d'attaque |
| Docker | Déploiement des applications cibles |
| DVWA | Application vulnérable avec plusieurs niveaux de difficulté |
| OWASP Juice Shop | Application moderne volontairement vulnérable |
| Burp Suite, OWASP ZAP | Proxys d'interception pour analyser et modifier les requêtes |

## Difficultés techniques

Travailler sur une machine **ARM64** a demandé plusieurs contournements :

- Burp Suite n'embarque pas son navigateur Chromium sur cette architecture : il a fallu configurer un navigateur externe pour passer par le proxy
- L'image Docker de Juice Shop, prévue pour x86, n'était pas compatible
- Des problèmes de réseau Docker et d'espace disque sont apparus pendant la mise en place de DVWA

<!-- Pour chaque point, explique comment tu l'as résolu. C'est ce qui montre ta capacité à débugger. -->

## Vulnérabilités étudiées

<!-- Pour chaque faille : principe, comment tu l'as exploitée (capture Burp), et comment la corriger. Exemple de structure : -->

### Injection SQL

<!-- Principe, exploitation, correctif (requêtes préparées). -->

### Cross-Site Scripting (XSS)

<!-- Principe, exploitation, correctif (échappement des sorties, CSP). -->

## Ce que j'en retiens

<!-- 2 ou 3 phrases. -->
