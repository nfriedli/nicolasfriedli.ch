---
title: Shortcodes et partials avec Hugo
description: 
draft: true
---

Les *shortcodes* et les *partials* sont souvent confondus dans Hugo.
Ils sont 2 manières d'appeler un bout de code dans un contexte précis.
Mais leur utilisation est complètement différente et pas forcément accesible aux mêmes personnes.

## *shortcodes* pour le contenu éditorial

Les *shortcodes* s’utilisent uniquement dans le contenu rédactionnel en markdown.
Ils sont disponibles pour toutes les personnes en charge de rédaction de pages.
Ils sont appelés quand nécessaire.

Les *shorcodes* ont un avantage: ils peuvent être appelés n’importe où dans le **contenu** de la page (corps de l’article).
Par exemple une liste de billets entre 2 paragraphes.

Ils ont un inconvénient: il faut les appeler à chaque fois.

### *shortcode* type

```
Les *shortcodes* sont appelés à partir du contenu éditorial.
Un exemple avec les dernières publications du site:

{{</* last */>}}
```

```
<ul>
    {{ range first 5 site.AllRegularPages.ByDate.Reverse }}
    <li>
        <a href="{{.RelPermalink}}">{{ .Title }}</a>
    </li>
    {{ end }}
</ul>
```


### Codes avec ou sans paramètres

### *Shortcodes* fournis par Hugo

```
{{</* qr text="https://nicolasfriedli.ch" /*/>}}
```


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