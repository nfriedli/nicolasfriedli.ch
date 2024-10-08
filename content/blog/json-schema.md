---
title: Mon premier JSON Schema
description: Rédaction d’un JSON Schema pour formaliser les contenus du site Églises ouvertes en Suisse romande.
date: 2024-03-18
lastMod: 2024-10-08
categories: 
- json
---

Le format JSON (JavaScript Object Notation) est un des plus utilisés sur le web. Il est léger et permet d’échanger des données. Je propose la rédaction d’un JSON Schema pour formaliser les contenus, à partir d’un l’exemple concret de données que j’utilise déjà.

## Un JSON tout simple

Pour un site patrimonial qui liste les églises protestantes ouvertes en Suisse romande, j’ai utilisé dès le début des données formatées en JSON. Chaque bâtiment a son propre fichier, assez lisible, qui ressemble à ceci:

```
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

J’ai ajouté les champs de données au fur et à mesure de la création du site, ne sachant pas quelles informations j’allais découvrir dans mes recherches.

## Un JSON plus structuré

S’il fallait modifier quelque chose, je structurerais peut-être les données un peu plus fortement, par exemple ainsi:

```
{
    "title": "Temple de Colombier",
    "liens": {
        "site": "https://www.eren.ch/barc/batiments/temple-de-colombier/",
        "maps": "https://goo.gl/maps/3KSuvNTqXsdSFmnc9"
    },
    "adresse": {
        "rue": "Rue du Château 3a",
        "npa": 2013,
        "localite": "Colombier",
        "commune": "Milvignes",
        "canton": "Neuchâtel"   
    },
    "coordonnes": {
        "latitude": 46.9666066,
        "longitude": 6.8623137
    },
    "ouverture": {
        "jours": "7/7",
        "horaire": "8:00-20:00"
    },
    "patrimoine": {
        "pbc": "B",
        "vitraux": ["Pierre-Eugène Bouvier"]
    }
}
```

C’est très théorique, parce qu’en voyant le résultat, je ne suis pas certain que ça apporterait beaucoup. Le «JSON tout simple» est donc celui que je conserve pour produire le site et sur lequel portent les exemples qui suivant.

## Objectifs du schéma JSON

Si le [format JSON](https://www.json.org/json-fr.html) est strict du point de vue le la forme, il laisse toute liberté pour les contenus. Un [JSON Schema](https://json-schema.org/) permet de fixer des règles pour la création d’un contenu JSON.

Le schéma que je vais créer doit notamment servir à vérifier:

- qu’un certain nombre de données soient présentes (titre, adresse complète, coordonnée et horaires d’ouverture)
- qu’il soit possible de faire un lien vers une page externe ou une fiche Google Maps
- que les numéros postaux soient des nombres de 4 chiffres
- que les coordonnées aient des valeurs raisonnables pour la Suisse romande
- qu’il ne soit pas possible d’ajouter d’autres données

Ainsi je pourrai vérifier la validité de mon corpus d’édifices en une seule commande, [par exemple avec JSONSchema](https://github.com/santhosh-tekuri/jsonschema). Ou tester un contenu directement en ligne avec [JSON Schema Validator](https://www.jsonschemavalidator.net/).

## Création d’un schéma JSON

L’utilisation de JSON est complètement libre, mais un [JSON Schema](https://json-schema.org/) permet de fixer des règles et de valider des contenus informatiquement. Pour ma culture générale, j’ai créé un schéma pour *Églises ouvertes en Suisse romande*  (site abandonné).

Je le copie intégralement, même si c’est un peu long. Puis je commente certaines parties dans la suite du billet. La version courante était disponible sur le site eglises-ouvertes.ch. Elle reste disponible dans de le [dépôt GitHub nfriedli/eglises-ouvertes](https://github.com/nfriedli/eglises-ouvertes/blob/main/static/schema.json).

```
{
    "$schema": "https://json-schema.org/draft/2020-12/schema",
    "$id": "https://eglises-ouvertes.ch/schema.json",
    "title": "église ouverte",
    "description": "description complète d’une des Églises ouvertes de Suisse romande",
    "type": "object",
    "properties": {
        "title": {
            "description": "nom du bâtiment",
            "type": "string"
        },
        "nomCourt": {
            "description": "version simplifiée du nom du bâtiment",
            "type": "string"
        },
        "site": {
            "description": "page de présentation du bâtiment (horaire d’ouverture impératif)",
            "type": "string"
        },
        "maps": {
            "description": "fiche Google Mas du bâtiment (horaire d’ouverture impératif)",
            "type": "string"
        },
        "rue": {
            "description": "rue avec numéro",
            "type": "string"
        },
        "localite": {
            "description": "village dans une plus grande commune",
            "type": "string"
        },
        "commune": {
            "type": "string"
        },
        "npa": {
            "description": "numéro postal d’acheminement",
            "type": "integer",
            "minimum": 1000,
            "maximum": 9999
        },
        "canton": {
            "description": "un canton de Suisse romande",
            "enum": ["Berne", "Fribourg", "Genève", "Jura", "Neuchâtel", "Valais", "Vaud" ]
        },
        "latitude": {
            "type": "number",
            "minimum": 45,
            "maximum": 48
        },
        "longitude": {
            "type": "number",
            "minimum": 5,
            "maximum": 11
        },
        "ouverture": {
            "description": "jours d’ouverture (souvent 7/7)",
            "type": "string"
        },
        "horaire": {
            "description": "heures d’ouverture (parfois 24/24)",
            "type": "string"
        },
        "pbc": {
            "description": "patrimoine des biens culturels suisses",
            "enum": [ "A", "B" ]
        },
        "vitraux": {
            "description": "nom d’artiste",
            "type": "array",
            "items": { "type": "string" }
        }
    },
    "anyOf": [
        { "required": [ "site" ]},
        { "required": [ "maps" ]}
    ],
    "required": [
        "title",
        "rue",
        "npa",
        "commune",
        "canton",
        "latitude",
        "longitude",
        "ouverture",
        "horaire"
    ],
    "additionalProperties": false
}
```

### Validation des champs

En début de fichier, ce sont des champs qui demandent des chaînes de caractères (du texte libre). Cela n’appelle pas de commentaires particuliers.

Pour le numéro postal d’acheminement, j’impose un nombre de 4 chiffres entre 1000 et 9999. On pourrait limiter aux NPA de Suisse romande, mais c’est très bien ainsi:

```
"npa": {
    "description": "numéro postal d’acheminement",
    "type": "integer",
    "minimum": 1000,
    "maximum": 9999
}
```

Pour le canton, on limite le choix aux cantons romands (ou avec une partie romande) et il ne peut y en avoir qu’un:

```
"canton": {
    "description": "un canton de Suisse romande",
    "enum": ["Berne", "Fribourg", "Genève", "Jura", "Neuchâtel", "Valais", "Vaud" ]
},
```

La latitude et la longitude sont limitées dans des valeurs proches de celles de la Suisse:

```
"latitude": {
    "type": "number",
    "minimum": 45,
    "maximum": 48
},
"longitude": {
    "type": "number",
    "minimum": 5,
    "maximum": 11
}
```

Si elle est précisée, l’inscription à l’[Inventaire des biens culturels d’importance nationale et régionale (PBC)](https://www.bak.admin.ch/bak/fr/home/baukultur/archaeologie-und-denkmalpflege/inventare/kgs-inventar.html) peut prendre la valeur *A* ou la valeur *B*:

```
"pbc": {
    "description": "patrimoine des biens culturels suisses",
    "enum": [ "A", "B" ]
}
```

Les artistes ayant créé des vitraux peuvent être plusieurs pour un seul édifice:

```
"vitraux": {
    "description": "nom d’artiste",
    "type": "array",
    "items": { "type": "string" }
}
```

### Conditions de validation

Au-delà de la validation champ par champ, des conditions plus globales sont déclarées.

En premier lieu, certaines données sont nécessaires et il faut s’assurer de leur existence:

```
"required": [
    "title",
    "rue",
    "npa",
    "commune",
    "canton",
    "latitude",
    "longitude",
    "ouverture",
    "horaire"
]
```

Beaucoup plus intéressant, l’obligation de la présence d’un site cible ou d’une fiche Google Maps (ou les deux):

```
"anyOf": [
    { "required": [ "site" ]},
    { "required": [ "maps" ]}
]
```

Finalement, l’interdiction d’ajouter des champs autres que ceux déclarés dans le schéma:

```
"additionalProperties": false
```

## Assurances formelles et validité des contenus

C’était mon premier essai de rédaction d’un schéma JSON. J’ai trouvé l’exercice plutôt intéressant. C’est toujours amusant de lire une référence technique sur un écran et d’écrire le fichier de code sur l’autre.

Il faudrait aller un peu plus loin pour certaines données, par exemple avec des [expressions régulières](https://json-schema.org/understanding-json-schema/reference/regular_expressions#regular-expressions) pour valider des plages horaires. Mais je m’arrête là pour le moment.

L’enjeu bien réel derrière cet exercice, c’est que la validité formelle ne dit rien de la validité réelle des contenus. Elle assure la présence de contenus, non leur justesse. Il y a quelque chose de paradoxal à formaliser des données alors que les informations n’existent souvent pas en ligne.

Le rachitisme du défunt *Églises ouvertes en Suisse romande* est une conséquence directe de la paresse de celles et ceux qui pourraient publier des contenus utiles. Mais pas une question de format de données.
