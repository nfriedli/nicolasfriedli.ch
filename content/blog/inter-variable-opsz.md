---
title: Inter variable avec taille optique
description: L’astuce pour obtenir la variation de taille optique (opsz) dans son navigateur avec une polices locale. Avec exemple de code et proposition de font stack.
date: 2025-02-04
categories:
- polices
---

Sur mon poste Linux, la police d’écriture Inter installé localement est variable (graisses de 100 à 900).
Mais elle n’utilise pas les tailles optiques (`opsz`).
Cela (me) pose problème, car Inter est trop espacée en grande taille, pour les titres et les intertitres.

Si j’utilise Inter en webfont (fichier `woff2`), tout va bien.
La police est variable en graisse (`wght`) comme en taille (`opsz`)

Dans ma recherche pour proposer une *font stack* (pile de polices) de qualité sans recourir à des envois de fichiers, je croyais avoir enfin trouvé la solution.

**Comme Chrome et Firefox ne sont pas d’accord sur la manière de nommer une police dans un `font-face`, cette solution ne fonctionne pas toujours!**
Si vous souhaitez une solution qui marche partout en 2025, il faut passer par un webfont...

## Inter avec `font-face`

Pour obtenir la variation tant souhaitée, je déclare la police avec `font-face`, comme si c’était une police distante:

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

**Cette déclaration ne fonctionne pas dans Chrome pour Windows.**

## Proposition de *font stack*

Désormais, je peux créer une *font stack* optimale (les familles génériques n’ont pas de guillemets):

```
html {
  font-family: 
    "Inter Variable",   /* Inter variable, déclarée précédemment, si installée            */
    ui-sans-serif,      /* utilise San Francisco (variable) disponible sur iOS            */
    "Inter",            /* Inter en version statique (non variable), si installée         */
    "Roboto",           /* Roboto, si installée                                           */
    system-ui,          /* Segoe UI sur Windows, Roboto sur Android, à choix sur Linux    */
    sans-serif;         /* la police sans empattement de secours                          */
}
```

Avec une telle «pile d’écritures», je suis certain que vous aurez quelque chose de beau et de très lisible.
Vous pouvez ajouter `"Arial"` avant `system-ui` si vous souhaitez éviter autant que possible Segoe UI dont l’apparence diffère nettement des autres.

Sans surprise, je vous invite à [installer Inter](https://rsms.me/inter/download/).
Soit en version variable, soit en version statique.
La version statique est plus fiable et je vous conseiller d’installer les 18 fichiers.

Et sans surprise non plus, au vu des problèmes d’implémentation, ces propositions resteront un simple exercice de style.
