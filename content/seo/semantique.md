---
title: Web sémantique
description: L’utilisation simple mais rigoureuse des éléments de syntaxe classiques d’HTML est amplement suffisante pour produire un contenu a forte valeur sémantique. Des bonnes bases valent mieux que du verbiage.
---

Il n’y a pas besoin de beaucoup d’éléments pour produire des pages web avec une forte valeur sémantique.
C’est parce que ces éléments utiles, voire nécessaires, sont peu nombreux qu’il est possible de travailler avec un balisage léger comme Markdown.
Je liste l’essentiel de ce qui permet de produire de bonnes pages web.
J’essaie de proposer le contenu le moins technique possible.

## Structure

Le titre est essentiel.
Il est balisé automatiquement par `h1` dans tous les outils qui produisent des pages web.
En principe, ce serait bien d’utiliser un seul titre `h1` par page, même si HTML permet d’en utiliser plusieurs.
Il ne faut jamais proposer un titre vide, y compris pour des raisons esthétiques.

Ensuite, la page propose sa hiérarchie avec des titres `h2`, `h3`, etc.
HTML propose 6 niveaux de titres, mais je conseille de vous limiter aux niveaux 2 ou 3 dans la majorité des cas.
Une page très structurée de documentation peut naturellement aller plus loin.

Il faut respecter la hiérarchie des titres (un `h3` ne peut jamais suivre directement `h1`).
Et, bien entendu, de ne jamais utiliser les titres pour des raisons visuelles et esthétiques.

L’[extension SEO Detailed](https://detailed.com/extension/) permet de vérifier instantanément la structure de la page finale dans son navigateur.
Je conseille à toutes les personnes qui gèrent un site de l’installer et de l’utiliser régulièrement.

La structure est en principe rendue visuellement, par des espacements, des tailles d’écriture, des polices spécifiques, etc.
Parfois, elle est aussi présente dans une table des matières de la page.
Mais, quel que soit son rendu, elle compte énormément, tant pour des questions d’accessibilité (A11Y) que de référencement (SEO).

## Formatage du texte

Le texte, à proprement parler, n’a pas forcément besoin de beaucoup d’éléments sémantiques.
Il peut être clair sans ajouts particuliers.

### Paragraphes (& sauts de lignes)

L’unité naturelle du texte, c’est le paragraphe.
Avec un principe simple: **1 paragraphe = 1 idée**.
Le web et les paragraphes simples et courts font très bon ménage.
Toute page n’est pas du Proust.

Souvent, il existe un espacement entre 2 paragraphes successifs.
Quand cela ne convient pas, il est possible d’utiliser des sauts de ligne (qui restent toutes dans la même unité sémantique).

C’est utile.  
Parfois.  
Rarement.  
Mais ça existe.

Si votre site propose un espacement problématique entre les paraphraphes (trop petit ou trop grand), il faut le gérer de manière globale.
Une feuille de style CSS ou un petit code dans votre WordPress (CSS additionnel dans la personnalisation) règlent cela pour tout le site, sans changement sémantique.

### Liens

Les liens sont la brique de base du web avec le texte.
Je conseille de toujours les insérer dans le corps du texte, au bon endroit, avec un intitulé correct.

La règle [Opquast 132](https://checklists.opquast.com/fr/assurance-qualite-web/le-libelle-de-chaque-lien-decrit-sa-fonction-ou-la-nature-du-contenu-vers-lequel-il-pointe) est claire:

> Le libellé de chaque lien décrit sa fonction ou la nature du contenu vers lequel il pointe.

Avec des unités de sens de tailles raisonnables et des liens dans le corps du texte, c’est ce qui donne le plus de valeur aux liens.
**Des liens aux intitulés porteurs de sens placés dans le bon contexte sont le meilleur outil sémantique qui soit.**

### Emphases

HTML propose 2 types de mises en évidence:

- l’emphase (`em`) rendue par défaut par un *italique*
- l’emphase forte (`strong`) rendue par défaut par un **gras**

Les balises `i` et `b` sont sémantiquement beaucoup moins intéressantes et à abandonner.

### Citations

Les **citations doivent être balisées avec `blockquote`** et pas être mises simplement en italique ou en gras.
Par défaut dans la majorité des navigateurs, la citation propose un léger retrait.
Ensuite, toutes la variations sont possibles (soit au niveau du site par CSS, soit au niveau de la citation avec WordPress).

La règle Opquast ci-dessus donne un exemple de mise en page de citation sur nicolasfriedli.ch
Il est possible d’affiner les choses avec un attribut `cite`, mais je me perds dans les débats sur le sujet.
Je préfère donner le lien de la source dans l’introduction à l’extrait.

## Listes

Formellement, les listes sont aussi un formatage du texte.
J’en fait pourtant un élément de structure différent parce qu’elles sont particulières.

### Liste non ordonnée

La liste non ordonnée est souvent appelée «liste à puces».
Toutefois, une liste `ul` (*unordered list*) peut se présenter visuellement sans puces.

Dans une recette de cuisine, la liste non ordonnées présente les ingrédients:

- lait
- beurre
- farine
- sel
- poivre

**L’ordre n’est pas fondamental** d’un point de vue sémantique, mais il garde son sens à la lecture.
J’omets les quantités et simplifie; pour réaliser une [sauce Béchamel](https://chefsimon.com/gourmets/chef-simon/recettes/sauce-bechamel--8), je vous renvoie chez [Chef Simon](https://chefsimon.com/).

### Liste ordonnée

Dans une liste ordonnée (`ol` comme *ordered list*), comme on peut s’y attendre, **l’ordre compte**.

Pour poursuivre notre recette de cuisine:

1. Faire fondre le beurre sans coloration.
2. Ajouter la farine.
3. Cuire le roux.
4. Verser le lait en une fois.
5. Etc.

Je trouve les listes ordonnées sous-utilisées sur le web.
**À chaque fois que l’on poste une liste, il faudrait se demander si son ordre a un sens ou non.**

### Liste de définition

La liste de définition est beaucoup trop peu utilisée alors qu’elle est sémantiquement très intéressante.
WordPress, qui motorise la moitié du web, ne la propose malheureusement par défaut.

Elle pourrait se présenter ainsi, dans notre suite culinaire:

roux
: «tant pour tant» de farine et de beurre cuit lentement

sauce
: machin plus ou moins liquide (et plus ou moins bon) pour mettre en valeur (ou pas) un plat

tant pour tant
: préparation dans laquelle tous les ingrédients sont utilisés en quantités égales

Ce qui est intéressant, c’est la **forte valeur sémantique du code**:

```
<dl>

    <dt>roux</dt>
    <dd>«tant pour tant» de farine... </dd>

    <dt>sauce</dt>
    <dd>machin plus ou moins liquide...</dd>

    ...

</dl>
```

Le terme (`dt` ou *description term*) est lié à sa description (`dd` ou *description détails*).
C’est exactement la structure que j’utilise sur les pages paroissiales de [Trouver ma paroisse](https://ma-paroisse.ch/) avec de beaux résultats dans les moteurs de recherche (SERP).

## Éléments multimédias

Pour donner un maximum de valeur aux **images**, il faut toujours leur donner une alternative.
L’attribut `alt` permet de **décrire l’image** et est utile:

- aux internautes qui ne peuvent pas la voir
- aux moteurs de recherche qui peuvent l’indexer
- en cas de problème d’affichage (lenteurs, problèmes de serveur, etc.)

Quand une image est purement décorative, il convient de lui attribuer un `alt` vide plutôt que pas d’attribut.

Pour l’**audio** (podcasts) et la **vidéo**, je constate que les services tiers sont massivement utilisés.
Je conseillerais simplement d’ajouter une transcription, des sous-titres ou un bon résumé sur la page du site.

## Tableaux

**Il ne faut utiliser des tableaux que si les données présentées le justifient.**
L’apparence n’est pas une bonne raison pour utiliser un tableau.
Il existe d’autres moyens de mettre des contenus en page.

Je vous invite à découvrir les [notions de base sur les tableaux](https://developer.mozilla.org/fr/docs/Learn_web_development/Core/Structuring_content/HTML_table_basics) du Mozilla Developper Network (MDN).

## Métadonnées

D’un point de vue sémantique, je conseille de **toujours renseigner la description de la page**.
La règle [Opquast 3](https://checklists.opquast.com/fr/assurance-qualite-web/le-code-source-de-chaque-page-contient-une-metadonnee-qui-en-decrit-le-contenu) est claire:

> Le code source de chaque page contient une métadonnée qui en décrit le contenu.

Certes, la description n’est plus utilisé comme critère de classement par les moteurs de recherche.
Mais elle est toujours importante dans l’affichage des résultats (SERP).

Et, surtout, c’est une excellente manière de travailler que de toujours prendre la peine de rédiger un résumé de 150 ou 200 caractères au moment de la mise en ligne de la page.
Cette introduction pourra être affichée sur le site, par exemple dans la liste des billets.
Et, là, c’est un vrai plus de sens.

## À propos des données structurées

En version courte: **il n’y a pas besoin de données structurées**.
L’utilisation correcte de ce qui est présenté ci-dessus est suffisant.

Elles ne servent presque à rien dans la majorité des cas, parce qu’elles ne font que redire ce qui l’est déjà.
Les données structurées ne prennent de sens que si elles sont vraiment structurées, avec une certaine profondeur.

## À propos des intelligences artificielles (IA)

**Il ne faut faire aucun effort pour «aider» les intelligences artificielles.**
Si une prétendue IA est incapable de lire correctement une page sémantiquement correcte, mieux vaut l’oublier.

Je vous laisse effectuer une recherche sur l’optimisation pour les IA génératives (GEO ou *Generative Engine Optimization*).
C’est globalement du vent.
Des dizaines de «spécialistes» répètent les mêmes mantras pour vendre leur came.

Tout ce que j’ai vu de sérieux sur le sujet, c’est que **les sites bien faits sont biens compris par les grand modèles de langage (LLM)**.
Les règles de bases de HTML, les règles Opquast, les recommandations SEO classiques, c’est parfait!
Et que si l’on veut faire (potentiellement) mieux, il faut attaquer les «données structurées vraiment structurées».

Un fichier `llms.txt` à la racine de votre site ne remplacera jamais un bon contenu.
D’ailleurs, pour le moment, tous les acteurs des IA disent ne pas l’utiliser.
Je signale que l’[analyse d’Olivier Duffez sur llms.txt](https://www.webrankinfo.com/dossiers/ia/fichier-llms-txt) est un des rares contenus de qualité sur le sujet.
