+++
title = "Markdown a gagné"
description = "Le langage de balise léger Markdown est le plus utilisé aujourd’hui. De nombreux outils le produisent ou le comprennent. Il est facile à apprendre et suffisant pour la grande majorité des usages."
date = 2025-09-11
+++

Le langage de balisage léger Markdown a gagné la course.
Il n’est pas forcément le plus puissant, il n’est pas forcément le meilleur, mais il est devenu la norme.
Il permet de structurer les textes de manière simple et rapide.
Il est accessible à toute personne capable d’utiliser un outil informatique.

Cette page n’est pas un tutoriel ou un guide.
Elle n’a pas vocation à faire le tour du sujet.

## Langage de balisage léger

Entrons dans le vif du sujet.
Je vous donne un exemple plutôt que de laborieuses explications:

```
Si vous arrivez à **lire** ce texte, c’est parfait!
Vous comprenez que Markdown insiste sur le *sens* plutôt que sur la *forme*.

Un langage de balisage léger doit être:

- facile à rédiger
- facile à lire en code
- facile à transformer

Et voilà le résultat...
```

Voici le résultat dans la page web (le tout placé dans une citation):

> Si vous arrivez à **lire** ce texte, c’est parfait!
> Vous comprenez que Markdown insiste sur le *sens* plutôt que sur la *forme*.
>
> Un langage de balisage léger doit être:
>
> - facile à rédiger
> - facile à lire en code
> - facile à transformer
>
> Et voilà le résultat...

Un langage de balisage léger, c’est la possibilité d’une mise en forme par le sens avec des signes très simples.

En HTML, pour faire une liste, il faudrait faire:

```
<ul>
    <li>facile à rédiger</li>
    <li>facile à lire en code</li>
    <li>facile à transformer</li>
</ul>
```

C’est moins facile à rédiger et plus compliqué à lire.
Et pas naturel du tout.
Seul avantage, il n’y a rien à transformer pour l’afficher sur le web.
Mais Markdown n’est pas seulement pour le web...

## Syntaxe de Markdown

Je ne vous explique pas la syntaxe de Markdown ici.
Elle est très bien présentée dans [Markdown Reference](https://commonmark.org/help/).
Vous pouvez aussi l’apprendre directement dans le [Markdown Tutorial](https://commonmark.org/help/tutorial/) interactif.

Ce qu’il faut retenir, c’est que cette syntaxe très simple permet de:

- structurer le contenu du document par des titres hiérarchiques (jusqu’à 6 niveaux)
- mettre votre texte en forme avec de l’**emphase forte** (gras), de l’*emphase faible* (italique), des contenus ~effacés~ barrés
- créer des listes à puces, numérotées (avec plusieurs niveaux), voire des listes de définitions
- proposer des citations, avec des imbrications possibles (citation dans la citation)
- publier du code (comme plus haut sur cette page)
- créer des tableaux simples
- pourrir la vie des internautes avec des notes de bas de page
- faire vivre le web avec des liens
- ajouter des images

Il y a tout le nécessaire pour ajouter les éléments de *sens* à vos textes.
Les outils de transformation (par exemple votre site web), se chargent de le mettre en *forme*.

Le problème, c’est que Markdown propose plusieurs dialectes, qui ne se comprennent pas tous.
Autrement dit, il existe plusieurs balisages différents et certains ne sont pas toujours bien interprétés.
Depuis quelques années, l’initiative [CommonMark](https://commonmark.org/) vise à uniformiser la syntaxe.
Beaucoup d’outils se fondent sur ces règles aujourd’hui.

## Autres langages de balisage léger

Si je dis que Markdown a gagné, c’est que d’autres ont «perdu» la course.

- [reStructuredText](https://fr.wikipedia.org/wiki/ReStructuredText) est plus puissant que Markdown.
Il n’est pas orienté spécifiquement pour le web et permet des constructions très raffinées.
C’est le langage par défaut de l’excellent [Sphinx](https://www.sphinx-doc.org/en/master/index.html).
Mais Markdown est tellement répandu que (même) Sphinx propose une extension spécifique pour lui.

- [AsciiDoc](https://asciidoc.org/) propose plus de richesse sémantique que Markdown.
Il cherche aussi à proposer un code lisible et peut être transformé en plusieurs formats de sortie intéressants.
Je n’ai jamais apprécié cette syntaxe.

Mais ces langages de balisage sont pénibles à utiliser pour une personne qui ne passe pas son temps à rédiger des documentations techniques.
Le choix pragmatique, c’est bien Markdown.

## Markdown est partout

Les pages web comme celles que vous êtes en train de lire ne sont pas le seul terrain de jeu de Markdown.

Le chercheur Arthur Perret a publié l’excellent [Le futur de l’édition scientifique est au format texte](https://www.arthurperret.fr/blog/2025-06-13-le-futur-de-l-edition-scientifique-est-au-format-texte.html).
Il y défend un usage de Markdown et [Pandoc](https://pandoc.org/) pour le monde de la recherche.
Je pense qu’il a raison.

À l’opposé des textes longs et complexes du monde académique, vous pouvez aussi utiliser certains éléments de Markdown dans WhatsApp, Slack, Discourse ou Telegram.
Plusieurs logiciels de mail formattent bien les `*`, `**` ou `>` (citation).

Gutenberg, l’éditeur interne de WordPress, comprend aussi une partie de Markdown à la rédaction.
Par exemple, `##` permet d’insérer un intertitre dans quitter le clavier.
Et `-` commence une vraie liste à puces automatiquement.

Pour vous faire une idée de l’état des lieux, je vous conseille cette [liste d’outils qui parlent Markdown](https://www.markdownguide.org/tools/).
Elle est non exhaustive, mais donne quelques pistes.

## Éléments de réflexion

À l’université, j’utilisais [LaTeX](https://fr.wikipedia.org/wiki/LaTeX) pour mes travaux.
J’aurais adoré disposer de Markdown (et de [Git](https://fr.wikipedia.org/wiki/Git)).
La possibilité de collaborer vraiment, la maintenance d’un corpus en ligne (ou non), l’amélioration continue, etc.

Le premier paragraphe de l’article d’Arthur Perret cité précédemment:

> Ma recherche est de nature épistémologique: j’examine la manière dont la connaissance advient, est construite.
> Plus précisément, j’étudie les outils d’écriture, les processus d’analyse et de synthèse de connaissances, ainsi que l’édition scientifique.
> C’est une recherche qui est ancrée dans le monde du texte et du document.

L’édition de documents dans un [éditeur de textes](https://fr.wikipedia.org/wiki/%C3%89diteur_de_texte) est beaucoup plus efficace que dans un traitement de texte (comme Word).
Elle permet de séparer la forme du fond, elle produit des [fichiers textes](/blog/txt/) légers et pérennes.

Je m’étonne à chaque fois que je vois des personnes utiliser des traitements de texte pour des tâches qui devraient se faire dans des éditeurs.
Je m’effraie en pensant au temps perdu en mise en page au moment de la rédaction, à l’énergie perdue face aux bugs et à la lourdeur de ces outils.
J’imagine le pire pour la pérennité des documents produits.

Sur GitHub, vous trouverez la [source de cette page](https://github.com/nfriedli/theologique.ch/blob/main/content/blog/markdown.md).
Je ne vous ment pas, c’est vraiment très simple.
Vérifiez!
