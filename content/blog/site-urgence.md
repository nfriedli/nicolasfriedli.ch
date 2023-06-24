+++
title = "Réflexions sur un site d'urgence"
date = 2023-06-02
draft = true
+++

## Typologie d'urgences

### Problèmes du côté des internautes

Chute des providers, coupures électriques donc surcharge de certains réseaux, etc.

### Problèmes de serveur

Hébergement interne, coupure de courant, question territoriale

### Problèmes de montée en charge

Souvent prévisible plusieurs jours avant.

### Accumulation des problèmes

Dans de nombreux cas, 2 ou 3 des problèmes cités surviennent ensemble.

## The Emergency Website Kit

Le développeur autrichien Max Böck a posé des jalons important dans la réflexion sur un site d'urgence. Et il a surtout proposé une solution concrète et pragmatique pour répondre aux enjeux: [The Emergency Website Kit](https://mxb.dev/blog/emergency-website-kit/).

Bien que la publication de son outil date de la période du Covid-19, la réflexion est plus ancienne. Dans son billet [The Hurricane Web](https://mxb.dev/blog/hurricane-web/), il apporte des éléments intéressant sur le web purement textuel. C'est donc avant tout au premier cas de la typologie ci-dessus qu'il répond.

2 idées principales président à sa démarche:

- **l'optimisation drastique de tout ce qui peut l'être:** dans l'urgence, on abandonne plein de choses que l'on pense nécessaire et dont on n'a plus besoin: des outils marketing, des illustrations «décoratives», des statistiques, des polices d'écritures distantes, etc.
- **la facilité de déploiement du site:** pas besoin d'être développeur pour activer le site proposé par Max Böck, tout est prévu et simplifié



## Un exemple de réalisation

Pour une ville bilingue de Suisse, j'ai proposé et mis en place un site d'urgence et les choix stratégiques qui vont avec:

- le nom de domaine est distinct du site principal et réservé chez un **autre fournisseur d'accès**
- alors que le site normal est hébergé sur des serveurs de la ville, le site d'urgence est hébergé chez un **prestataire externe** (CDN CloudFlare)
- l'administration du site d'urgence est effectuée sur GitHub, avec la possibilité d'y accéder par **tout ordinateur connecté** (pas besoin de *login* de l'administration ou d'accès VPN)
- l'ensemble est **documenté** en pdf (fichier local sur l'ordinateur des personnes concernées) et sur papier, avec la mise à disposition physique des codes d'accès
- les personnes en charge de la publication ont déjà effectué des **déploiements réels** pour tester l'ensemble de la démarche
- le site est **actif** (mais sans urgence affichée à l'heure où j'écris ces lignes)

À chaque *commit* sur GitHub, le site est compilé et déployé chez CloudFlare. Mais comme le résultat est statique et léger, il est aussi possible de l'envoyer sur n'importe quel serveur toujours fonctionnel par FTP ou rsync.

**Remarque.** À part ma facture de consultant pour la mise ne place du projet, le site ne coûte à la ville que les frais annuels de nom de domaine!

## Ma proposition: un site d'urgence avec Hugo

## Réflexions à mener au cas par cas