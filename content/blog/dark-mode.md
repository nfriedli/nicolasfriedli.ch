---
title: Mode sombre en quelques lignes de CSS
date: 2024-02-10
---

En quelques lignes de CSS, il est possible d'activer un mode sombre automatique sur son site. La *version aboutie* est celle que j'utilise pour plusieurs projets. C'est simple et fiable.

## Version minimale

Le plus simple, c'est:

```
root {
    color-scheme: light dark;
}
```

Si les couleurs d'arrière-plan, de texte, des liens, etc. n'ont pas été définies, c'est parfaitement fonctionnel. Il suffit de signaler au navigateur qu'il a le droit de s'afficher en clair (*light*) ou en foncé (*dark*) selon les préférences de l'internaute. Si aucune préférence a été fixée, c'est le mode *light* qui sera choisi.

Il est aussi possible de passer au mode sombre sans fixer aucune couleur, mais sans bascule automatique en fonction des préférences:

```
root {
    color-scheme: dark;
}
```

Au lieu de préciser le schéma de couleur dans la feuille de style CSS, il est possible de le faire dans le code HTML de la page:

```
<meta name="color-scheme" content="dark light">
```

Dans certains cas, c'est préférable, car le navigateur a cette information avant même de charger la feuille de style. Mais c'est un gain mineur.

## Version aboutie (mais simplissime)

Dès que des couleurs sont choisies, il faut de la cohérence pour éviter du text foncés sur fond foncé. La feuille de style la plus simple pour gérer cela:

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

a {
    color: inherit;
}
```

## Autres méthodes

Des feuilles de style distinctes, une pour le sombre, une pour le clair, avec un appel différencié. Ce peut être intéressant sur les thèmes sont très différents, mais sinon les variables CSS paraissent plus efficaces. Exemple:

```
<link media="(prefers-color-scheme: light)" href="light.css" rel="stylesheet">
<link media="(prefers-color-scheme: dark)"  href="dark.css"  rel="stylesheet">
```

Un changement de couleur avec du javascript comme le propose Max Böck dans [Color Theme Switcher](https://mxb.dev/blog/color-theme-switcher/). C'est très élégant, ça ouvre des perspectives, mais c'est bien plus complexe que quelques lignes de CSS.

L'utilisation de la fonction [`invert()`](https://developer.mozilla.org/en-US/docs/Web/CSS/filter-function/invert) permet, comme son nom l'indique, d'inverser des valeurs. Cette méthode ne me convient pas. Je pense que l'on peut choisir ses couleurs plus finement qu'en les inversant simplement (et elle pose des problème avec les images). 

Plutôt que cette méthode par `invert()`, je procéderais plutôt ainsi s'il fallais simplement inverser les valeurs:

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

## Mode par défaut

¼¼¼¼¼ à réécrire.

Lors que le navigateur ne demande pas *explicitement* un thème, c'est toujours le clair qui est affiché. Je trouve dommage, dans ma feuille de style CSS, de ne pas pouvoir choisir le thème foncé si le navigateur ne précise rien. Je pourrais avoir envie que mon site soit foncé par défaut, par choix esthétique, sans 

En code, ce serait quelque chose comme:

```
@media (prefers-color-scheme: light) { 
    /* règles CSS si light est explicitement choisi */
}
```

Une règle `no-preference` a été envisagée mais elle est désormais caduque selon la [documentation de MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/@media/prefers-color-scheme).
