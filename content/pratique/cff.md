---
title: Citations facilitées avec le fichier CITATION.cff
description: Comment citer correctement un site web? Comment donner la référence précise d’un logiciel? Le fichier CITATION.cff permet de transmettre des données claires et utiles. 
aliases:
- /pratique/cff/
---

Comment citer correctement un site web?
Comment donner la référence précise d’un logiciel?
Le fichier `CITATION.cff` permet de transmettre des données claires et utiles.

## Fichier `CITATION.cff` pour nicolasfriedli.ch

J’ai généré un fichier `CITATION.cff` en utilisant le site [CFFINIT](https://citation-file-format.github.io/cff-initializer-javascript/#/).
Pour le site sur lequel vous vous trouvez, cela donne (la [version courante](https://github.com/nfriedli/nicolasfriedli.ch/blob/main/CITATION.cff) est disponible dans GitHub):

```
cff-version: 1.2.0
title: Site personnel de Nicolas Friedli
message: >-
  Proposition de citation:
  Nicolas Friedli, site personnel, https://nicolasfriedli.ch, consulté le...
type: dataset
authors:
  - given-names: Nicolas
    family-names: Friedli
    email: hello@nicolasfriedli.ch
identifiers:
  - type: url
    value: "https://nicolasfriedli.ch"
    description: Site personnel
repository-code: "https://github.com/nfriedli/nicolasfriedli.ch"
url: "https://nicolasfriedli.ch/"
license: CC-BY-SA-4.0
```

Ce fichier est lisible, même si sa rédaction manuelle peut être fastidieuse.
C’est un fichier structuré en `YAML`.
Le format complet est document sur le site [Citation File Format (CFF)](https://citation-file-format.github.io/).

Mais en première approche, je conseille de **favoriser le générateur CFFINT**.
Évitez à tous prix les outils comme ChatGPT qui ajoutent des champs délirants (j’ai testé avant de l’affirmer)!

## `CITATION.cff` dans GitHub

Le site GitHub utilise les fichiers de citation quand ils sont placés à la racine du dépôt.
Par exemple, le dépôt <https://github.com/nfriedli/nicolasfriedli.ch> affiche (colonne de droite sur grand écran): *Cite this repository*.

À partir du fichier source, il donne un accès direct:

- au format [APA](https://fr.wikipedia.org/wiki/Style_APA) (American Psychological Association)
- au format [BibTeX](https://fr.wikipedia.org/wiki/BibTeX)
- et au fichier source

Des outils comme [Zotero](https://www.zotero.org/) proposent des moyens d’utiliser directement un tel fichier.

## Citation de nicolasfriedli.ch en texte simple

Bien entendu, vous pouvez continuer à citer une source sans recours à un logiciel spécifique.
Lorsque vous renvoyez à une page de ce site, vous pouvez proposer un **lien visible** dans un document imprimé, par exemple:

> «Faciliter les citations avec le fichier CITATION.cff» (<https://nicolasfriedli.ch/pratique/cff/>), consulté le 27 octobre 2025

Sur une page web, un **lien cliquable** classique suffit, par exemple:

> [Faciliter les citations avec le fichier CITATION.cff](<https://nicolasfriedli.ch/pratique/cff/>) (27.10.2025)

Et si vous souhaitez une **citation complète**, je vous suggère un format de type:

> Nicolas Friedli, site personnel, <https://nicolasfriedli.ch>, licence Creative Commons BY-SA, consulté le 27.10.2025.

## Citer une page ou un nom de domaine

Pour les liens dans les pages web, je pense qu’il vaut toujours la peine de favoriser les **URL directes** vers les pages citées.
Il est assez facile de vérifier ses liens régulièrement et d’apporter des modifications si nécessaire.

Pour les impressions et les utilisations dans des travaux de longue durée, je suis plus réservé.
Je pense que le **nom de domaine** suffit.
Il permet, en cas de besoin, de retrouver le contenu quelque part.
En particulier si vous ne disposez pas d’un logiciel pour faire un travail d’archivage efficace.

De manière générale, quand des pages sont citées, je conseille de toujours **les faire entrer dans la Wayback Machine**.
J’en dis quelques mots dans [Disparition d’une page ou d’un site web](/pratique/disparition/).

À ma connaissance, les fichiers `CITATION.cff` restent rare des projets «littéraires» et je pense que cela mériterait de changer.
