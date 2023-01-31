---
title: Premiers pas avec NSX-T
slug: nsx-t-first-steps
excerpt: Découvrez NSX-T
section: NSX-T
order: 01
---

**Dernière mise à jour le 30/01/2023**

> [!warning]
> Les guides concernant NSX-T dans la solution VMware ne sont pas définitifs, ils seront modifiés lors de la sortie en version BETA et finalisés quand la version définitive sera prête. 
>


## Objectif

**Ce guide est une introduction à NSX-T dans un cluster Hosted Private Cloud by VMware**

> [!warning]
> OVHcloud vous met à disposition des services dont la configuration, la gestion et la responsabilité vous incombent. Il vous appartient donc de ce fait d’en assurer le bon fonctionnement.
>
> Ce guide a pour but de vous accompagner au mieux sur des tâches courantes. Néanmoins, nous vous recommandons de faire appel à un prestataire spécialisé si vous éprouvez des difficultés ou des doutes concernant l’administration, l’utilisation ou la mise en place d’un service sur un serveur.
>

NSX-T est une solution de gestion de réseau logicielle **Sofware Defined networking (SDN)** fournie par VMware. OVHcloud propose ce service en remplacement de NSX-V dans son offre Hosted Private Cloud Powered by VMware. 

Lorsque un client souscrit à l'offre NSX-T et quelle est activée une préconfiguration est appliqué avec deux passerelles :

- **Tier-0 Gateway**: Pour les connexions entre le cluster et le réseau INTERNET public, que l'on nomme trafic nord-sud.
- **Tier-1 Gateway** : Pour les communications entre segments virtuels du cluster. Ce type de connexion s'appelle trafic est-ouest.

Les deux passerelles sont reliées entre elles afin d'autoriser les réseaux internes à communiquer à l'extérieur du cluster.

OVHcloud fourni un bloc de 8 adresses IP publiques, certaines sont réservées vous pouvez utiliser l'adresse qui est préconfigurée pour le SNAT en sortie.


## Prérequis

- Être contact administrateur du [Hosted Private Cloud infrastructure](https://www.ovhcloud.com/fr/enterprise/products/hosted-private-cloud/), celui-ci recevant les identifiants de connexion.
- Avoir un identifiant utilisateur actif avec les droits spécifiques pour NSX-T (créé dans l'[espace client OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/fr/&ovhSubsidiary=fr))

## En pratique

### Connexion à l'interface d'administration de NSX-T

La connexion à NSX-T se fait à partir de l'URL de votre cluster fourni par OVHcloud de la forme **https://pcc-xxxxx.ovh.xx**.

A partir de la page d'accueil de votre cluster cliquez sur l'icône `NSX NSX-T`{.action}.

![01 NSX-T Connection 01](images/01-nsxt-connection01.png)

Saisissez vos informations d'identifications et cliquez sur `LOG IN`{.action}.

> [!warning]
> Pour s'authentifier sur l'interface NSX-T, il faut utiliser un compte fourni par OVHcloud suivi du nom FQDN de votre cluster comme **admin@pcc-xxxxx.ovh.xx**. 
>

![01 NSX-T Connection 02](images/01-nsxt-connection02.png)

L'interface NSX-T s'affiche.

![01 NSX-T Connection 03](images/01-nsxt-connection03.png)

### Affichage de la configuration par défaut

Nous allons voir la topologie du réseau configurée par défaut lors du déploiement du service **NSX-T**.

Au travers de l'interface **NSX-T** cliquez sur l'onglet `Networking`{.action}.

![02 Display network topology 01](images/02-display-network-topology01.png)

Une vue de l'ensemble des éléments du réseau est affichée.

Cliquez à gauche sur `Network Topology`{.action}.

![02 Display network topology 02](images/02-display-network-topology02.png)

Un schéma représentant la topologie réseau est disponible avec deux adresses IP publiques (Ces deux adresses servent pour NSX-T et ne sont pas utilisables pour des redirections de ports) connectées à la passerelle **ovh-T0-gateway** ainsi que la connexion à la passerelle **ovh-T1-gateway**.

![03 Display network topology 03](images/02-display-network-topology03.png)

## Aller plus loin

Échangez avec notre communauté d'utilisateurs sur <https://community.ovh.com>.
