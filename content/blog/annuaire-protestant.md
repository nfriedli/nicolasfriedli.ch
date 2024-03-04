---
title: Proposer un annuaire protestant en ligne
description: Avec theologique.ch, je propose un annuaire protestant (réformé) francophone en ligne. Voici quelques raisons qui m’ont poussé à créer ce site.
date: 2024-03-04
---

Avec theologique.ch, je propose un annuaire protestant (réformé) francophone en ligne. C’est un outil et non une finalité en soi. Voici quelques raisons qui m’ont poussé à créer ce site.

## Établir un état des lieux

Il y a presque 10 ans, j’avais proposé un recensement lors des *Assises du web protesatant romand*. L’[annuaire protestant theologique.ch](https://theologique.ch/) que je propose aujourd’hui est une version plus développée de ce qui avait été fait alors.

Des discussions existent, à différents niveaux décisionnels, pour savoir quelles présences en ligne il faut envisager. **Il me paraît impensable d’imaginer des choses nouvelles, ou différentes, sans savoir ce qui existe maintenant.** L’état des lieux que constitue theologique.ch est une brique nécessaire mais insuffisante pour réfléchir aux questions de présence sur le web.

## Évaluer le web protestant francophone

Pour construire theologique.ch, j’ai parcouru tous les sites référencés (et bien d'autres). Pour chacun, j’ai navigué assez pour rédiger une description sommaire. **Ce travail m’a permis une redécouverte du web protestant réformé francophone que je connais un peu mieux qu’avant.**

Même si je n’ai pas systématiquement [testé les sites](/blog/tester-site/) consultés, quelques minutes de navigation et de lecture sur chacun d’eux me donnent un bon aperçu de leur état (contenu, menus, voire performances ou accessibilité). Cela m’est utile en tant que webmaster de certaines sites protestants, pour savoir comment ils se positionnent par rapport au panorama général.

## Trouver des sites sans moteur de recherche

Pourquoi construire un annuaire alors que les moteurs de recherche, Google en premier lieu, sont aujourd’hui si performants? À mes yeux, la réponse est évidente: je n’aurais jamais réussi à construire un annuaire dans liens sur certains sites consultés.

Quelle que soit l’efficacité des moteurs de recherche, ils ne donneront presque jamais certains sites de theologique.ch dans les résultats de recherche (SERP). Sauf, bien entendu, si l’on sait quel site ont souhaite trouver *a priori*.

**La présence de liens est un formidable moyen de rendres visibles des sites que l’on estime pertinents dans un contexte donné.** J’ai découvert ces sites sur des *pages de liens*, dans des *blogrolls*, dans des *pages de partenariats* ou dans le *corps du texte*. Toutefois, il m’en reste encore à découvrir, par vos suggestions.

## Favoriser la découverte

Sur chaque page de l’annuaire qui présente un site, il existe plusieurs actions possibles:

- le clic sur le site en question (qui s’ouvre dans une nouvelle page)
- le retour à l’accueil
- le clic sur la (ou les) catégorie(s) du site
- la consultation d’autres sites proposés

**theologique.ch rend visible d’autres propositions pertinentes, en fonction du contexte.** C'est la raison pour laquelle je n'ajoute pas de moteur de recherche sur le site pour le moment. De plus, je suis convaincu que cette mise en relation est favorable pour les moteurs de recherche.

Je signale que le lien sortant vers le site cible est toujours visible en tant qu’URL simplifiée, afin d’aider à la mémorisation des noms de domaine qui existent.

## Travailler avec Hugo

Le [générateur de sites statiques Hugo](https://gohugo.io/) motorise theologique.ch. J’avais envie de travailler avec les taxonomies et les liens de type *à voir aussi* ou *peut aussi vous intéresser*. Hugo dispose de possibilités intéressantes dans ce domaine avec [Related](https://gohugo.io/methods/pages/related/).

Chaque page qui propose un site est classée:

- dans une ou plusieurs rubriques (*tags*), toutes disponibles sur la page d’accueil
- avec un ou plusieurs précisions (*keywords*), comme le type de site ou sa localisation, pour améliorer les choix des sites en lien mais pas affichés
- avec parfois une entrée supplémentaire (*editors*), pour créer une relation forte quand un même entité ou personne édite plusieurs sites

En JSON, cela se présente ainsi:

```
{
  "title": "Cèdres Formation",
  "site": "https://cedresformation.ch/",
  "tags": ["formation","spiritualité"],
  "keywords": ["vaud"],
  "editors": ["cedres"]
}
```

Ensuite, une pondération de ces 3 taxonomies permet d’afficher une liste de suggestions, limitée à 5 sites. **Avec une telle méthode, j’espère faire émerger des propositions de mise en relations auxquelles je ne penserais pas spontanément.** Et j’espère aussi pouvoir classer beaucoup de sites sans m’égarer dans l’élaboration de menus complexes (et difficiles à maintenir).

Tous les détails sont disponibles en permanence dans les [sources sur GitHub](https://github.com/nfriedli/theologique.ch).

## Faciliter le partage de liens

Même si j’ai découvert des sites par des liens sur d’autres, le maillage du protestantisme réformé francophone reste lacunaire. Il me semble que theologique.ch est une esquisse de solution simple et efficace.

**Chaque site qui fait un lien vers la page d’accueil de theologique.ch ou n’importe quelle page de l’annuaire renforce au final l’ensemble des sites référencés.**

Je ne peux que conseiller à toutes les personnes qui administrent des sites d’ajouter un renvoi vers theologique.ch dans leur *blogroll*, leur *page de liens* ou dans un *contenu éditorial*. Mais je ne demanderai jamais de lien en retour pour ajouter un site dans l'annuaire.

## En résumé

Ce que je retire de la création de theologique.ch:

1. Mieux vaut un annuaire incomplet que pas d'annuaire du tout.
1. En recherchant des informations utiles sur des sites (pour rédiger les descriptions), j'ai appris beaucoup sur l'état du web protestant réformé francophone.
1. Les moteurs de recherche ne remplacent pas les *vrais liens*.
1. Les liens contextuels apportent plus que des listes simples «plates».
1. Hugo permet une gestion performante des taxonomies.
1. Mieux vaut des liens vers un site centralisé que pas de liens du tout.

Toutes propositions d'ajout ou d'améliorations sont bienvenues.
