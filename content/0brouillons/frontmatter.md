+++
title = "Frontmatter & métadonnées"
description = "Les fichiers Markdown comportent souvent des métadonnées. Le «frontmatter» permet de structurer ses données pour les réutiliser efficacement. Et avec souplesse."
date = 2025-09-30
+++

J’ai parlé plusieurs fois de [fichiers au format texte](/blog/txt/) et de [balisage léger avec Markdown](/blog/markdown/).
Mais je ne vous ai pas encore tout dit.

Parfois, les fichiers comportent aussi des métadonnées.
C’est par exemple le cas des contenus de theologique.ch.
*Frontmatter*, c’est le petit nom de la partie réservée aux métadonnées en début de fichier.

**Ce billet est un peu technique.**
Mais je pense qu’il est possible d’en comprendre les grands principes et de saisir les enjeux des métadonnées en *frontmatter*.
Sachez qu’elles peuvent changer votre vie (pour le meilleur)!

## Métadonnées simples

La version toute simple, c’est:

```toml
+++
title = "Frontmatter & métadonnées"
date = 2025-09-30
+++
```

Les `+++` signalent simplement le début et la fin de ce passage (ici en syntaxe TOML).
La [source de la page sur laquelle vous vous trouvez](https://github.com/nfriedli/theologique.ch/blob/main/content/blog/frontmatter.md) permet de visualiser les métadonnées.

Jusque là, rien de très étonnant.
Mais ce qui est intéressant avec le *frontmatter*, c’est qu’il peut «héberger» plein d’autres données.

## Métadonnées plus complètes

Par exemple, pour le site [Trouver ma paroisse](https://ma-paroisse.ch/), certaines pages ne sont constituées que du *frontmatter*.
Je vous invite à regarder:

- la [paroisse de La BARC](https://ma-paroisse.ch/neuchatel/barc/)
- la [source de La BARC](https://raw.githubusercontent.com/nfriedli/ma-paroisse.ch/refs/heads/main/content/neuchatel/barc.md) (avec un *frontmatter* en YAML, délimité par `---`)

C’est parce que les données sont structurées qu’il est possible d’alimenter le moteur de recherche, de faire des tris intéressants, etc.

Dans le même esprit, pour l’ancien eglise-ouvertes.ch, j’avais créé des *frontmatter* (formatés en JSON, délimités par `{` et `}`).
Pour le temple de Colombier, dans la même paroisse de La BARC:

```json
{
    "title": "Temple de Colombier",
    "site": "https://www.eren.ch/barc/batiments/temple-de-colombier/",
    "maps": "https://goo.gl/maps/3KSuvNTqXsdSFmnc9",
    "rue": "Rue du Château 3a",
    "npa": 2013,
    "localite": "Colombier",
    "commune": "Milvignes",
    "canton": "Neuchâtel",
    "latitude": 46.9666066,
    "longitude": 6.8623137,
    "ouverture": "7/7",
    "horaire": "8:00-20:00",
    "pbc": "B",
    "vitraux": ["Pierre-Eugène Bouvier"]
}
```

Je vous perds?
Vous ne comprenez pas immédiatement pourquoi créer un semblant de base de données ainsi?
Voici pourquoi c’est génial.

## Un exemple pratique

Vous mettez des prédications ou des discours en ligne?
Il est facile de les documenter sérieusement, que ces informations soient affichées publiquement ou non.
Par exemple, pour la prédication [Des suiveurs invités à suivre](https://dianefriedli.ch/des-suiveurs-invites-a-suivre/) par Diane Friedli:

```toml
title = "Des suiveurs invités à suivre"
lectures = [
    "Sagesse 9,13-18", 
    "Philémon 8-17 ", 
    "Luc 14,25-33"
    ]

[[cultes]]
lieu = "Grandchamp"
date = 2025-09-07

[[cultes]]
lieu = "Auvernier"
date = 2025-09-14
```

Alors, le truc rend possible de lister tous les cultes à Grandchamp, de proposer une chronologie de toutes les prédications, de créer un catalogue de livres bibliques utilisés.

## Souplesse du *frontmatter*

Ce qui est génial avec un *frontmatter*, c’est que l’on peut ajouter un champ à tout moment, sans besoin de modifier une base de données.
Celles et ceux qui ont manipulé des bases de données savent qu’ajouter un contenu n’est pas toujours trivial.
Par exemple, pour signaler si un enregistrement existe:

```toml
audio = true
video = false
```

Et pourquoi pas ajouter des informations personnelles utiles:

```toml
sources = [
    "Commentaire intégral de la Bible (Antoine Nouis)",
    "Commentaire L&F (François Bovon)"
]

[[cultes]]
lieu = "Grandchamp"
date = 2025-09-07
audience = 47

[[cultes]]
lieu = "Auvernier"
date = 2025-09-14
audience = 51
```

## Pour une base documentaire collaborative?

Vous avez compris l’idée.
Il serait très simple de créer une base de données collaborative de prédications (par exemple).
Celles et ceux qui le souhaitent déposent un fichier Markdown sur GitHub.
C’est facile, [interopérable](https://fr.wikipedia.org/wiki/Interop%C3%A9rabilit%C3%A9), ouvert, pérenne et efficace.

J’imagine aussi plein de choses pour les chercheuses et chercheurs en théologie, en sciences humaines, etc.
Ne sachant pas si de telles considérations intéressent celles et ceux qui me lisent, je ne développe pas plus (pour le moment).

À vous de me relancer si ça vous parle!
