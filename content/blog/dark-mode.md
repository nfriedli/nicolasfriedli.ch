---
title: Mode sombre en quelques lignes de CSS
description: Activer un mode sombre sur son site en une ligne de CSS ou en utilisant quelques variables et des medias queries. Simple et fiable.
date: 2024-02-10
---

En quelques lignes de CSS, il est possible d’activer un mode sombre automatique sur son site. La *version aboutie* est celle que j’utilise pour plusieurs projets. C’est simple et fiable.

## Version minimale

Le plus simple, c’est:

```
root {
    color-scheme: light dark;
}
```

Si les couleurs d’arrière-plan, de texte, des liens, etc., n’ont pas été définies, c’est parfaitement fonctionnel. Il suffit de signaler au navigateur qu’il a le droit de s’afficher en clair (*light*) ou en foncé (*dark*) selon les préférences de l’internaute. Si aucune préférence a été fixée, c’est le mode *light* qui sera choisi.

Il est aussi possible de passer au mode sombre sans fixer aucune couleur, mais sans bascule automatique en fonction des préférences:

```
root {
    color-scheme: dark;
}
```

Au lieu de préciser le schéma de couleur dans la feuille de style CSS, il peut être annoncé dans le code HTML de la page:

```
<meta name="color-scheme" content="dark light">
```

Dans certains cas, c’est préférable, car le navigateur a cette information avant même de charger la feuille de style. Mais c’est là une question de détails.

## Version aboutie (mais simplissime)

Dès que des couleurs sont choisies, il faut de la cohérence pour éviter du texte foncé sur fond foncé (ou clair sur clair). La feuille de style la plus simple pour gérer cela:

```
:root {
    color-scheme: light dark;
    --background: #FFF;
    --text: #333;
}

@media (prefers-color-scheme: dark) {
    :root {
        --background: #000;
        --text: #DDD;
    }
}

html {
    background: var(--background);
    color: var(--text);
}

a {
    color: inherit;
}
```

Le code est simple:

- Le navigateur peut choisir le mode *light* ou le mode *dark*
- Une couleur de fond et une couleur de texte sont déclarées en variables CSS
- Si la préférence du navigateur est le mode sombre, les variables sont modifiées.
- Le fond et le texte sont déclarés pour tout le document.
- Les liens prennent la même couleur que le texte.

La même chose est possible sans variables, de la manière suivante:

```
:root {
    color-scheme: light dark;
}

html {
    background: #FFF;;
    color: #333;
}

@media (prefers-color-scheme: dark) {
    html {
        background: #000;
        color: #DDD;
    }
}

a {
    color: inherit;
}
```

## Autres méthodes

Des feuilles de style distinctes, une pour le sombre, une pour le clair, avec un appel différencié. Ce peut être intéressant sur les thèmes qui sont très différents, mais sinon les variables CSS paraissent plus efficaces. Exemple:

```
<link media="(prefers-color-scheme: light)" 
    href="light.css" rel="stylesheet">
<link media="(prefers-color-scheme: dark)"  
    href="dark.css"  rel="stylesheet">
```

Un changement de couleur avec du JavaScript comme le propose Max Böck dans [Color Theme Switcher](https://mxb.dev/blog/color-theme-switcher/). C’est très élégant, ça ouvre des perspectives, mais c’est bien plus complexe que quelques lignes de CSS.

L’utilisation de la fonction [`invert()`](https://developer.mozilla.org/en-US/docs/Web/CSS/filter-function/invert) permet, comme son nom l’indique, d’inverser des valeurs. Cette méthode ne me convient pas. Je pense que l’on peut choisir ses couleurs plus finement qu’en les inversant simplement (et elle pose des problèmes avec les images).

Plutôt que cette méthode par `invert()`, je procéderais plutôt ainsi s’il fallait simplement inverser les valeurs:

```
:root {
    color-scheme: light dark;
    --light: #FFF;
    --dark: #222;
}

html {
    background: var(--light);
    color: var(--dark);
}

@media (prefers-color-scheme: dark) {
    :html {
        --background: var(--dark);
        --text: var(--light);
    }
}

a {
    color: inherit;
}
```

## Choix du mode par le site

Dans les exemples précédents, c’est l’internaute qui choisit un thème clair ou un thème foncé. Si le site accepte les 2 modes, c’est bien aux utilisateurs et utilisatrices que le choix incombe. Mais...

Une règle `no-preference` a été envisagée, mais elle n’a jamais été implémentée dans un seul navigateur. Au final, elle a simplement été [supprimée de la spécification technique](https://github.com/w3c/csswg-drafts/issues/3857#issuecomment-634779976). C’est bien dommage. Parce que si un·e internaute n’a pas fait de choix, c’est le thème *light* qui est tout de même considéré comme son choix!

En d’autres termes, en tant que responsable de site, je ne peux pas proposer, en pur CSS, un site qui s’affiche:

- en mode sombre par défaut
- en mode clair si et seulement si l’internaute a fait un choix explicite

Pour disposer d’un mode sombre par défaut avec une possibilité de passer au mode clair sur demande, il faudra obligatoirement passer par un petit développement (par exemple le *Color Theme Switcher* mentionné plus haut). 
