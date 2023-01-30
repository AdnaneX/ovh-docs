---
title: Configuration du DHCP
slug: nsx-t-dhcp-configuration
excerpt: Ajout d'un serveur DHCP à un segment
section: NSX-T
order: 03
---

**Dernière mise à jour le 30/01/2023**

> [!warning]
> Les guides concernant NSX-T dans la solution Hosted Private Cloud Powered by VMware ne sont pas définitifs, ils seront modifiés lors de la sortie en version BETA et finalisés quand la version définitive sera prête. 
>

## Objectif

**Comment faire pour configurer un serveur DHCP dans un segment**

> [!warning]
> OVHcloud vous met à disposition des services dont la configuration, la gestion et la responsabilité vous incombent. Il vous appartient donc de ce fait d’en assurer le bon fonctionnement.
>
> Ce guide a pour but de vous accompagner au mieux sur des tâches courantes. Néanmoins, nous vous recommandons de faire appel à un prestataire spécialisé si vous éprouvez des difficultés ou des doutes concernant l’administration, l’utilisation ou la mise en place d’un service sur un serveur.
>

## Prérequis

- Être contact administrateur du [Hosted Private Cloud infrastructure](https://www.ovhcloud.com/fr/enterprise/products/hosted-private-cloud/), celui-ci recevant les identifiants de connexion.
- Avoir un identifiant utilisateur actif avec les droits spécifiques pour NSX-T (créé dans l'[espace client OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/fr/&ovhSubsidiary=fr))
- Avoir **NSX-T** déployé avecn un segment configuré dans votre configuration NSX-T, vous pouvez vous aider de ce guide [Gestion des segments dans NSX-T](https://docs.ovh.com/fr/private-cloud/nsx-t-segment-management).



## En pratique

Nous allons configurer un serveur DHCP sur un segment connecté à **OVH-T1-gw**. Ce segment est configuré avec une passerelle en **192.168.1.254/24**.

A partir de l'interface NSX-T allez dans l'onglet `Networking`{.action} et cliquez sur `Segments`{.action} à gauche.

![01 add DHCP ON Segment 01](images/01-add-dhcp-on-segment01.png)

Cliquez sur l'icône de configuration indiqué avec `trois points verticaux`{.action} à gauche de votre segment et choisissez `Edit`{.action}.

![01 add DHCP ON Segment 02](images/01-add-dhcp-on-segment02.png)

Cliquez sur `Set DHCP CONFIG`{.action}.

![01 add DHCP ON Segment 03](images/01-add-dhcp-on-segment03.png)

Choisissez à gauche `Local DHCP Server`{.action} dans **DHCP Type**. Ensuite cliquez à droite de **DHCP Profile** sur l'icône de configuration avec `trois points verticaux`{.action} et choisissez `Create New`{.action}.

![01 add DHCP ON Segment 04](images/01-add-dhcp-on-segment04.png)

Choisissez ces informations :

***Name**: Nom de votre serveur DHCP.
***Server IP Address**: L'adresse IP de votre serveur DHCP, qui ne doit pas être la même que l'adresse IP de votre passerelle sous la forme 192.168.1.253/24.
***Edge Cluster**: Sélectionnez votre cluster edge.

Et cliquez sur `Save`{.action}.

![01 add DHCP ON Segment 05](images/01-add-dhcp-on-segment05.png)

Saisissez ces valeurs :

* **DHCP Server Address** : Adresse du serveur DHCP 192.168.1.253/24 (Ce doit être la même adresse que dans le profil DHCP).
* **DHCP Range** : Etendue de votre serveur DHCP avec l'adresse du début et de fin séparés par un tiret 192.168.1.10-192.168.1.200.
* **DNS Server** : Serveur DNS OVHcloud 213.186.33.99.

Ensuite cliquez sur `APPLY`{.action}.

![01 add DHCP ON Segment 06](images/01-add-dhcp-on-segment06.png)

Les machines virtuelles sur ce segment peuvent maintenant être configuré en DHCP.

## Aller plus loin

[Premiers pas avec NSX-T](https://docs.ovh.com/fr/private-cloud/nsx-t-first-steps/)

[Gestion des segment dans NSX-T](https://docs.ovh.com/fr/nsx-t-segment-management/)

Échangez avec notre communauté d'utilisateurs sur <https://community.ovh.com>.

