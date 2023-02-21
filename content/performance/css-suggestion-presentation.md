+++
title = "Feuilles de style CSS & suggestion de présentation"
date = 2023-02-20
draft = true
+++

Rappel par Matthias Ott dans [Forging Links - Web Design Engineering and CSS](https://www.css.cafe/forging-links-web-design-engineering-and-css/):

Dans l'article original: 

> If you use style sheets properly, to suggest the appearance of a page, not to control the appearance of a page, and you don’t rely on your style sheet to convey information, then your pages will “work” fine in any browser, past or future.
> 
> https://alistapart.com/article/dao/

En français, par pompage.net:

> Si vous utilisez correctement les feuilles de style, pour suggérer l'apparence d'une page et non pour la contrôler, et que vous ne dépendez pas de la feuille de style pour acheminer l'information, alors vos pages «marcheront» bien dans tous les navigateurs, existants ou à venir. 
> 
> http://www.pompage.net/traduction/dao

Pari sur l'avenir

Pérennité

Efficience

Tout n'est que suggestion: taille d'écran, polices, blocages, etc.

Sur ce site, en version adaptée (j'utilise des variables CSS):

```css
html {
    font-family:    
        system-ui,          
        -apple-system,      
        "Segoe UI",         
        Roboto,   
        "Helvetica Neue", 
        "Noto Sans", 
        "Liberation Sans", 
        Arial, 
        sans-serif, 
        "Apple Color Emoji", 
        "Segoe UI Emoji", 
        "Segoe UI Symbol", 
        "Noto Color Emoji";
}
```

Et pour les extraits de code, nombreux sur mon site:

```css
code, pre {
    font-family:    
        SFMono-Regular,         
        Menlo,
        Monaco,                 
        Consolas, 
        "Liberation Mono", 
        "Courier New",          
        monospace;       
}
```

Vouloir tout contrôler, boulot de graphiste, pas de web... Surtout, pas efficient du tout.