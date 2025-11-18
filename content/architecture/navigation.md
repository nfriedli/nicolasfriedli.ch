---
title: Navigation dans une documentation
description: La navigation doit être claire et facile pour rendre justice à un contenu de qualité. Voici quelques principes de base pour faciliter l’utilisation d’une documentation en ligne.
date: 2025-10-03
---

J’ai émis quelques critiques structurelles à propos d’une documentation qui venait d’être mise en ligne.
Je considérais que l’architecture d’information n’était pas bonne et la navigation peu intuitive.
**La navigation doit être claire et facile pour rendre justice à un contenu de qualité.**
En conséquence, je liste quelques principes ici.

Cette page s’inspire largement de [Building navigation for your doc site: 5 best practices](https://www.writethedocs.org/videos/na/2017/building-navigation-for-your-doc-site-5-best-practices-tom-johnson/) par Tom Johnson et du livre *Information Arcitecture for the Web and Beyond* de Louis Rosenfeld, Peter Morville et Jorge Arango.
Ces ressources sont beaucoup plus complètes que mon billet, mais aussi beaucoup plus longues et en anglais.
Je vous les conseille vivement si le sujet vous intéresse.

## Documentation hiérarchique

Avec Tom Johnson, je considère qu’**une documentation est essentiellement hiérarchique**.
Elle est constituée de page, de sous-pages, de sous-sous-pages, etc.
La hiérarchie peut être plus ou moins profonde et plus ou moins complexe.

L’avantage de la hiérarchie, c’est qu’elle permet de comprendre intuitivement ce qui est dans un environnement proche.
De ce point de vue, le blog n’est pas un bon outil.
Il insiste sur la chronologie, qui importe peu dans une documentation.
La proximité temporelle n’apporte rien (d’autre que de la confusion).

Le wiki, même s’il crée des proximités par le maillage interne, est souvent trop complexe à appréhender (tant pour les personnes qui l’éditent que pour les internautes).
Il permet certes de rédiger une documentation, mais il est généralement faible dans la création de menus, de fils d’Ariane (*breadcrumbs*), de pages filles, etc.

## Page mère

Quand je suis dans une documentation, je souhaite **savoir immédiatement où je me trouve**.
Il m’arrive de débarquer sur une page par un lien direct ou un moteur de recherche et je ne souhaite pas tout parcourir pour comprend mon «emplacement».

Dans tous les cas, je dois au moins avoir la possibilité de **remonter facilement d’un niveau, vers la page mère**.
Il est possible de donner une information de «positionnement» par un fil d’Ariane.
Il est aussi possible de le faire par un menu dont les pages ancêtres sont surlignées.

Je préfère les fils d’Ariane visibles aux menus (souvent cachés sur petits écrans).

## Pages filles

Lorsque je me trouve sur une page quelconque, je souhaite **voir toutes les pages filles d’un seul coup d’œil** (si elles existent).
Dans une arborescence informatique classique, on pourrait dire que lorsque qu’un répertoire est ouvert dans un explorateur de fichiers, il montre tous les sous-répertoires et tous les fichiers qu’il contient.

Autrement dit, je peux facilement:

- voir tout ce qui est traité à cet endroit de la documentation
- passer directement à chaque sujet en 1 clic

Là aussi, je souhaite que le maximum de contenu soit visible immédiatement, sans clic inutile sur un «onglet» ou un bloc de détails qui s’ouvre.

## Pages sœurs

Dans l’idéal, je souhaiterais **voir directement les pages sœurs** à partir de n’importe quelle page.
Ainsi, je n’a pas besoin de faire 2 clics (page mère puis page fille) pour y accéder.

L’intérêt principal de la visualisation des pages sœurs n’est pas d’économiser 1 clic.
Mais plutôt de rendre la structure générale de la documentation beaucoup plus limpide, de la comprendre et de l’apprivoiser.

## Navigation interne à une page

Lorsqu’une page est longue et complexe, je trouve confortable de **pouvoir sauter à un intertitre précis** par une table des matières.
C’est aussi un avantage pour certains moteurs de recherche qui valorisent ce type de liens dans les résultats (SERP).
C’est le cas de Google, mais aussi de l’excellent système statique [Pagefind](https://pagefind.app/).

Ce qui est intéressant, c’est qu’il est alors possible de renvoyer les internautes à un endroit précis de la documentation.
Je vous donne un exemple avec les [ancres dans *Material for MkDocs*](https://squidfunk.github.io/mkdocs-material/reference/content-tabs/?h=anchor#anchor-links) dont il vaut la peine d’étudier tout le site.

## Liens contextuels

Finalement, une documentation a presque toujours **besoin de liens contextuels**, dans le corps du texte.
C’est là qu’est portée l’attention lors de la lecture et c’est un endroit précieux pour aider à la navigation.
Et ce sont ces liens qui ont le plus de valeur pour les moteurs de recherche.

Dans l’idéal, les liens internes à la documentation sont distincts des liens externes ([règle Opquast 142](https://checklists.opquast.com/fr/qualite-numerique/les-liens-internes-et-externes-sont-differencies)).

## Plan complet

Parfois, un [plan du site](/sitemap/) est disponible; c’est le cas ici.
Il permet de visualiser la structure globale du contenu.
Et peut-être de faire des recherches directes sur les titres.

Dans le cadre d’une documentation important il est intéressant de disposer du **plan complet de la documentation**.
Il doit bien montrer la structure et les niveaux pour être utile.
Une simple liste de pages ne fait pas l’affaire.

## Références

En plus des 2 sources citées en début d’article, je vous conseille:

- [Write the Docs](https://www.writethedocs.org/), qui est une mine d’or sur la thématique de la documentation technique
- le *framework* [Diátaxis](https://diataxis.fr/), qui propose des réflexions fondamentales sur le classement d’une documentation
- le logiciel [Sphinx](https://www.sphinx-doc.org/), créé en Python pour la documentation de ce langage de programme, hyper puissant mais relativement difficile à prendre en main (MkDocs cité dans l’article est plus simple d’accès)
- le thème [Furo](https://pradyunsg.me/furo/) pour Sphinx, pour la clarté de son menu (et du site en général)
