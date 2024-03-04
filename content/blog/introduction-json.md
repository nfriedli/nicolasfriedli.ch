---
title: Introduction à JSON
description: Le format de données JSON permet de structurer très simplement des données. Il est léger et facile à utiliser dans des programmes informatiques. Et ailleurs.
date: 2024-02-15
draft: true
---


## Un exemple pratique

Voici l’adresse d’un personne fictive:

```
Pierre Robert Michaud
Appartement 666
Rue de l’Esplanade 3
1234 Trifoullis-les-Oies (BE)
```

Je parie que sa lecture vous parait assez simple. Vous comprenez facilement que où se trouve le nom de la personne, son domicile, sa localité, etc. Mais quel est son prénom (Pierre Robert ou Pierre)? Quel est son nom de famille (Michaud ou Robert Michaud)? C’est moins évident.

Vous utilisez peut-être des publipostages. Vous savez que passer d’un fichier Excel à des adresses autocollantes est facile. Mais ce serait beaucoup plus compliqué si je vous donnais 100 adresses dans un fichier Word et que je vous demandais de reconstituer un tableau. Difficile par exemple de savoir de manière automatique à quoi correspond la ligne 2.

Avec le format JSON, il est facile d’avoir des données fiables. Dans notre exemple, un peu plus étoffé:

```
{
    "destinataire: {
        "titre": "Monsieur",
        "nom": "Michaud",
        "prenom": "Pierre Robert"
    }
    "adresse": {
        "rue": "Rue de l’Esplanade",
        "numero": "3",
        "complement": "Appartement 666",
        "npa: "1234",
        "localite": "Trifoullis-les-Oies",
        "canton": "BE",
        "pays": "Suisse"
    }
}
```

Les données sont structurées, avec des clés, ce qui signifie qu’il est facile de lister toutes les personnes d’une canton, d’un pays, etc. Ou de trier la liste par nom de famille. Comme dans un tableur.

Alors pourquoi utiliser JSON? Nombre de colonne connu.

Mais dans le cas d’un CV, par exemple...

## Légerté du format

## Javascript natif

## Modéliser une base de données
