---
title:  Déplacer une IP Fail Over
excerpt: "Découvrez comment déplacer une IP Fail Over depuis l'espace client ou via les API OVHcloud"
slug: ip-fo-move
section: 'Réseau & IP'
order: 7
---

**Dernière mise à jour le 12/03/2021**

## Objectif

Les IP fail-over peuvent être déplacées entres les services que vous utilisez. L'intérêt est de ne pas perdre votre réputation, votre référencement et d'améliorer la continuité de service de vos applications et systèmes.
Cette technologie vous permet d’échanger les adresses IP d'une solution à l'autre en moins d'une minute, pratiquement sans aucune interruption pour vos utilisateurs. Elle peut être utilisée lors des migrations de services (déplacement des projets de l'environnement de développement à celui de production, par exemple) ou lors du basculement vers un serveur de secours en cas de défaillance.

**Découvez comment déplacer une IP Fail Over depuis votre espace client OVHcloud ou via les API OVHcloud**

## Prérequis

- Disposer d'un [serveur dédié](https://www.ovhcloud.com/fr-ca/bare-metal/){.external} dans votre espace client OVHcloud.
- Disposer d'une [adresse IP Fail Over](https://www.ovhcloud.com/fr-ca/bare-metal/ip/).
- Être connecté à l'[espace client OVHcloud](https://ca.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/ca/fr/&ovhSubsidiary=qc){.external}.

## En pratique

> [!primary]
> Une IP Fail Over ne peut pas être déplacée d'une zone à l'autre. Par exemple, une IP située dans le datacenter SBG pourra être déplacée vers GRA ou RBX mais ne pourra pas être déplacée vers BHS

### Déplacer une IP depuis l'espace client OVHcloud

Connectez-vous à votre [espace client OVHcloud](https://ca.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/ca/fr/&ovhSubsidiary=qc), cliquez sur le menu `Bare Metal Cloud`{.action} puis sur la section `IP`{.action} située en bas de la colonne à gauche de la page.

![espace client](images/manager01.png){.thumbnail}

Le menu déroulant « Service » vous permet de ne sélectionner que les IP Failover.

Cliquez sur le bouton `...`{.action} à droite de l'adresse IP à déplacer puis sur `Déplacer l'IP failover`{.action}.

![espace client](images/manager02.png){.thumbnail}

Dans le menu contextuel qui apparaît, sélectionnez le service vers lequel déplacer l'adresse IP.

Cliquez sur `Suivant`{.action} puis sur `Valider`{.action}.

![espace client](images/manager03.png){.thumbnail}

### Déplacer une IP via les API

Connectez-vous sur la page page web des [API OVHcloud](https://ca.api.ovh.com/).

Dans un premier temps, il est préférable de vérifier si l'adresse IP peut bien être déplacée.
<br>Pour vérifier si l'IP peut être déplacée vers un de vos serveurs dédiés, utilisez l'appel suivant :

> [!api]
>
> @api {GET} /dedicated/server/{serviceName}/ipCanBeMovedTo
>

- `serviceName` : la référence du serveur dédié de destination
- `ip` : l'adresse IP Fail Over à déplacer

Pour déplacer l'adresse IP, utilisez l'appel suivant :

> [!api]
>
> @api {POST} /dedicated/server/{serviceName}/ipMove
>

- `serviceName` : la référence du serveur dédié de destination
- `ip` : l'adresse IP Fail Over à déplacer

## Aller plus loin

Échangez avec notre communauté d'utilisateurs sur <https://community.ovh.com/>.
