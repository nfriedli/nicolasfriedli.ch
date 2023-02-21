+++
title = "Manipulation des CSS"
date = 2023-01-30
lastMod = 2023-02-13
+++

Les feuilles de style (CSS) permettent de mettre en forme une page web. Hugo permet des manipulations pour simplifier la maintenance ou optimiser le résultat.

En premier, ce qui est utilisé sur ce site, puis toutes les explications qui permettent de comprendre ce qui se cache sous le code.

## Sur ce site

Sur ce site, je charge 4 feuilles de style:

- `dracula.css` sert à la colorisation syntaxique du code à l’écran
- `github.css` sert à la colorisation syntaxique du code à l’impression
- `screen.css` représente la mise ne page du site sur écran et à l’impression
- `print.css` est utilisée pour l’impression seulement

En code, cela donnait:

```go-html-template
{{ $dracula := resources.Get "css/dracula.css" | minify | fingerprint }}
{{ $github := resources.Get "css/github.css" | minify | fingerprint }}
{{ $main := resources.Get "css/main.css" | minify | fingerprint }}
{{ $print := resources.Get "css/print.css" | minify | fingerprint }}

<link rel="stylesheet" href="{{ $dracula.RelPermalink }}" media="screen">
<link rel="stylesheet" href="{{ $github.RelPermalink }}" media="print">
<link rel="stylesheet" href="{{ $main.RelPermalink }}">
<link rel="stylesheet" href="{{ $print.RelPermalink }}" media="print">
```
Gestion du cache dans le fichier `.htaccess` (pour ce site):

```apache
<filesMatch ".(css)$">
Header set Cache-Control "max-age=63072000, public, immutable"
</filesMatch>
```

Ou par le fichier `_headers` chez CloudFlare ou Netlify:

```txt
/css/*
    Cache-Control: max-age=63072000,immutable
```

## Copie simple

Le cas le plus simple consiste à placer sa feuille de style dans le répertoire `static/css/`. Le fichiers qui s’y trouvent sont simplement copiés dans le site généré; il n’y a aucune transformation. La CSS se trouvera donc dans le répertoire `css/` du site en production.

```html
<link rel="stylesheet" href="/css/style.css">
```

## Traitement par Hugo

Plus intéressant, utiliser Hugo pour transformer la feuille de style. Il faudra la placer dans le répertoire `assets/`. Par exemple dans `assets/css/` pour que le répertoire de sortie deviennent `css/`.

```go-html-template
{{ $style := resources.Get "assets/css/style.css" }}
<link rel="stylesheet" href="{{ $style.RelPermalink }}">
```

Dans cet exemple, le résultat est le même que pour le précédent. Mais il est désormais possible d’effectuer des manipulations automatiques.

## Minification

Le filtre `minify` permet de compresser le fichier CSS:

```go-html-template
{{ $style := resources.Get "assets/css/style.css" 
    | minify }}
<link rel="stylesheet" href="{{ $style.RelPermalink }}">
```

Résultat:

```html
<link rel="stylesheet" href="/css/style.min.css">
```

##  Fingerprint

Le filtre `fingerprint` permet d’ajouter un identifiant unique au fichier:

```go-html-template
{{ $style := resources.Get "assets/css/style.css" 
    | minify  
    | fingerprint }}
<link rel="stylesheet" href="{{ $style.RelPermalink }}">
```

Le résultat ressemblera à:

```html
<link rel="stylesheet" href="/css/style.min.c404b5ab4e13daf8edc0029b322fa4ef18e19dd2a212d422e677f999c4bc7d6b.css">
```
Comme le fichier comprend un identifiant unique dans son nom, il devient possible d’utiliser un cache très long, voire un cache immutable.

## Subresource Integrity

L’utilisation de Subresource Integrity (SRI) permet d’ajouter une «clé» à l’appel de la feuille de style.

```go-html-template
{{ $style := resources.Get "assets/css/style.css" 
    | minify  
    | fingerprint }}
<link rel="stylesheet" 
    href="{{ $style.RelPermalink }}"
    integrity="{{ $style.Data.integrity }}">
```

Ainsi, si la feuille de style est modifiée après compilation, elle ne sera pas utilisée par le navigateur. C’est un outil intéressant pour activer les Content Security Policy (CSP).

##  SCSS et SASS

Je n’utilise pas de compilateurs de feuilles de styles. Toutefois, ils sont disponibles par défaut dans la version «extended» de Hugo. Ils sont activés par le filtre `toCSS`. Évidemment, c’est un fichier scss qui est appelé comme source.

```go-html-template
{{ $style := resources.Get "assets/css/style.scss" 
    | toCSS
    | minify  
    | fingerprint }}
```

## Bundle

Le bundle permet de regrouper plusieurs feuilles de style, pour au final n’en produire qu’une sur le site en production. C’est très utile pour un travail modulaire sur plusieurs petits fichiers.

```go-html-template
{{ $style := resources.Get "assets/css/style.css" }}
{{ $fonts := resources.Get "assets/css/fonts.css"}}
{{ $bundle := slice $style $fonts 
    | resources.Concat "/assets/bundle.css" }}
<link rel="stylesheet" href="{{ $bundle.RelPermalink }}">
```

## PurgeCSS

Hugo permet aussi d’optimiser plus sérieusement les feuilles de style en les nettoyant du code inutile. La page [PostProcess](https://gohugo.io/hugo-pipes/postprocess/) documente ce sujet.

Toutefois, cette méthode exige l’utilisation de `node.js` et fait perdre à Hugo un de ces principaux avantage: la présence d’un seul binaire. Si je devais optimiser le code à ce point, j’utiliserais peut-être Eleventy (11ty).

**Remarque.** L’utilisation de PurgeCSS pose problème avec les classes de Chroma qui ne sont pas reprises dans les statistiques produites par Hugo. Voir: [PurgeCSS and highlighting](https://discourse.gohugo.io/t/purgecss-and-highlighting/41021/1).