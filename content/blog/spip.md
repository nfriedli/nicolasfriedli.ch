---
title: Notes sur SPIP en 2025
description: SPIP reste une merveilleuse «machine à publier». Il a perdu de sa popularité, il intéresse moins que d’autres CMS, il n’est pas commercial, mais son projet militant dure depuis 2001.
date: 2025-02-17
lastMod: 2025-03-31
---

SPIP est un magnifique système de publication né en 2001.
Il a eu ses heures de gloire dans le monde francophone (et ailleurs).
Il n’est plus aussi populaire mais qu’importe.

Pour des tests sur [theologique.ch](https://theologique.ch/), j’ai réinstallé un SPIP tout frais.
Même s’il est peu probable que je conserve ce site sous SPIP, je vous explique pourquoi il reste génial en 2025.
**Le projet a été modifié et je ferai un site en [langage simplifié]({{% relref "falc-plain-ia" %}}) avec Hugo.**

En fin de billet, je vous donnerai aussi quelques «problèmes» qui m’empêchent de l’utiliser plus souvent.

## Amélioration progressive

J’apprécie particulièrement la gestion très progressive des champs activables.
SPIP a été conçu pour la publication éditoriale et ça se ressent.
Au départ, un article, c’est un titre et un corps de texte.

Selon la demande, je peux activer, seulement quand c’est nécessaire:

- un sur-titre
- un sous-titre
- un descriptif (ou résumé)
- un chapo (ou introduction)
- un post-scriptum

Immense avantage de cette progressivité, rien d’inutile n’est affiché dans l’interface d’administration.
Elle reste simple et légère.
Elle se complexifie en fonction des nécessités avec le temps.

## Attribution des auteurs

Alors que beaucoup de systèmes de gestion de contenu (CMS) ont exactement un auteur ou une autrice par article, SPIP est beaucoup plus souple.
Pour rappel, chez WordPress, c’est une personne pour les articles et pas de signature pour les pages.

Pour chaque page, il permet d’attribuer zéro, un ou plusieurs auteurs et autrices.
Une fois qu’une personne se voit listée, elle devient responsable de la page et peut la modifier.
Cela ouvre de belles perspectives pour un travail collaboratif.

## Syntaxe de rédaction et gestion typographique

De son origine dans le monde de la presse, SPIP a gardé l’excellence de sa gestion typographique.
Chaque page est rédigée avec une syntaxe particulière, en pur texte.

Ainsi, on évite les ~~délires~~ variations de mises en pages.
Les copier-coller ne produisent pas les horreurs possibles avec les systèmes visuels WYSIWYG (What you see is what you get).
La logique de SPIP, c’est WYMISYG (What you mean is what you get): ce que vous voyez, c’est ce qui est conforme à votre pensée.

Les corrections typographiques permettent de ne pas se soucier des choix des personnes en charge de la rédaction.
Il y a toujours une espace insécable avec les deux-points, les points-virgules, etc.
Ici, je n’utilise pas d’espacement autour des ponctuations, mais je ne peux pas être certain qu’une autre personne le respectera.
Avec SPIP, tout est uniformisé de force.

## Gestion des URL et maillage interne

C’est une des raisons pour lesquelles j’ai installé SPIP sur theologique.ch.
J’ai activé les URL libres.
Ce qui signifie que je peux choisir la chaîne de caractère de l’adresse de la page, toujours en minuscule et à la racine.

Si je déplace une page dans la hiérarchie, l’adresse ne change pas.
Ainsi, je peux construire une structure au fil du temps, en conservant les adresses.

Mieux, comme les liens se font par raccourcis, du genre `[->art1]`, le titre et le lien seront toujours corrects.
Même quand le titre change, même quand l’emplacement dans le site change.

Et si je décide de changer une URL, l’ancienne adresse reste valide, avec une redirection propre de type 301.

## Notion de popularité

SPIP mesure la [popularité des publications](https://www.spip.net/fr_article1846.html).
Ce qui permet de classer les articles par ordre décroissant de visites à un moment donné.

J’ai bien envie de construire, une fois, un site dont les classement seraient dynamiques, en favorisant le plus lu.
C’est bien entendu peu imaginable avec un site statique (à moins de s’adosser à une plateforme de déploiement).
C’est une bonne raison d’installer SPIP.

Évidemment, ce genre de choix est discutable.
Mais le tester «en vrai» sur un site personnel m’intéresse.

## Gestion des mots clés

Au départ, pas de mots-clés activés.
L’interface reste minimale, comme déjà dit.

Mais quand j’ai besoin de taxonomies, je peux activer les mots-clés.
Puis créer de groupes et des mots.

La gestion avancée permet des choses intéressantes comme:

- l’attribution par les personnes en charge de l’administration seulement (et non les rédacteurs et rédactrices)
- l’incitation à choisir au moins un mot-clé d’un group
- l’interdiction de choisir plus d’un mot-clé d’un groupe

C’est à la fois très simple et très malin.

## Installation et optimisation

Dès son installation, SPIP propose tout le nécessaire (batteries included).
Et l’installation, avec un base SQLite, et la configuration prennent à peine quelques minutes
Pas besoin de se surcharger le tout de plugins et extensions pour avoir un «vrai» site.

L’optimisation est présente par défaut:

- concaténation et minimisation des CSS
- concaténation et minimisation du JavaScript
- système de cache pour un site rapide et fiable

Les statistiques internes sont déjà présente, la gestion des images aussi.
Tout est beau dans le meilleur des monde.
Mais...

## Les «problèmes» de SPIP

Il n’est pas possible d’installer des thèmes comme avec WordPress.
Ni de les configurer aussi simplement; SPIP n’est pas un cliquodrome.
Son thème par défaut est un peu daté (mais très efficace).
Et ce CMS ne dispose pas de tout l’écosystème de WordPress.

La syntaxe n’est pas Markdown, aujourd’hui la plus utilisée.
Normal, elle est née avant!
Mais elle peut dérouter et déplaire.
Beaucoup de personnes restent réticentes au balisage léger.
Elles préfèrent le «à la Word», même s’il est moins efficace dans la durée.

La documentation est médiocre.
Certaines parties sont bonnes, mais elle contient un nombre impressionnant de vieilleries et de scories.
Elle ne peut pas inspirer pas confiance à une personne qui découvre SPIP.

SPIP n’est pas produit pas une fondation ou une grande entreprise.
Pour beaucoup, c’est problématique.
Ce CMS est géré par des personnes, sans réel·le propriétaire.
Quand on voit les conflits de gouvernance chez WordPress actuellement, on se dit que c’est peut-être une bonne idée...

Finalement, SPIP n’a pas de marketing, pas de modèle économique, pas de vrai calendrier.
Celles et ceux qui le créent sont idéalistes, libertaires, libristes, etc.
La nouvelle version arrive «quand elle est prête».
Beaucoup d’entreprises et d’organisations refusent de se fier à un tel fonctionnement (qui dure pourtant depuis très longtemps).

----

Une personne qui [lance un blog en 2025]({{% relref "blog-2025" %}}) et qui ne souhaite pas un site statique devrait peut-être s’intéresser à SPIP.
