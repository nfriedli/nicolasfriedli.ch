---
title: Disparition d’une page ou d’un site web
description: Il est possible de consulter une page disparue grâce à différents systèmes d’archives. C’est précieux quand on site des liens dans nos articles.
aliases:
- /blog/disparition/
---

Que faire quand une page n’est plus disponible en ligne mais que son contenu nous intéresse toujours?
Et quand un site entier a disparu?

On m’a récemment demandé une ancienne page de ce site, qui semblait intéressante au moins pour un internaute.
Je vous livre une méthode pour retrouver plein de vieilleries.

Pour commencer son travail de fouille, il faut au moins disposer de l’adresse de la page ou du nom de domaine du site.
C’est facile lorsque l’on dispose encore d’un lien quelque part.
Ensuite, plusieurs possibilités existent.

## Wayback Machine

La solution royale, c’est l’utilisation de la [Wayback Machine](https://web.archive.org/) de l’Internet Archive.
Si la page fait partie de l’archive, il est possible de la retrouver telle qu’elle existait à différentes dates
Quand un site entier est archivé, il est même possible de naviguer et de l’utiliser (presque) comme quand il était en ligne.

Par exemple, pour nicolasfriedli.ch:

- les différentes [captures du site par date](https://web.archive.org/web/20250000000000*/nicolasfriedli.ch) ou
- la liste de [toutes URL archivées](https://web.archive.org/web/*/nicolasfriedli.ch*) avec la mention du type de fichier et un horodatage

### Ajouter des archives

Quand un article qui comporte des liens importants est publié, je conseille de toujours le faire entrer dans la Wayback Machine.
Avec l’option *Save outlinks*, disponible uniquement avec un compte (gratuit), toutes les pages en lien sont aussi sauvées.

Pour ajouter un lot de pages, par exemple pour archiver son propre site, il est toujours intéressant de partir d’une page qui liste beaucoup de liens:

- plan complet du site s’il existe
- sitemap (par exemple https://nicolasfriedli.ch/index.xml)
- à défaut, une page de liste sérieuse (par exemple une catégorie de blog)

En principe, je sauvegarde nicolasfriedli.ch pour que toutes les pages se trouvent dans l’Internet Archive.

### Extensions de navigateur et applications Web Archive

Il existe des extensions de navigateur et des applications iOS et Android pour la Wayback Machine.
Je n’utilise que les premières.

Elles permettent de sauvegarder rapidement une page, avec l’option *Save outlinks* si nécessaire.
Mais surtout, elles signalent automatiquement la présence d’une archive quand une page n’est plus disponible en ligne.

Dans certains cas, une page est toujours en ligne, mais pas dans la version souhaitée.
L’extension signale alors le nombre de sauvegardes existantes et permet d’y accéder facilement.

## Cache des moteurs de recherche

Parfois, les pages supprimées restent disponibles dans les moteurs de recherche.
C’est notamment le cas quand on ne prend pas sont de les en exclure via, par exemple, la Google Search Console.
Ou que l’on ne demande pas à son serveur d’envoyer un [code HTTP](https://fr.wikipedia.org/wiki/Liste_des_codes_HTTP) de suppression clair (par exemple 410).

Les pages ne sont plus accessible dans leur dernière version indexée directement dans le moteur de recherche.
Mais c’est une manière de faire précieuse pour retrouver des contenus.
Et surtout pour obtenir des URL que l’on utilisera dans la Wayback Machine.

## Historique de Git

Quand un site est géré avec Git sur un système public (GitHub, GitLab, etc.), on peut souvent en refaire l’histoire.
Certes, les contenus proposés sont parfois des sources (par exemple en [Markdown](/blog/markdown)), mais le contenu textuel est bien là.
C’est une bonne raison de toujours donner la [priorité au texte](/blog/txt/) quand on édite un site.

Pour nicolasfriedli.ch, le dépôt GitHub est parfois nettoyé, notamment pour ne pas colporter des images utilisées précédemment.
Mais l’histoire récente est bien là.

Pour rappel, le dépôt est public: https://github.com/nfriedli/nicolasfriedli.ch

## Archives dans le lecteur RSS ou Atom

C’est une astuce que je trouve peu utilisée, mais diablement efficace.
En entrant un nom de domaine dans Inoreader ou Feedly, l’agrégateur propose souvent une liste des anciennes publications.

Pour diminuer leur bande passante, ces outils stockent des articles.
Si le flux RSS ou Atom propose le contenu entier des pages, c’est un trésor.

Certains agrégateurs, avec des comptes payants, proposent aussi de stocker des articles (par exemple en PDF).
Puis de placer ces fichiers automatiquement dans un répertoire précis de Dropbox ou un autre outil de stockage.

## Service Worker

Enfin, quand un site dispose d’un [service worker](https://developer.mozilla.org/en-US/docs/Web/API/Service_Worker_API), il est possible qu’il garde des pages longtemps en mémoire sur votre périphérique.
Certaines pages *déjà visitées* pourraient être encore consultables, même quand le site qui les publiait n’existe plus.

J’hésite à intégrer un [service worker minimal façon Adactio](https://adactio.com/journal/13540) pour ce blog.
Ou à m’inspirer de la [réflexion de Tantek Çelik](https://tantek.com/2024/151/t1/minimum-interesting-service-worker) pour conserver, un peu, des contenus.

----

Je suis à l’écoute pour améliorer ce billet si vous avez d’autres manières de faire efficaces, des outils à conseiller, des besoins d’éclaircissements.
