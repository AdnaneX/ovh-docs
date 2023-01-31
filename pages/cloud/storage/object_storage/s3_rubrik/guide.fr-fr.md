---
title: Utiliser S3 Object Storage avec Rubrik
slug: s3/rubrik
excerpt: Découvrez comment configurer le stockage dans Rubrik pour utiliser un bucket S3 Object Storage
section: Object Storage S3 High Performance
order: 172
---

**Dernière mise à jour le 31/01/2023**

## Objectif

Rubrik est une solution de sauvegarde robuste et sécurisée qui autorise l'archivage sur un stockage High Performance Object Storage OVHcloud.

**Ce guide vous montre comment configurer High Performance Object Storage OVHcloud comme dépôt d'archivage du logiciel Rubrik.**

> [!warning]
>
> OVHcloud met à votre disposition des services dont la configuration, la gestion et la responsabilité vous incombent. Il vous revient de ce fait d'en assurer le bon fonctionnement.
>
> Nous mettons à votre disposition ce guide afin de vous accompagner au mieux sur des tâches courantes. Néanmoins, nous vous recommandons de faire appel à un [prestataire spécialisé](https://partner.ovhcloud.com/fr/) et/ou de contacter l'éditeur du logiciel si vous éprouvez des difficultés. En effet, nous ne serons pas en mesure de vous fournir une assistance. Plus d'informations dans la section « Aller plus loin » de ce guide.
>
> Les licences Rubrik ne sont pas fournies par OVHcloud. Pour plus d’informations, contactez le service commercial de Rubrik.
>

## Prérequis

- Avoir créé un projet public au travers de l'espace client OVHcloud.

Consultez notre guide « [Créer votre premier projet Public Cloud](https://docs.ovh.com/fr/public-cloud/create_a_public_cloud_project/) » pour plus de détails.

## En pratique

Vous devez créer un utilisateur dans un compte public OVHcloud qui a la possibilité de générer des *Buckets*, ensuite produire une clé RSA 2048 bits avant de pouvoir utiliser **High Performance Storage** en tant que dépot d'archive du logiciel Rubrik.

### Création d'un utilisateur sur un projet public OVHcloud

Nous allons créer un compte dans un projet public qui sera capable d'ajouter des *buckets* sur un stockage **High Performance Object Storage**.

Connectez-vous à l'espace client OVHcloud au travers de l'url [OVHcloud](https://www.ovhcloud.com).

Cliquez en haut à gauche sur le `menu principal`{.action}.

![01 Create User 01](images/01-createuser01.png)

Choisissez `Public Cloud`{.action}.

![01 Create User 01](images/01-createuser02.png)

Cliquez en haut à droite sur la `flêche vers la droite`{.action}.

![01 Create User 03](images/01-createuser03.png)

Cliquez sur votre `projet`{.action}.

![01 Create User 04](images/01-createuser04.png)

Cliquez en haut à gauche sur le `menu principal`{.action}.

![01 Create User 06](images/01-createuser05.png)

Sélectionnez `Public Cloud`{.action}.

![01 Create User 06](images/01-createuser06.png)

Utilisez la `barre de défilement`{.action} et cliquez sur `Users & Roles`{.action}.

![01 Create User 07](images/01-createuser07.png)

Cliquez sur `Ajouter un utilisateur`{.action}.

![01 Create User 08](images/01-createuser08.png)

Saisissez un `nom d'utilisateur` dans **Description de l'utilisateur** et cliquez sur `Suivant`{.action}.

![01 Create User 09](images/01-createuser09.png)

Cochez la case `ObjectStore operator`{.action} et cliquez sur `Valider`{.action}.

![01 Create User 10](images/01-createuser10.png)

Cliquez sur `l'icône rond avec 3 petits points`{.action} à droite du compte utilisateur créé pour générer les accès S3.

![01 Create User 11](images/01-createuser11.png)

Choisissez `Générer les credentials S3`{.action} à droite.

![01 Create User 12](images/01-createuser12.png)

L'accès S3 est créé il est composé de ces éléments :

- **access key** ;
- **secret key** .

![01 Create User 13](images/01-createuser13.png)

### Production d'une clé privé RSA

Nous allons utiliser l'outils en ligne de commande openssl disponible sous Linux ou Windows. 

Lancer cette commande dans un terminal :

```bash
openssl genrsa -out rubrik_encryption_key.pem 2048
```

Le contenu du fichier est de cette forme par exemple :

```console
-----BEGIN RSA PRIVATE KEY-----
tbEH9hP4TVC6ZRdxqL59hEuKMLQru93sW1b4uZ/S8W7y5Ip1WwnqJPNqUbwOto/f
LhsVAoGBAOnHOBJeUabERcur4It6NJdwQ/TPSrOkLnW5WMjEOcbwZr0Pq7GaW6l/
tbEH9hP4TVC6ZRdxqL59hEuKMLQru93sW1b4uZ/S8W7y5Ip1WwnqJPNqUbwOto/f
LhsVAoGBAOnHOBJeUabERcur4It6NJdwQ/TPSrOkLnW5WMjEOcbwZr0Pq7GaW6l/
oic8XYh0OdAA5aY1kIy33Gg8NVarnGMe+ezc9NhF6AHIhAgwXZ+NBLdcUujPBaqx
7p3lZs1vEEBX4ouHX93qz7ymNJ+MTeQtCNX4tQfE4kcLT0pY+DtW
-----END RSA PRIVATE KEY-----
```

### Configuration du stockage dans le logiciel Rubrik

Saisissez ces informations dans le logiciel Rubrik lors de la configuration du dépôt d'archives.

* ** Acces Key** : Votre `Acces key` ; 
* ** Secret Key** : Votre `Secret key` ;
* ** hostname** : Soit `s3.gra.perf.cloud.ovh.net` pour le Datacenter de Gravelines ou `s3.sbg.perf.cloud.ovh.net` pour celui de Strasbourg ;
* ** bucket Prefix** : `Prefixe du bucket` en minuscule ;
* ** Number of Buckets** : Choisissez `1` ;
* ** Archival Location Name** : `S3Compatible`
* ** RSA Key** : Copiez la `clé RSA` 

Ensuite cliquez sur `Add`{.action}

![02 Configure rubrik repository 01](images/02-configure-rubrik-repository01.png)

Un *bucket* est automatiquement créé dans le projet public OVHcloud avec comme préfixe le nom contenu dans  **bucket Prefix**.

## Aller plus loin

Site Officiel de [Rubrik](https://www.rubrik.com/)

Échangez avec notre communauté d'utilisateurs sur [https://community.ovh.com](https://community.ovh.com){.external}.

