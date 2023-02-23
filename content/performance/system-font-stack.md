+++
title = "Polices d’écriture système"
date = 2023-02-23
+++

Le choix des polices d’écriture d’un site semble être capital. C’est ce que l’on peut en déduire en voyant nombre de pages qui requièrent beaucoup de téléchargement distants (souvent chez Google Fonts). Pourtant, il est possible de créer un site en utilisant uniquement des polices systèmes (*system font stack*). C’est meilleur du point de vue de la performance. Et souvent tout aussi bon d’un point de vue visuel.

## Le principe du «font stack»

Sur le web, les polices sont appelées par une série de choix. Une «pile de polices» (*font stack*) est proposée. La première fonte disponible est affichée. Un exemple classique:

```css
html {
    font-family: Helvetica, Arial, sans-serif;
}
```

Si la police Helvetica est disponible sur le périphérique (c’est le cas sur les périphériques Apple). Si non, c’est Arial qui sera choisie (sur presque tous les systèmes). Si non, c’est la police sans empattement par défaut (par exemple Roboto sur Android).

Avec l’arrivée de Google Fonts (et d’autres services analogues), il est simple d’utiliser une police qui n’est pas disponible sur le périphérique de consultation. Par exemple:

```css
@import url("https://fonts.googleapis.com/css2?family=Roboto:ital,wght@0,400;0,700;1,400;1,700&display=swap");
html {
    font-family: Roboto, sans-serif;
}
```

Ainsi, Roboto sera téléchargée chez Google et affichée. En cas de problème, c’est la police sans empattement par défaut qui sera utilisée. Génial... sauf que cela pose des problèmes:

- des lenteurs (surtout en utilisant `@import` comme ici)
- des transferts pas toujours utiles
- une dépendance à des services tiers
- des problèmes de confidentialité et de respect de la vie privée (voir, par exemple: [Google Fonts : quand la police enfreint le RGPD](https://swissprivacy.law/131/))

En revenant à des classiques du web, on se souvient que le choix d’une *police exacte* n’est pas une nécessité. Le retour à un *font stack* un peu plus sérieux que celui ci-dessus est une excellente idée.

## La feuille de style est une suggestion de présentation

Le développeur Matthias Ott cite un passage intéressant de 2000 dans son excellente présentation [Forging Links - Web Design Engineering and CSS](https://www.css.cafe/forging-links-web-design-engineering-and-css/):


> If you use style sheets properly, to suggest the appearance of a page, not to control the appearance of a page, and you don’t rely on your style sheet to convey information, then your pages will “work” fine in any browser, past or future. ([A Dao of Web Design](https://alistapart.com/article/dao/))

En français, [traduit par pompage.net](http://www.pompage.net/traduction/dao):

> Si vous utilisez correctement les feuilles de style, pour suggérer l’apparence d’une page et non pour la contrôler, et que vous ne dépendez pas de la feuille de style pour acheminer l’information, alors vos pages «marcheront» bien dans tous les navigateurs, existants ou à venir.

Vous avez compris le truc. Si j’accepte l’idée d’une *suggestion* de présentation plutôt qu’une présentaton exacte, j’ai toutes les raisons d’utiliser une *font stack* du système. En passant, l’idée de gérer une *présentation exacte* est aujourd’hui illusoire en regard de la multiplication des tailles d’écran et des différentes résolutions.

En choisissant une police système, c’est un pari sur le présent et l’avenir. Les systèmes d’exploitation proposent toujours plus d’excellentes polices. Et il y a tout à parier que cela va continuer. *San Francisco* chez Apple, *Roboto* pour Android, *Segoe UI* pour Windows ou *Noto* pour Linux sont excellentes. Non seulement on évite ainsi certaines horreurs typographiques, mais on gagne tant en performance qu’en cohérence. Elles sont de plus mises à jour avec le système.

**Note.** Je garde des réserves sur la générique `system-ui`, pas toujours convaincu que le site doit avoir la même tête que l’interface.

## Sur ce site

Sur ce site, j’ai choisi un pile de polices qui ressemble à ceci:

```css
html {
    font-family:    
        Roboto,             /* Android et, souvent, Linux */
        Inter,              /* pour qui l’a installée */
        -apple-system,      /* Apple modernes */
        "Noto Sans",        /* Linux */
        "Liberation Sans",  /* Linux */
        "Segoe UI",         /* Windows récents */
        Arial,              /* presque tout le monde */
        sans-serif;         /* et sinon... */
}
```

**Note.** J’ai relégué *Segoe UI* en bas de liste, parce que je ne raffole pas de cette police. Elle est toutefois utile pour les internautes qui utilisent Windows et plus complète qu’*Arial*.

Et pour les extraits de code, nombreux:

```css
code, pre {
    font-family:
        "Roboto Mono"       /* Android et, souvent, Linux */    
        SFMono-Regular,     /* Apple récents */
        Menlo,              /* Apple moins récents */
        Monaco,             /* Apple plus anciens */
        Consolas,           /* Windows */
        "Noto Sans Mono",   /* Linux */
        "Liberation Mono",  /* Linux */
        monospace;          /* et sinon...*/
}
```

Il n’a pas été simple d’accepter de lâcher prise et de ne faire qu’une *suggestion*. C’est toutefois bien ainsi que fonctionne le web. J’ai bien conscience qu’il est possible d’atteindre des scores de performances excellent avec des polices web, le choix des polices du système me semble actuellement le meilleur pour ce site.

**Note.** Je connais les polices web locales, le préchargement, `woff2`, le *subsetting* et `font-display: optional;`. Je les utilise sur des sites qui le requièrent ou pour des client·e·s qui exigent des fontes précises.