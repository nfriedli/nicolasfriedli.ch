+++
title = "Pages sœurs, filles et mère avec Hugo"
description = "La navigation sur un site web ressemble parfois à de la généalogie. Si un site créé avec Hugo est correctement structuré, le parcours de l’arbre est facile."
date = 2023-06-25
aliases = ["/hugo/siblings"]
+++

La navigation sur un site web ressemble parfois à de la généalogie. Si un site créé avec Hugo est correctement structuré, le parcours de l’arbre est facile.

Je suppose donc que les pages (de type single) sont correctement placées dans des répertoires. Et que chaque répertoire contient une page _index.md (de type list). Selon la logique des types se pages d’Hugo.

## La page mère (niveau supérieur)

Les pages disposent d’une variable .Parent, ce qui rend recherche de la page mère triviale. Si la page courante a une page mère, on affiche le lien:

```
{{ with .Parent }}
  <a href="{{ .RelPermalink }}">
    {{ .Title }}
  </a>
{{ end }}
```

En version un peu plus développée, on pourrait par exemple afficher:

```
{{ with .Parent }}
  {{ if not .IsHome }}
    <aside>Publié dans 
      <a href="{{ .RelPermalink }}">
        {{ .Title | markdownify }}
      </a>
    </aside>
  {{ end }}
{{ end }}
```

Ce lien n’est pas affiché sur les sections et les pages de premier niveau du site.

## Les pages filles (niveau inférieur)

La variable .Pages renvoie précisément les pages et sous-sections de la page de liste courante. C’est donc simple:

```
{{ range .Pages }}
  <a href="{{ .RelPermalink }}">{{ .Title }}</a>
{{ end }}
```

Un détour par la documentation Page Variables (en anglais) peut être utile pour mieux comprendre ce que renvoient exactement les variables disponibles.

Ensuite, il y a possibilité d’affiner un peu les choses, par exemple en listant séparément les sections et les pages:

```
{{ range .Sections }}
  <h2><a href="{{ .RelPermalink }}">{{ .Title }}</a></h2>
  {{ .Description }}
{{ end }}
{{ range .RegularPages }}
  <a href="{{ .RelPermalink }}">{{ .Title }}</a>
{{ end }}
```

## Les pages sœurs (même niveau)

Finalement, les pages sœurs ne sont rien d’autres que des pages dont la mère est commune. En version simple:

```
{{ with .Parent }}
  {{ range .Pages }}
    <a href="{{ .RelPermalink }}">{{ .Title }}</a>
  {{ end }}
{{ end }}
```

Un exemple un peu plus développé dans lequel la page courante n’est pas affichée, mais seulement ses sœurs:

```
{{ $current := . }}
{{ with .Parent }}
  Voir aussi:
  <ul>
  {{ range .Pages }}
    {{ if ne $current .}}
      <li>
        <a href="{{ .RelPermalink }}">{{ .Title }}</a>
      </li>
    {{ end }}
  {{ end }}
  </ul>
{{ end }}
```

Cela semble assez lisible:

- on mémorise la page courante dans une variable
- si la page a une mère, on affiche Voir aussi: et on commence une liste
- on parcourt les sous-pages et on les affiches si la page listée n’est pas la page courante

Autre possibilité, mettre en valeur la page courante par l’attribution d’une classe CSS. Ou encore de l’afficher mais sans en faire un lien actif.

## Un exemple en version *shortcode*

Sur ce site, ~~j’utilise~~ j’utilisais le shortcode `subpages.html` que je peux appeler directement dans le *markdown* de n’importe quelle page:

```
Ma liste de sous-pages:

{{</* subpages */>}}

Et la suite de mon texte...
```

Le code de `layouts/shortcodes/subpages.html`:

```
<ul>
{{ range .Page.Pages }}
    <li>
        <a href="{{.RelPermalink}}">{{ .Title }}</a>
    </li>
{{ end }}
</ul>
```