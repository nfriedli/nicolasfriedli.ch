---
title: Logique cumulative ou qualitative
description: Un blog est une «machine à ajouter du contenu» alors que qu’un site hiérarchique est un outil pour «maintenir du contenu à jour». Quels sont les enjeux pour ce site?
date: 2024-11-21
categories:
- documentation
draft: true
---

Ce site est construit selon une logique de blog: **j’accumule du contenu**.
Chaque nouvelle publication est ajoutée dans la même rubrique.
Il existe quelques taxonomies qui permettent de lier les pages entre elles par thématiques.

Mais je m’interroge et hésite à créer un site hiérarchique.
Avec une idée derrière la tête: **maintenir à jour un corpus** de taille raisonnable.

## Le modèle cumulatif

Les **sites cumulatifs** par excellence sont les blogs et les sites d’actualités.
L’intervention principale sur le site est l’ajout d’une nouvelle page.
Et parfois l’ajout «à la volée» de nouvelles taxonomies.

Si je qualifie ce modèle de «cumulatif», cela ne dit rien de la qualité des contenus publiés.
Mais plutôt l’idée qu’**une page en ligne est rarement modifiée**.

Le blog est efficace et pertinent pour mettre en ligne des contenus «terminés».
Il n’y a pas de raison de les revoir à l’avenir, parce qu’ils ont été délivrés tels quels.
Bien entendu, la correction de coquilles ou de liens est toujours possible.

À mes yeux, le risque principal de ce type de publication est la cannibalisation des contenus.
Je me vois mal publier 10 pages sur l’[optimisation des polices d’écriture]({{% relref "police-optimisee-titres" %}}) au fil du temps.
Si 9 billets sont dépassés, à quoi bon les conserver.

Le message que donne un blog, c’est:

> Vous trouvez ici du contenu «dans son jus», tel qu’il a existé à un moment, et c’est ce qui fait sa saveur.
> Il n’est peut-être plus pertinent, mais ce n’est pas la question.
> Servez-vous si cela vous intéresse.

## Le modèle qualitatif

Les **sites qualitatifs** sont avant tout des documentations et des wiki.
Les interventions sont souvent des corrections et améliorations de pages existantes.

Généralement, les wiki ne contiennent pas de taxonomies.
Et l’ajout de catégories dans les sites hiérarchiques (en arbre) est non trivial.

Si je qualifie ce modèle de «qualitatif», cela ne signifie pas que chaque contenu sera de qualité.
Mais plutôt que **la qualité d’un contenu donné sera améliorée au fil du temps**.

Lorsque je documente du code, je constate que la logique du blog n’est pas toujours la bonne.
Les outils changent et il y a un grand risque de garder en ligne des extraits caducs ou dépassés.

Je préfère avoir 1 billet sur un sujet et le corriger quand nécessaire.

Le message que donne un site qualitatif:

> Vous trouvez ici un contenu utilisable aujourd’hui.
> Son histoire n’est pas (immédiatement) visible.
> Mais ce qui compte, c’est sa pertinence actuelle.

## Éviter les absolus

Bien évidemment, aucun de ces modèles n’est parfait.
Certains billets de blog sont corrigés, maintenus, réactualisés, parfois avec une republication ou une redirection.

Alors que le modèle hiérarchique n’empêche en rien l’ajoute régulier de contenus.
Et il n’est pas certain que tous les articles seront parfaitement à jour.

La question que je me pose, c’est celle de l’**orientation fondamentale** de mon site ou de sa **ligne de conduite**.

Mon billet sur les [pages sœurs, filles et mère]({{% relref "hugo-pages-soeurs-filles" %}}), utilisées dans d’autres contextes, me titille.
J’aimerais bien réussir à proposer des navigations contextuelles plus intéressantes que les seuls «articles en relation» de bas de page.

## Avantages et désavantages techniques

Techniquement, le modèle qualitatif me paraît offrir quelques avantages:

- la possibilité de disposer d’un fil d’Ariane ou *breadcrumb* qui permet de **se situer sur le site**
- l’utilisation d’**URL hiérarchiques** est intéressante pour l’étude des données statistiques
- la structuration de «secteurs» permet d’envisager simplement des **mises en pages différenciées**
- la **croissance organique du site** est une manière de faire que j’apprécie

Mais ce modèle hiérarchique, en arbre, a aussi des limitations:

- **une page fait partie d’une seule rubrique**, ce qui demande pas mal de réflexions du point de vue de l’architecture d’information
- **l’utilisation des taxonomies est relativisée**, alors que c’est un mode de pensée qui me convient
- l’automatisation des navigations fait toujours courir le risque de proposer **moins de liens dans le corps du texte** (pour éviter les doublets)

----

Je reçois volontiers vos retours et conseils par *webmention* ou par mail.
Ou, mieux encore, dans un billet ajouté à votre propre blog.
