---
title: Comment créer une galerie d'images?
description: Afficher un ensemble d'images sur une page, avec des légendes et des grandes images en cliquant.
date: 2021-04-28
images:
    - https://cdn.pixabay.com/photo/2017/11/12/22/50/human-2944064_960_720.jpg
---

Sur une page donnée: afficher des vignettes avec leurs légendes et proposer un lien vers des images en grande taille.
Un code basique que je souhaite garder sous la main parce qu'il me sera utile souvent.

## Une feuille (*leaf bundle*)

En premier lieu, il faut bien comprendre les principe des [Page Bundles](https://gohugo.io/content-management/page-bundles/) de Hugo.
Si vous n'avez pas compris le truc, vous allez vous arracher les cheveux et perdre du temps.

Donc dans un répertoire se trouvent:
- un fichier `index.md` (et pas `_index.md`)...
- l'ensemble des images qui apparaîtront dans la galerie
- il n'y a pas d'autres pages ou de sous-répertoires

Et, évidemment:
- il faut une page de modèle dans `layouts`
- les vignettes sont de vrais vignettes (bien dimensionnées, etc.), pas des images réduites par le navigateur

## Les données de `index.md`

L'entête (*frontmatter*) ressemble à ceci:

```yaml
---
title: Titre de la galerie
_build:
  publishResources: false
resources:
- title: |
    Titre en *markdown*  
    avec un saut de ligne forcé
  src: image-1.jpg
  params:
    weight: 10
- title: |
    Un océan au bord de l'eau  
    Anonyme  
    CC0
  src: ocean.jpg
  params:
    weight: 20
---
```

Le premier titre, c'est ce lui de la page et de la galerie.
Chaque image possède un titre, un nom de fichier et un critère de classement.

Le passage `_build` est intéressant.
Je choisis de ne pas copier les images sources sur le site public.
Seules les images traitées sont utilisées.

## Le modèle

Dans la page utilisée comme `layouts`, appelée par héritage ou explicitement par `layout:` dans l'entête (*frontmatter*) de page, il me faudra quelque chose comme:

```go-html-template
{{ range sort .Resources "Params.weight" }}
    {{ $large := .Resize "1024x q85 MitchellNetravali" }} 
    {{ $small := .Fit "300x300 q75 MitchellNetravali" }}
    <div class="image">  
        <a href="{{ $large.Permalink }}" target="_blank">
        <img src="{{ $small.Permalink }}" alt="{{ .Title }}" 
            width="{{ $small.Width }}" height="{{ $small.Height }}" 
            loading="lazy">
        </a>
        <p>{{ .Title | markdownify}}</p>
    </div> 
{{ end }}
```
Cette boucle fait le actions suivantes:
- elle liste toutes les images du répertoire (y compris celles qui ne sont pas listées explicitement dans l'entête) 
- elle les trie par le critère de tri puis, pour chaque image
- elle crée une grande image dont la largeur vaut au maximum 1024 pixels, en assez bonne qualité
- elle crée une petite image (vignette) dont la plus grande dimension entre la largeur et la hauteur vaut 300 pixels, en qualité moyenne
- elle affiche la vignette (avec les attributs de hauteur, de largeur et le texte alternatif `alt`)
- elle crée un lien vers la grande image (ouverture dans une nouvelle fenêtre)
- elle propose au navigateur de charger les images seulement quand c'est nécessaire (`loading="lazy"`)
- elle affiche la légende, traitée en *markdown*.

Reste à choisir un mise en page, par exemple en utilisant `flex` ou `grid` de CSS.
Et à ajouter, au besoin, une visionneuse façons *lightbox*.
Tout cela n'a plus rien à voir avec Hugo, je n'en parle pas ici.