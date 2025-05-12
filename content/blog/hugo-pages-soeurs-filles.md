---
title: Pages sœurs, filles et mère avec Hugo
description: Des extraits de code Hugo pour automatiser le maillage interne du site avec une navigation au même niveau, au niveau supérieur et au niveau inférieur.
date: 2024-11-20
categories:
- hugo
---

Dans un site hiérarchique construit avec Hugo, il est facile de se créer des *shortcodes* ou des *partials* pour afficher une navigation contextuelle.
Je considère que le site est construit avec des répertoires et des pages `_index.md` dans chaque répertoire.

C’est idéal pour construire automatiquement le maillage interne d’un cocon sémantique «à l’ancienne»:

- lien vers la page mère en haut de page
- lien vers les pages sœurs en bas de page
- et éventuellement des liens vers les pages filles dans le corps du texte (si ce n’est pas fait manuellement, ce qui est meilleur)

Des codes plus évolués sont disponibles dans certaines de [mes dépôts GitHub](https://github.com/nfriedli/).

## *Shortcode* ou *partial*

La distinction entre les 2 doit être claire pour vous avant de vous lancer.
Si ce n’est pas le cas, il ne vaut pas la peine d’aller plus loin.
Mieux vaut lire la documentation d’Hugo: [Shortcodes](https://gohugo.io/content-management/shortcodes/) et [Partial templates](https://gohugo.io/templates/partial/).

Un *shortcode* est appelé **dans la source de la page en Markdown**, avec un code de ce type, disponible pour les rédacteurs et rédactrices:
  
```
{{</* sisters */>}}
```

Les *shorcodes* ont un **avantage**: ils peuvent être appelés n’importe où dans le **contenu** de la page (corps de l’article).
Par exemple un liste de billets entre 2 paragraphes. Ils ont un **inconvénient**: il faut les appeler à chaque fois.

Un *partial* est appelé **dans un *template* de page**, avec un code de type, disponibles pour les «programmeurs» et «programmeuses»:

```
{{ partial "header" . }}
```

Les *partials* ont un **avantage**: ils peuvent être appelés systématique **hors du contenu** de la page (corps de l’article).
Par exemple en pied de page ou comme liste de pages sous l’article.
Ils ont un **inconvénient**: les variations au cas par cas ne sont pas triviales.

## Pages filles (sous-pages ou niveau inférieur)

### Affichage des pages filles avec un *shortcode*

Un fichier dans `/layouts/_shortcodes/subpages.html`:

```
<ul>
    {{ range page.Pages }}
        <li><a href="{{ .RelPermalink }}">{{ .LinkTitle }}</a></li>
    {{ end }}
</ul>
```

On l’appelle par `{{</* subpages */>}}`.

Comme il n’est pas certain que des pages filles existent, on peut ajouter une condition sur la présence de pages.
Ou ne jamais utiliser ce *shortcode* quand il n’y a pas de filles.

### Affichage des pages filles avec un *partial*

Un fichier dans `/layouts/_partials/subpages.html`:

```
<ul>
    {{ range .Pages }}
        <li><a href="{{ .RelPermalink }}">{{ .LinkTitle }}</a></li>
    {{ end }}
</ul>
```

On l’appelle par `{{ partial "subpages" . }}`.
Avec le point qui transmet le [contexte](https://www.regisphilibert.com/blog/2018/02/hugo-the-scope-the-context-and-the-dot/)!

Comme il n’est pas certain que des pages filles existent, il **faut** ajouter une condition sur la présence de pages pour ne pas créer une liste vide.

## Pages sœurs (même niveau)

### Affichage des pages sœurs avec un *shortcode*

Un fichier dans `/layouts/_shortcodes/sisters.html`:

```
{{ with page.Parent }}
    <ul>
        {{ range .Pages }}
            <li><a href="{{ .RelPermalink }}">{{ .LinkTitle }}</a></li>
        {{ end }}
    </ul>
{{ end }}
```

On l’appelle par `{{</* sisters */>}}`.

Quand une rubrique existe, c’est qu’elle comporte normalement plusieurs pages.
Mais comme ce n’est pas une nécessité, le *shortcode* n’est appelé que quand il y a plusieurs pages.
Il faut alors l’ajouter sur toutes les nouvelles pages.
Je conseille d’ajouter des conditions (par exemple pour ne pas mettre un lien sur la page courante).

### Affichage des pages sœurs avec un *partial*

Un fichier dans `/layouts/_partials/sisters.html`:

```
{{ with .Parent }}
    <ul>
        {{ range .Pages }}
            <li>
                <a href="{{ .RelPermalink }}">
                    {{ .LinkTitle }}
                </a>
            </li>
        {{ end }}
    </ul>
{{ end }}
```

On l’appelle par `{{ partial "sisters" . }}`.
Avec le point qui transmet le contexte!

Quand une rubrique existe, c’est qu’elle comporte normalement plusieurs pages.
Je conseille d’ajouter des conditions (par exemple pour ne pas mettre un lien sur la page courante).

## Page mère (répertoire ou niveau supérieur)

### Affichage de la page mère avec un *shortcode*

Un fichier dans `/layouts/_shortcodes/mother.html`:

```
{{ with page.Parent }}
    <a href="{{ .RelPermalink }}">{{ .LinkTitle }}</a></li>
{{ end }}
```

On l’appelle par `{{</* mother */>}}`.

L’utilisation de `with` ne provoquera l’affichage que si une page mère existe.

### Affichage de la page mère avec un *partial*

Un fichier dans `/layouts/_partials/mother.html`:

```
{{ with .Parent }}
    <a href="{{ .RelPermalink }}">{{ .LinkTitle }}</a></li>
{{ end }}
```

On l’appelle par `{{ partial "mother" . }}`.
Avec le point qui transmet le contexte!

L’utilisation de `with` ne provoquera l’affichage que si une page mère existe.

## Conditions utiles

Je conseille d’ajouter certaines conditions d’affichage:

- affichage des pages sœurs uniquement s’il y a en a plus de 2 (la page présente et une autre page)
- désactiver l’affichage de la page actuelle de la liste ou
- désactiver le lien de la page actuelle dans la liste

Et aussi, tester le nombre de pages avant d’ouvrir un liste `<ul>...</ul>`.

Un exemple concret, que je vous invite à essayer de comprendre à la lecture:

```
{{ with .Parent }}
{{ if gt (len .Pages ) 2 }}
<aside>
    <strong>Ces contenus peuvent aussi vous intéresser:</strong>
    <ul>
        {{ range .Pages }}
            {{ if ne .Page page }} 
            <li>
                <a href="{{ .RelPermalink }}">
                    {{ .LinkTitle }}
                </a>
            </li>
            {{ end }}
        {{ end}}
    </ul>
</aside>
{{ end }}
{{ end }}
```

Je suis disponible pour vous aider à écrire vos conditions au cas par cas.
