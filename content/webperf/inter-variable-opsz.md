---
title: Police Inter variable locale avec taille optique
description: L’astuce pour obtenir la variation de taille optique (opsz) dans son navigateur avec une polices locale. Avec exemple de code et proposition de font stack.
date: 2025-02-04
lastMod: 2025-11-23
---

Sur mon poste Linux, la très belle police d’écriture Inter installée localement est variable (graisses de 100 à 900).
Mais elle n’utilise pas les tailles optiques (`opsz`) dans un navigateur.
Cela (me) pose problème, car Inter est trop espacée en grande taille, pour les titres et les intertitres.

Si j’utilise Inter en police en ligne (fichier `woff2`), tout va bien.
La police est variable en graisse (`wght`) comme en taille (`opsz`)

## Problème

Dans ma recherche pour proposer une *font stack* (pile de polices) de qualité sans recourir à des envois de fichiers, je croyais avoir enfin trouvé la solution.

En principe, on devrait pouvoir remplacer:

```
html {
    font-family: "Inter", system-ui, sans-serif;
}
```

par:

```
html {
    font-family: "Inter Variable", system-ui, sans-serif;
}
```

Malheureusement, comme Chrome et Firefox ne sont pas d’accord sur la manière de nommer une police dans une déclaration CSS, cette solution ne fonctionne pas toujours!

Si vous souhaitez une solution qui marche partout en 2025, le plus sûr reste l’utilisation d’une police en ligne ([*web font*](https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/Text_styling/Web_fonts)), avec la bande passante que cela suppose.
Mais l’utilisation de `@font-face` pourrait être un bon palliatif.

## Inter avec `@font-face`

Pour obtenir la variation tant souhaitée, je déclare la police avec `@font-face`, comme si c’était une police distante:

```
:root {
  font-optical-sizing: auto;
}

@font-face {
  font-family: "Inter Variable";        /* sélection de la version variable */
  font-style: normal;
  font-weight: 100 900;
  src: local("Inter Variable");         /* nom local de la police */
}

@font-face {
  font-family: "Inter Variable";        /* sélection de la version variable */
  font-style: italic;
  font-weight: 100 900;
  src: local("Inter Variable Italic");  /* nom local de la police */
}
```

Cette déclaration fonctionne parfois, mais pas toujours dans Chrome pour Windows.

Pour augmenter les chances que cela soit parfait partout, il faut donc utiliser plusieurs noms de police (ce qui est possible avec `@font-face`):

```
:root {
  font-optical-sizing: auto;
}

@font-face {
  font-family: "Inter Variable";        /* sélection de la version variable */
  font-style: normal;
  font-weight: 100 900;
  src:  local("Inter Variable"),  
        local("Inter-Variable"),
        local("InterVariable");         /* noms locaux de la police */
}

@font-face {
  font-family: "Inter Variable";        /* sélection de la version variable */
  font-style: italic;
  font-weight: 100 900;
  src: 
        local("Inter Variable Italic"),
        local("Inter-Variable Italic"),
        local("InterVariable Italic");  /* noms locaux de la police */
}
```

Désormais, si le navigateur et le système d’exploitation reconnaissent au moins un des noms, ça fonctionne.

## Proposition de *font stack*

Désormais, je peux créer une *font stack* optimale (les familles génériques n’ont pas de guillemets):

```
html {
  font-family: 
    "Inter Variable",   /* Inter variable, déclarée précédemment, si installée            */
    ui-sans-serif,      /* utilise San Francisco (variable) disponible chez Apple         */
    "Inter",            /* Inter en version statique (non variable), si installée         */
    "Roboto",           /* Roboto, si installée                                           */
    system-ui,          /* Segoe UI sur Windows, Roboto sur Android, à choix sur Linux    */
    sans-serif;         /* la police sans empattement de secours                          */
}
```

Avec une telle «pile d’écritures», je suis certain que vous aurez quelque chose de beau et de très lisible.
Vous pouvez ajouter `"Arial"` avant `system-ui` si vous souhaitez éviter autant que possible Segoe UI dont l’apparence diffère nettement des autres.

Sans surprise, je vous invite à installer Inter, soit du [site officiel](https://rsms.me/inter/), soit en [téléchargement chez Google Fonts](https://fonts.google.com/specimen/Inter).
Elle est alors disponible en versions variable et statique.
La version statique est très fiable (et je vous conseille, si c’est celle que vous souhaitez, d’installer les 18 fichiers).
La version variable est bien plus élégante en grande taille (et ne demande que 2 fichiers).

Comme je suppose qu’Inter n’est pas installée sur beaucoup d’ordinateurs, je considère que cette page est avant tout un exercice de style.
Et un moyen de me confronter aux divergences d’implémentation et de creuser un peu la logique de [`@font-face`](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/At-rules/@font-face).
