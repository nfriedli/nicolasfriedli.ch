---
title: Shortcodes et partials avec Hugo
description: 
draft: true
---

Les *shortcodes* et les *partials* sont souvent confondus dans Hugo.
Ils sont 2 manières d'appeler un bout de code dans un contexte précis.
Mais leur utilisation est complètement différente et pas forcément accessible aux mêmes personnes.

## *shortcodes* pour le contenu éditorial

Les *shortcodes* s’utilisent uniquement dans le contenu rédactionnel en markdown.
Ils sont disponibles pour toutes les personnes en charge de rédaction de pages.
Ils sont appelés quand nécessaire.
Ce sont des raccourcis.


Les *shorcodes* ont un avantage: ils peuvent être appelés n’importe où dans le **contenu** de la page (corps de l’article).

Ils ont un inconvénient: il faut les appeler à chaque fois.

### *shortcode* minimal

Le fichier `/layouts/_shortcodes/version.html` contient le code suivant:

```
{{ hugo.Version }}
```

Il peut être appelé n'importe où dans le texte d'une source en Markdown.
Et produire un paragraphe de ce type:

> C'est Hugo {{< version >}} qui a compilé la version courante de ce site.

La source de ce paragraphe sera simplement:

```
C'est  Hugo {{</* version */>}} qui a compilé la version courante de ce site.
```

C'est possible de faire de même avec une date, n'importe quelle variable disponible ou même un texte statique qui se répète *dans* le contenu des pages.

### Exemple de *shortcode* fourni par Hugo

Hugo fournit par défaut un moyen de [produire des codes QR](https://gohugo.io/shortcodes/qr/), par exemple:

{{< qr text="https://nicolasfriedli.ch" alt="Lien vers le site nicolasfriedli.ch" scale=8 level="low" loading="lazy" targetDir="/images/" />}}

Il est produit par quelque chose comme ceci:

```
{{</* qr text="https://nicolasfriedli.ch" /*/>}}
```

Le *shortcode* permet d'entrer des paramètres, comme l'URL de destination, le texte alternatif, etc.
L'image ci-dessus en utilise quelques uns.
En conséquence, il est possible de publier plusieurs codes QR sur la page, avec des destinations différentes.

Il existe de nombreux autres [raccourcis disponibles par défaut](https://gohugo.io/shortcodes/), par exemple pour:

- pour inclure des images proprement
- pour coloriser le code
- pour embarquer un post Instagram
- pour intégrer une vidéo YouTube

### Codes disponibles ou à créer

Les personnes qui sont en charge de la partie rédactionnelle d'un site ont sous la main les *shortcodes* par défaut de Hugo.
Elles disposent, peut-être, de codes du thème utilisé (dans `/themes/`).
Elles peuvent aussi avoir en réserve des codes spécifiques à leur site (donc dans `/layouts/`).

Au besoin, elles peuvent créer de nouveaux codes ou demander à l'équipe de développement de site de le faire pour elles.

Il vaut la peine de réfléchir aux codes qui seraient utiles pour éviter les répétitions ([Ne vous répétez pas](https://fr.wikipedia.org/wiki/Ne_vous_r%C3%A9p%C3%A9tez_pas)) et assurer la pérennité et la cohérence d'un site.

## *partials* pour les gabarits de pages

Les *partials* s’utilisent uniquement dans les modèles de pages (*templates*).
Ils sont disponibles uniquement pour celles et ceux qui codent ces gabarits.
Ils sont appelés de manière automatique.

Les *partials* ont un avantage: ils peuvent être appelés de manière systématique hors du contenu de la page (corps de l’article).
Par exemple en pied ou comme liste de pages sous l’article.

Ils ont un inconvénient: les variations au cas par cas ne sont pas triviales.

### *partial* type

```
{{ if .Params.description }}
    <meta name="description" content="{{ .Params.description }}">
{{ else }}
    <meta name="description" content="{{ .Summary }}">
{{ end }}
```

Appelé par:

```
{{ partial "description" . }}
```



### *partials* fournis par Hugo

```
{{ partial "opengraph.html" . }}
```