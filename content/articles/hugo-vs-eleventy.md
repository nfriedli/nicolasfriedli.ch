---
title: Hugo ou Eleventy? De grandes différences
date: 2020-08-29
description: 
images: 
    - 
draft: true
---

Vus de loin, Eleventy (11ty) et Hugo sont des cousins.
Pour une personne qui vient d'un CMS (Content Management System ou système de gestion de contenu) standard comme WordPress ou Drupal, ils sont même des frêres jumeaux.

Tous les deux génèrent rapidement un site statique à partir d'un ensemble de pages rédigées à l'aide d'un langage de balisage léger (par exemple markdown).
Tout se passe localement sur son ordinateur.
Il n'y a pas d'interface graphique, pas de login dans le navigateur, etc.
À la fin du processus de construction, le site est envoyé sur le serveur.

Mais tout cela, c'est vu de loin.
Dès que l'on compare dans le détail, on constate des choix très différents entre ces deux SSG (Static Site Generator  ou générateur de site statique).
J'essaie de passer les différentes principales en revue.

 ## Sens du projet



https://gohugo.io/about/what-is-hugo/

 Hugo is for people that prefer writing in a text editor over a browser.

Hugo is for people who want to hand code their own website without worrying about setting up complicated runtimes, dependencies and databases.

Hugo is for people building a blog, a company site, a portfolio site, documentation, a single landing page, or a website with thousands of pages.

https://www.zachleat.com/web/introducing-eleventy/

Another static site generator? Yes. But why? Fair question.

Eleventy was created for three reasons:

    Flexibility
    Betting on JavaScript
    Not a JavaScript Framework

 ## Installation

 simple binaire / pas d'installation

 node + extensions

 ## Structure et souplesse

 page vs list/single

 importance +/- grande des données

 ## Configuration

 text/yaml vs js

 ## Batteries incluses

 not. minify + images
 rss sitemap minify

 ## Pagination

 simple découpage vs création à partir de données
 
 ## Limites et complexité

 permet presque tout, mais pas extensible

 permet tout, mais presque rien par défaut

 ## En conclusion

 critères décisifs:
 - installation binaire
 - pagination
