---
title: Feuilles de style CSS minifiées par Hugo et gestion du cache
description: Ce que j’applique en général pour la minification et la mise en cache des feuilles de style. C’est une optimisation raisonnable qui utilise certaines fonctions natives d’Hugo mais évite trop de complexité.
date: 2024-03-15
lastMod: 2025-11-16
---

Ce que j’applique en général pour la minification et la mise en cache des feuilles de style.
C’est une optimisation raisonnable qui utilise certaines fonctions natives d’Hugo mais évite trop de complexité.

## Utiliser une feuille de style externe

La version la plus simple pour déclarer une feuille de style CSS, c’est un appel dans l’entête HTML:

```
<link rel="stylesheet" href="/css/style.css">
```

Pour que la feuille de style se trouve bien à l’endroit référencé après une compilation par Hugo, on la place dans: `/static/css/style.css`.

Le fichier est seulement copié, sans aucune modification, et placé dans le répertoire du site compilé: `/public/css/style.css`.
C’est le principe de fonctionnement pour les [fichiers statiques](https://gohugo.io/getting-started/directory-structure/#static) chez Hugo.
Tout ce qui se trouve dans le répertoire `/static/` est copié tel quel, avec la même hiérarchie, dans `/public/`.

## Minification des CSS par Hugo

C’est une bonne idée de minifier les feuilles de style.
La copie seule est alors insuffisante (à moins de placer un fichier déjà minifié par un outil tiers dans `/static/`, évidemment) Je place donc la feuille de style de départ dans `/assets/css/screen.css`.
Comme son nom l’indique, elle est spécifique à l’affichage sur un écran.

Le répertoire `/assets/` permet d’effectuer des opérations sur les fichiers qu’il contient.
Ici:

```
{{ $screen := resources.Get "css/screen.css" | minify }}
<link rel="stylesheet" href="{{ $screen.RelPermalink }}" media="screen">
```

La première ligne va chercher le fichier, relativement au répertoire, `/assets/` et le minifie.
J’utilise pour cela un filtre.
La seconde ligne appelle le fichier final en HTML.
Le fichier produit sera `/public/css/screen.min.css`.

## Fingerprint et cache long

Il est possible de mettre les feuilles de style en cache dans le navigateur pour une très longue durée.
C’est pourquoi je souhaite que le nom de fichier final soit unique.
C’est facile avec [fingerprint](https://gohugo.io/functions/resources/fingerprint/):

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

Tant que le style n’a pas été modifié, le fichier n’est pas téléchargé.
C’est clair et efficace.

## Intégrer la feuille de style

Sur ce site, j’intégrais le CSS dans le code HTML.
C’est favorable lors de la première visite d’une page et avec un feuille de style légère:

```
{{ $screen := resources.Get "css/screen.css" }} 
<style media="screen">{{ $screen | safeCSS }}</style>
```

Mais c’est potentiellement contre-productif si l’internaute lit beaucoup de pages ou revient souvent sur le site.
Toutefois, le gain d’une solution ou de l’autre est toujours minime sur un site léger.

Quand le style est intégré, on pourrait aller plus loin et nettoyer *chaque page* de ses styles inutiles.
C’est ce que fait Max Böck avec son [site d’urgence avec Eleventy (11ty)](https://mxb.dev/blog/emergency-website-kit/).
C’est impossible avec Hugo sans outils externes et le gain est reste marginal.

## Outils Hugo non utilisés sur ce site

Il me semble que les options choisies sont pertinentes et suffisantes pour ce site.
Mais Hugo propose d’autres possibilités.
Par exemple:

- Réunir des feuilles de style avec [Concat](https://gohugo.io/hugo-pipes/bundling/).
  C’est inutile puisque je ne n’ai qu’un fichier (par type de média).
- Ajouter une vérification par [Subresource Integrity](https://gohugo.io/functions/resources/fingerprint/).
  C’est pertinent si l’on dépose ses CSS sur un serveur tiers (par exemple un CDN) et que l’on veut être certain qu’elles n’ont pas été modifiées.
- Traiter la feuille de style avec SASS par la commande [ToCSS](https://gohugo.io/hugo-pipes/transpile-sass-to-css/).
  Je préfère l’utilisation des variables CSS.
  La version de SASS embarquée dans Hugo n’est plus mise à jour.
  Et la version Dart exige des dépendances externes.
- [Supprimer les styles non utilisés avec PurgeCSS](https://zwbetz.com/how-to-use-purgecss-with-hugo/) comme le propose Zachary Wade Betz.
  C’est utile sur un site avec une grande feuille de style (par exemple un *framework* CSS), mais pas ici.

Je signale que l’équipe de développement a pas mal travaillé sur l’utilisation de [Tailwind CSS avec Hugo](https://gohugo.io/functions/css/tailwindcss/).

----

Désormais, j’utilise des feuilles de style CSS externes, minifiés, avec un numéro de version unique.
Cette page n’est pas modifiée en conséquence mais tout ce qui y est dit reste utilisable, tant pour les CSS intégrées comme que les feuilles de style externes.

Les sources du site sur GitHub permettent de voir le [partial qui s’occupe des styles CSS](https://github.com/nfriedli/nicolasfriedli.ch/blob/main/layouts/_partials/head/css.html) tel qu’il est utilisé actuellement.
