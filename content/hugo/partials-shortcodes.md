+++
title = "Différence entre «partials» et «shortcodes»"
date = 2023-02-02
+++

Les partials comme les shortcodes permettent d’appeler un bout de code dans une autre page. Mais ils sont complètements différents.

## Les «partials» pour les gabarits de page

Partout où un même extrait de code est utilisé plusieurs fois, un partial pourrait ou devrait être créé. Par exemple, pour chaque page du site, un test est effectué:

```go-html-template
{{ if .Params.description }}
    <meta name="description" content="{{ .Params.description }}">
{{ else }}
    <meta name="description" content="{{ .Summary }}">
{{ end }}
```

En français:
- si la description a été rédigée explicitement, elle est reprise telle quelle
- sinon, elle est composée à partir du début de la page

Plutôt que de mettre ce bout de code dans le gabarit (*template*) général de la page, il a été déplacé dans le fichier `layouts/partials/head/description.html`. Le dossier `layouts/partials/head/` comprend tous les shortcodes utilisés dans les dans `<head>`.

Ensuite, dans le code du site:

```go-html-template
<head>
    ...
    {{ partial "head/description" .}}
    {{ partialCached "head/css" . }}
    ...
</head>
```
Le second shortcode appelé dans l’exemple ci-dessus, c’est l’ensemble des feuilles de style. J’en parle ici: [Manipulation des CSS](/hugo/css/).

Le code est appellé avec `partialCached`. Il n’est compilé qu’une seule fois pour tout le site, quel que soit le nombre de pages. La documentation officiel sur [Cached Partials](https://gohugo.io/templates/partials/#cached-partials) donne des exemples de caches sélectifs, par exemple par section ou par langue.

**En résumé:** Les *partials* s’utilisent uniquement dans les *templates* en HTML. Ils sont disponibles uniquement aux personnes qui codent des gabarits de pages

## Les «shortcodes» pour le contenu éditorial

Les shortcodes sont appelés à partir du contenu éditorial. Un exemple avec les dernières publications du site:

{{< last >}}

Ce qui précède est produit par:

```markdown
Les shortcodes sont appelés à partir du contenu éditorial.
Un exemple avec les dernières publications du site:

{{</* last */>}}
```

C’est donc le shortcode `layouts/shortcodes/last.html` qui fait tout. 
Ici, l’affichage des 5 dernières pages éditoriales du site, par ordre antéchronologique:

```go-html-template
<ul>
    {{ range first 5 site.AllRegularPages.ByDate.Reverse }}
    <li>
        <a href="{{.RelPermalink}}">{{ .Title }}</a>
    </li>
    {{ end }}
</ul>
```

N’importe en rédigeant une page, il est possible d’inclure les dernières nouveautés en un seul code.

Même principe pour lister les pages d’une section ou d’une rubrique, avec un shortcode `subpages`.
Voir aussi: [Pages sœurs, filles et mère](http://localhost:1313/hugo/siblings/).

**En résumé:** Les *shortcodes* s’utilisent uniquement dans le contenu rédactionnel en *markdown*. Ils sont disponibles pour toutes les personnes en charge de rédaction de pages.

## En pratique

Avec Hugo, il existe 2 types principaux de pages:

- les pages de listes (*list pages*): ce sont les répertoires, qui *listent* souvent des sous-pages
- les pages de contenu (*single pages*): ce sont des pages éditoriales

Les premières utilisent le *template* `list.html`, par exemple:

```go-html-template
{{ define "main" }}
    <h1>{{ .Title }}</h1>
    {{ .Content }}
    
    <ul>
    {{ range .Pages }}
        <li><a href="{{.RelPermalink}}">{{ .Title }}</a></li>
    {{ end }}
    </ul>
{{ end }}
```
Les secondes utilisent le *template* `single.html`, par exemple:

```go-html-template
{{ define "main" }}
    <h1>{{ .Title }}</h1>
    {{ .Content }}
{{ end }}
```

**Remarque:** sur ce site, les 2 *templates* sont identiques et les sous-pages sont listées par un *shortcode*. Tout est visible dans les sources sur GitHub (lien ci-dessous).