---
title: Recherches Google avancées
description: Utiliser des opérateurs logiques et des conditions pour tout trouver rapidement. Et pour se construire des alertes Google pour une veille efficace.
aliases:
- /blog/recherche-google-avancee/
---

Le moteur de recherche Google est souvent utilisé de manière basique.
Comme il est plutôt efficace, quelques mots suffisent souvent.
Toutefois, quelques astuces permettent d’affiner ses recherches.

La maîtrise des recherches est une compétence ~~utile~~ nécessaire pour effectuer une veille efficace.

**Un conseil:** à chaque étape de cette page, faites des tests avec vos propres requêtes! C’est en utilisant ces critères que vous en comprendrez vraiment l’utilité (et les mémoriserez).

## Documentation de Google

Le moteur de recherche propose des pages de [documentation](https://support.google.com/websearch) intéressantes.
Par exemple:

- [Affiner les recherches Google](https://support.google.com/websearch/answer/2466433)
- [Effectuer une recherche avancée sur Google](https://support.google.com/websearch/answer/35890)
- [Utiliser le filtre de langue des résultats dans la recherche Google](https://support.google.com/websearch/answer/13485060)

Si c’est toujours une bonne idée de lire les documentations officielles, je préfère vous donner rapidement les requêtes les plus utiles.

Je signale qu’il existe un [formulaire de recherche avancée](https://www.google.ch/advanced_search), mais je n’aime pas l’utiliser.
Les requêtes textuelles me parlent plus qu’un formulaire.

## Opérateurs logiques

### Rechercher une expression *et* une autre avec `AND`

Par défaut, une recherche sans précisions particulières recherche tous les mots.
Par exemple:

    Nicolas Friedli

Je peux préciser explicitement que je souhaite tous ces mots avec:

    Nicolas+Friedli

L’utilisation de `AND` au lieu de `+` est possible:

    Nicolas AND Friedli

Ce type de recherche est celui que vous effectuez la plupart du temps.

### Recherche une expression *ou* une autre avec `OR`

Le *ou* n’est jamais explicite.
Il faut donc le préciser dans sa recherche, avec une des syntaxes suivantes:

    Nicolas|Friedli
    Nicolas OR Friedli

C’est peu utile ainsi.
Je pourrais effectuer successivement les 2 recherches pour avoir le même résultat.

Le `OR` n’est pas exclusif, ce qui signifie qu’il peut y avoir des résultats avec 1 mot, l’autre mot ou les 2.

Mais c’est très puissant dans les recherches complexes dont on parlera ci-dessous.

### Exclure des résultats de recherche avec `-`

L’exclusion de résultat est intéressante pour éviter des résultats parasites.
Il existe un Nicolas Friedli qui s’occupe de pieds.

Donc, je pourrais faire une recherche comme:

    Nicolas Friedli -podologue -pédicure

Comme il est possible de recherche plusieurs mots, il est possible d’en exclure plusieurs.

Les exclusions sont très intéressantes quand on utilise des requêtes complexes pour les actualités Google.

### Rechercher un motif exact avec `" "`

L’utilisation de guillemets permet la recherche d’une expression exacte.
Ce qui signifie que les 2 requêtes suivantes donnent des résultats différents:

    "Nicolas Friedli"
    "Friedli Nicolas"

Comme les algorithmes de recherche ont tendance à corriger automatiquement les requêtes, c’est un outil nécessaire dans certains cas.
C’est particulièrement puissant quand un nom a une orthographe particulière.

Le motif exact peut être un seul mot.
Ainsi, si je veux recherche *Nicaulas*, j’entrerai:

    "Nicaulas"

Et là, malgré les guillemets, Google me propose des résultats pour *Nicolas*.
Je peux ensuite forcer la recherche avec le lien proposé: *Essayez avec l’orthographe "nicaulas"*.

### Combinaisons d’opérateurs logiques

Pour effectuer des recherches d’actualité dans le domaine du protestantisme réformé, j’utilise:

    "(église|paroisse) (protestante|réformée)"

Ce qui signifie que je recherche 4 expressions exactes:

    "église protestante" OR "église réformée" OR "paroisse protestante" OR "paroisse réformée"

Mais j’évite les articles comprennent les mots *église* et *paroisse* seulement.

## Recherche dans un seul site avec `site:`

C’est un des outils méconnus les plus puissants: la recherche sur un seul nom de domaine ou une partie de site.
Un exemple tout simple:

    "nicolas friedli" site:reformes.ch

C’est une combinaison d’une expression exacte (`" "`) et d’une limitation à un seul site.

Une utilisation basique mais efficace de ce genre de requête, c’est:

    site:eliojaillet.ch

Ainsi, le *théologien vaudois éclectique* verra comment s’affichent les pages de son site dans Google (et quelles pages sont indexées).

Il n’est pas nécessaire d’utiliser un nom de domaine entier.
Une extension seule est aussi possible.
Par exemple:

    site:.fr "Elio Jaillet"

Les négations sont aussi possibles:

    "Elio Jaillet" -site:eliojaillet.ch

Et quand vous souhaitez effectuer une recherche sur un blog hébergé chez wordpress.com, utilisez quelque chose comme:

    site:sousdomaine.wordpress.com

Ces recherches sont très (très très) utiles quand un site ne dispose pas de moteur de recherche ou que son moteur de recherche est médiocre.

## Recherche par type de fichiers avec `filetype:`

J’utilise surtout la recherche par type de fichiers pour m’attaquer aux PDF.
Surtout quand ils ne sont pas référencés par le moteur de recherche interne ou que le moteur de recherche n’est pas assez bon.

Un exemple concret:

    filetype:pdf site:ne.ch "piste cyclable"

Avec ce que vous savez déjà, vous n’aurez aucune difficulté à comprendre ce que fait cette requête.

Essayez avec votre propre nom:

    "Prénom Nom" OR "Nom Prénom" filetype:pdf site:.ch

Un outil de veille très intéressant.

## 1 exemple de recherche pour des sites WordPress

Pour les sites WordPress, j’aime bien ajouter des limitations.
En particulier quand ils comportent beaucoup de catégories et de tags.

Par exemple, sur le site d’Armin Kressmann (qui avait conservé une ancienne version de ce document), la liste des articles:

    site:ethikos.ch -site:ethikos.ch/category -site:ethikos.ch/tag -site:ethikos.ch/page

Et en version bien plus élégante:

    site:ethikos.ch -inurl:(category|tag|page)

Il y a dans cette ligne les notions de `site:`, la négation `-`, le `|` (ou).
Et j’ajoute le sélecteur `inurl` qui signale un motif dans l’adresse de la page (ou URL).

## Utiliser ses recherches pour des alertes Google

La construction d’une requête complexe peut prendre un peu de temps, mais elle est très utile pour les alertes Google.

Je construis sans la tester une requête de veille:

    "(église|paroisse) (protestante|réformée)" site:.ch -site:eren.ch -site:eerv.ch

Vous avez compris:

- je souhaite une des 4 expressions dont j’ai parlé avant
- sur un site «en principe suisse» (en `.ch`)
- mais pas sur les sites de l’EREN ou de l’EERV

Ajoutez une requête de ce type dans les [alertes Google](https://www.google.ch/alerts?hl=fr), puis faites-vous envoyer un mail (ou abonnez-vous par RSS)!
C’est redoutablement efficace.

----

Évidemment, pour faire des tests sur votre propre site, il faut qu’il soit bien indexé par Google.
C’est aussi un moyen de tester son référencement.

----

Besoin de compléments?
Problèmes à établir une requête précise?
Souhait d’une formation?
Contactez-moi!
