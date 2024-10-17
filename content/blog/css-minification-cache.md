---
title: Feuilles de style minifiées et gestion du cache
description: Ce que j’applique en général pour la minification et la mise en cache des feuilles de style. C’est une optimisation raisonnable qui utilise certaines fonctions natives d’Hugo mais évite trop de complexité.
date: 2024-03-15
categories:
- hugo
- performance
---

Ce que j’applique en général pour la minification et la mise en cache des feuilles de style. C’est une *optimisation raisonnable* qui utilise certaines fonctions natives d’Hugo mais évite trop de complexité.

## Utiliser une feuille de style externe

La version la plus simple pour déclarer une feuille de style CSS, c’est un appel dans l’entête HTML:

```
<link rel="stylesheet" href="/css/style.css">
```

Pour que la feuille de style se trouve bien à l’endroit référencé après une compilation par Hugo, on la place dans: `/static/css/style.css`.

Le fichier est seulement copié, sans aucune modification, et placé dans le répertoire du site compilé: `/public/css/style.css`. C’est le principe de fonctionnement pour les [fichiers statiques](https://gohugo.io/getting-started/directory-structure/#static) chez Hugo. Tout ce qui se trouve dans le répertoire `/static/` est copié tel quel, avec la même hiérarchie, dans `/public/`.

## Minification des CSS par Hugo

C’est une bonne idée de minifier les feuilles de style. La copie seule est alors insuffisante (à moins de placer un fichier minifié par un outil tiers dans `/static/`, évidemment) Je place donc la feuille de style de départ dans `/assets/css/screen.css`. Comme son nom l’indique, elle est spécifique à l’affichage sur un écran.

Le répertoire `/assets/` permet d’effectuer des opérations sur les fichiers qu’il contient. Ici:

```
{{ $screen := resources.Get "css/screen.css" | minify }}
<link rel="stylesheet" href="{{ $screen.RelPermalink }}" media="screen">
```

La première ligne va chercher le fichier, relativement au répertoire, `/assets/` et le minifie. J’utilise pour cela un filtre. La seconde ligne appelle le fichier final en HTML. Le fichier produit sera `/public/css/screen.min.css`.

Je procède de même pour la feuille de style dédiée à l’impression:

```
{{ $print := resources.Get "css/print.css" | minify }}
<link rel="stylesheet" href="{{ $print.RelPermalink }}" media="print">
```

Le fichier produit se trouvera au même endroit que celui dédié à l’impression. Son nom portera, lui aussi, la trace de la minification par `.min.`.

## Fingerprint et cache long

Il est possible de mettre en cache les feuilles de style pour une très longue durée. C’est pourquoi je souhaite que le nom de fichier final soit unique. C’est facile avec [fingerprint](https://gohugo.io/hugo-pipes/fingerprint/):

```
{{ $screen := resources.Get "css/screen.css" | minify | fingerprint }}
<link rel="stylesheet" href="{{ $screen.RelPermalink }}" media="screen">
```

Ainsi, le nom final sera quelque chose comme:

```
/css/screen.min.215a9ff1ab8351ee4d0a3c644904e7ab4945a1fa3d70197a0735fc3e43195476.css`
```

Double avantage de la démarche:

- la certitude que la feuille de style qui s’applique à la page actuelle est toujours la bonne (et jamais une autre CSS en mémoire dans le navigateur)
- la possibilité de proposer une durée de cache très longue pour ne jamais recharger la feuille de style si elle existe déjà dans le navigateur

Cela se passe dans `.htaccess` avec un serveur Apache:

```
<filesMatch ".(css)$">
Header set Cache-Control "max-age=63072000,immutable"
</filesMatch>
```

Ou dans `_headers` chez Netlify:

```
/css/*
    Cache-Control: max-age=63072000,immutable
```

Tant que le style n’a pas été modifié, le fichier n’est pas téléchargé. C’est clair et efficace.

## Intégrer la feuille de style

Sur ce site, j’intégre le CSS dans le code HTML. C’est favorable lors de la première visite d’*une* page:

```
{{ $screen := resources.Get "css/screen.css" }} 
<style media="screen">{{ $screen | safeCSS }}</style>
```

Mais c’est potentiellement contre-productif si l’internaute lit plusieurs pages ou revient sur le site. Toutefois, le gain d’une solution ou de l’autre est toujours minime sur un site léger comme le mien.

Quand le style est intégré, on pourrait aller plus loin et nettoyer *chaque page* de ses styles inutiles. C’est ce que fait Max Böck avec son [site d’urgence avec Eleventy (11ty)](https://mxb.dev/blog/emergency-website-kit/). C’est impossible avec Hugo sans outils externes et le gain est marginal.

## Outils Hugo non utilisés sur mon blog

Il me semble que les options choisies sont pertinentes et suffisantes pour ce site. Mais Hugo propose d’autres possibilités. Par exemple:

- Réunir des feuilles de style avec [Concat](https://gohugo.io/hugo-pipes/bundling/). C’est inutile puisque je ne n’ai qu’un fichier (par type de média).
- Ajouter une vérification par [Subresource Integrity](https://gohugo.io/hugo-pipes/fingerprint/#usage). C’est pertinent si l’on dépose ses CSS sur un serveur tiers (par exemple un CDN) et que l’on veut être certain qu’elles n’ont pas été modifiées.
- Traiter la feuille de style avec SASS par la commande [ToCSS](https://gohugo.io/hugo-pipes/transpile-sass-to-css/). Je préfère l’utilisation des variables CSS. La version de SASS embarquée dans Hugo n’est plus mise à jour. Et la version Dart exige des dépendances externes.
- [Supprimer les styles non utilisés avec PurgeCSS](https://zwbetz.com/how-to-use-purgecss-with-hugo/) comme le propose Zachary Wade Betz. C’est utile sur un site avec une grande feuille de style (par exemple un *framework* CSS), mais pas ici.
