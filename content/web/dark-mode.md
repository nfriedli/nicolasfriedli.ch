+++
title = "Mode sombre et version à fort contraste"
description = "Comment proposer un mode sombre (dark mode) simple? Et des versions à contraste élevé?"
date = 2023-05-15
+++

Comment proposer un mode sombre (dark mode) simple? Et des versions à contraste élevé? Avec des variables CSS, c’est possible en quelques lignes sur un site tel que mon blog.

## Versions claires et sombres par défaut

Si les couleurs ne sont pas définies sur un site, alors il utilise les couleurs par défaut. Les navigateurs choisissent le blanc pour le fond, le noir pour l’écriture et le bleu pour les liens. Les liens visités, survolés, etc. ont d’autres couleurs.

Dans ce cas, le mode sombre, ainsi que les version à fort contraste, sont disponibles par défaut. C’est une option à connaître pour proposer un site très accessible sans efforts. Mieux vaut ne rien définir que faire de mauvais choix. Je pense aux écritures trop fines, aux choix de contrastes problématiques, aux liens invisibles, etc.

Dans le code de la page, cette balise permet de signaler que le site accepte les modes clair ou sombre:

```
<meta name="color-scheme" content="dark light">
```

## Ma feuille de style light/dark

Par des variables CSS, je définis seulement 2 couleurs:

```
:root {
    --background: #d1e4dd;
    --text: #28303d;
}
```

Ensuite, je les applique à toute la page:

```
html {
    background-color: var(--background);
    color: var(--text);
}
```

Pour créer une déclinaison *dark*, je redéfinis mes variable avec une condition (mode sombre demandé):

```
@media (prefers-color-scheme: dark) {
    :root {
        --background:#28303d;
        --text: #FFF;
    }
}
```

Dans mon entête de page, je signale aussi que mon site peut accepter les version claires (*light*) ou foncée (*dark*). Ainsi, le navigaeur peut adapter ses couleurs (par exemple les barres de défilement):

```
<meta name="color-scheme" content="dark light">
```

Je signale que l’interface doit prendre une couleur précise. Dans le cas de mon blog, la couleur foncée (soit du texte, soit du fond):

```
<meta name="theme-color" content="#28303d">
```

## Le cas des liens

Je souhaitent que les liens prennent la couleur du texte. C’est le soulignement qui permettra de les distinguer.

Je n’utilise pas d’autres couleurs pour les cas particuliers (pseudo-classes `:link`, `:visited`, `:hover` et `:active`):

```
a {
    color: inherit;
}
```

Je déroge ici à la [règle Opquast 136](https://checklists.opquast.com/fr/assurance-qualite-web/le-site-napplique-pas-le-meme-style-aux-liens-visites-et-non-visites):

> Le site n’applique pas le même style aux liens visités et non visités.

## Versions à fort constraste

Un navigateur peut demander à afficher une version avec un contraste plus marqué. Il s’agit d’une possibilité expérimentale. **Cette possibilité est actuellement désactivée de mon site.**

Pour l’activer, pourrais redéfinir des variables si des conditions sont remplies (fort constraste demandé):

```
@media (prefers-contrast: more) {
    :root {
        --background: #FFF;
        --text: #000;
    }
}
```

Et (mode sombre et fort constraste demandés):

```
@media (prefers-color-scheme: dark) and (prefers-contrast: more) {
    :root {
        --background: #000;
        --text: #FFF;
    }
}
```

L’ordre des conditions est important. L’historique de la [feuille de style complète](https://github.com/nfriedli/nicolasfriedli.ch/blob/main/assets/css/screen.css) permet de voir comment les différentes situations s’organisent. 

## Modes par défaut

Si le navigateur ne précise rien, parce que l’internaute n’a rien affiché, c’est toujours la version *light* qui prime. 

Pour afficher une version foncée, *dark* doit être configuré explicitement. De même pour les version à fort contraste, qui doivent être explicitement demandées.

Lors du choix d’un thème WordPress, par exemple, il peut valoir la peine de se demander si le choix par défaut est configurable (avec du Javascript). C’est par exemple le cas de [Twenty Twenty-One](https://wordpress.org/themes/twentytwentyone/) qui dispose de modes clairs et sombres ou d’un choix automatique.

## Autres méthodes

Il existe d’autres moyen d’obtenir un *dark mode*, notamment:

- par simple inversion des couleurs: [Poor Man’s Dark Mode Using CSS Filter](https://dev.to/pqina/poor-man-s-dark-mode-using-css-filter-211n)
- avec du Javascript et des subtilités de contrastes d’image ou d’écritures: [A Complete Guide to Dark Mode on the Web
](https://css-tricks.com/a-complete-guide-to-dark-mode-on-the-web/)
- avec un sélecteur de thèmes: [Color Theme Switcher](https://mxb.dev/blog/color-theme-switcher/)

Pour *mon* site, je préfère *ma* méthode, que je pense à la fois simple et évolutive.