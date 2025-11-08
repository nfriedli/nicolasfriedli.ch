---
title: Shortcodes et partials avec Hugo
description: 
draft: true
---

Les *shortcodes* et les *partials* sont souvent confondus dans Hugo.
Ils sont 2 manières d’appeler un bout de code dans un contexte précis.
Mais leur utilisation est complètement différente et pas forcément destinée aux mêmes personnes.

## Shortcodes pour le contenu éditorial

**Les shortcodes s’utilisent uniquement dans le contenu rédactionnel en Markdown.**
Ils sont disponibles pour toutes les personnes en charge de rédaction de pages.
Ils sont appelés quand nécessaire.
Comme leur nom l’indique, ce sont des raccourcis.

Les shortcodes ont un avantage: ils peuvent être appelés n’importe où dans le **contenu** de la page (corps de l’article).

Ils ont un inconvénient: il faut les appeler à chaque fois.

### Shortcode minimal

Le fichier `/layouts/_shortcodes/version.html` contient le code suivant:

```
{{ hugo.Version }}
```

Il peut être appelé n’importe où dans le texte d’une source en Markdown.
Et produire un paragraphe de ce type:

> C’est Hugo {{< version >}} qui a compilé la version courante de ce site.

La source de ce paragraphe sera simplement:

```
C’est  Hugo {{</* version */>}} qui a compilé la version courante de ce site.
```

C’est possible de faire de même avec une date, n’importe quelle variable disponible ou même un texte statique qui se répète *dans* le contenu des pages.

### Exemple de shortcode fourni par Hugo

Hugo fournit par défaut un moyen de [produire des codes QR](https://gohugo.io/shortcodes/qr/), par exemple:

{{< qr text="https://nicolasfriedli.ch" alt="Lien vers le site nicolasfriedli.ch" scale=8 level="low" loading="lazy" targetDir="/images/" />}}

Il est produit par quelque chose comme ceci:

```
{{</* qr text="https://nicolasfriedli.ch" /*/>}}
```

Le shortcode permet d’entrer des paramètres, comme l’URL de destination, le texte alternatif, etc.
L’image ci-dessus en utilise quelques uns.
En conséquence, il est possible de publier plusieurs codes QR sur la page, avec des destinations différentes.

Il existe de nombreux autres [raccourcis disponibles par défaut](https://gohugo.io/shortcodes/), par exemple pour:

- pour inclure des images proprement
- pour coloriser le code
- pour embarquer un post Instagram
- pour intégrer une vidéo YouTube

### Codes disponibles ou à créer

Les personnes qui sont en charge de la partie rédactionnelle d’un site ont sous la main les shortcodes par défaut de Hugo.
Elles disposent, peut-être, de codes du thème utilisé (dans `/themes/`).
Elles peuvent aussi avoir en réserve des codes spécifiques à leur site (donc dans `/layouts/`).

Au besoin, elles peuvent créer de nouveaux codes ou demander à l’équipe de développement de site de le faire pour elles.

Il vaut la peine de réfléchir aux codes qui seraient utiles pour éviter les répétitions ([Ne vous répétez pas](https://fr.wikipedia.org/wiki/Ne_vous_r%C3%A9p%C3%A9tez_pas)) et assurer la pérennité et la cohérence d’un site.

Les shortcodes ont un avantage énorme sur les questions de sécurité.
En effet, il est possible, avec Hugo, d’autoriser l’inclusion de code HTML; à éviter autant que possible.
Mais la sécurité dépend alors de l’usage qui est fait par les rédactrices et rédacteurs.
En limitant les possibles, c’est un moyen de s’assurer qu’aucun code bizarre ne sera inclus dans le site.

## Partials pour les gabarits de pages

**Les partials s’utilisent uniquement dans les modèles de pages (templates).**
Ils sont disponibles uniquement pour celles et ceux qui codent ces gabarits.
Ils sont appelés de manière automatique.

Les partials ont un avantage: ils peuvent être appelés de manière systématique hors du contenu de la page (corps de l’article).
Par exemple en pied ou comme liste de pages pour poursuivre sa lecture sous l’article.

Ils ont un inconvénient: les variations au cas par cas ne sont pas triviales.

### Partial type

Un partial produit parfois des résultats qui ne sont pas visibles immédiatement aux internautes.
Par exemple, pour inclure, dans chaque page d’un site, la méta description si elle a été écrite dans la page source.
Il suffit du fichier `/layouts/_partials/description.html`:

```
{{ with .Params.description }}
    <meta name="description" content="{{ . }}">
{{ end }}
```

Ce code est appelé dans le modèle principal du site (par exemple `/layouts/baseof.html`) par:

```
{{ partial "description" . }}
```

C’est systématique, ça tient en un fichier de 3 lignes et 1 seul appel, et ça se répercute sur tout le site, quelle que soit sa taille.

### Partials fournis par Hugo

Certains partials sont [fournis par défaut](https://gohugo.io/templates/embedded/).
Les plus utiles sont:

- la [pagination](https://gohugo.io/templates/pagination/)
- la [création de schémas Open Graph](https://gohugo.io/templates/embedded/#open-graph)

Je ne trouve pas d’intérêt aux suivants:

- des commentaires par Disqus (parce qu’il faut éviter de les utiliser)
- des statistiques Google Analytics (idem)

Dans tous les cas, il est possible de télécharger le modèle inclus et de le modifier.

### Modularisation par partials et cache

Une des principales utilisations de partials, c’est découper son code en plus petites parties simples à lire et à comprendre.
Aucune raison d’en faire la liste, mieux vaut jeter un œil au [répertoire `_partials` des sources de ce site](https://github.com/nfriedli/nicolasfriedli.ch/tree/main/layouts/_partials).

Une remarque quand même, il est possible de classer ses partials dans des sous-répertoires pour encore plus de clarté.
Dans le cas présent: `head`.

Dans certains cas, il est possible d’utiliser un partial identique sur tout le site.
Pour ce site, c’est le cas du pied de page.
Pour ne pas faire le travail à chaque URL, il est placé en cache car appelé par:

```
{{ partialCached "footer" . }}
```

Le [cache peut être partial](https://gohugo.io/functions/partials/includecached/) et produit par section, rubrique, type de page, etc. pour des très grands sites ou des partials complexes.

## En résumé

Les **shortcodes** sont utilisés dans le contexte de la **gestion éditoriale** du site, dans les fichiers en **Markdown**, par les **équipes de rédaction**.

Les **partials** sont utilisés dans le contexte du **développement** du site, dans des fichiers en **HTML**, par des d**éveloppeurs et développeuses**.