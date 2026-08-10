---
title: Une page web est bien plus que son contenu visible
description: En rédigeant dans son site web, il est plus facile de gérer le balisage sémantique et les métadonnées. Voyage du copier-coller à la rédaction en ligne, en passant par les contenus conçus pour le web.
date: 2026-08-10
---

Ce que nous voyons intuitivement d’une page web n’est qu’une petite partie de ce qu’elle contient réellement.
Un contenu est placé dans un contexte, il porte des éléments sémantiques, il est en lien avec d’autres, il se situe dans un endroit précis d’un site.

Il existe plusieurs manières de créer des pages en ligne.
Elles ne produisent pas les mêmes résultats.
J’essaie d’expliquer pourquoi.

## Mettre en ligne

Dans bien des cas, des contenus sont simplement «mis en ligne».
Souvent, ils n’étaient pas destinés à être postés sur le web.
Le site est un (bon) moyen de diffusion, mais le résultat reste basique.

Ces contenus prévus pour d’autres usages sont nombreux.
Les articles de journaux sont calibrés et pensés pour la version papier.
Des publications scientifiques finissent en longs billets de blogs.
Les [prédications](https://dianefriedli.ch/category/predication/) de Diane Friedli sont premièrement orales.

Quand le travail est basique, la nouvelle publication se limite en gros à un copier-coller de son traitement de texte.
C’est généralement visible en quelques secondes.
Le texte est peu structuré, peu sémantique, des notes de bas de page sont nombreuses, aucun lien dans le corps.

Je ne reproche rien à ce type de publications «juste mises en ligne».
Je me réjouis même d’en retrouver en errant, parce qu’elles permettent d’injecter du contenu intéressant «sur Internet».
Il faut seulement avoir conscience qu’elles ne seront que rarement des pages «puissantes» de votre site.
Mais si le contenu est vraiment bon, elles sortiront du lot quand même.

Quand le travail est mieux fait, ce contenu est adapté au web:

- le titre est modifié pour être compréhensible à lui seul
- une belle URL est choisie
- une image Open Graph est ajoutée pour améliorer le partage (pas forcément visible sur le site)
- le contenu de la page est structuré par des intertitres
- des éléments sémantiques sont ajoutés
- des liens existent

Dans mon quotidien, c’est quelque chose que je pratique très peu.
Il est rarissime que je dispose de contenus «non prévus pour le web» qui se retrouvent sur un site.
D’habitude, je rédige pour le web ou j’écris en ligne.

## Rédiger pour le web

Une spécificité sous-estimée de la rédaction web, c’est la prise en compte du contexte.
Dans un site structuré, une page a une mère, des sœurs, des filles.

Quand je commence une page, je sais très exactement où elle se situera dans la hiérarchie.
Mieux, je sais quelle fonction précise elle doit remplir, à quelle question elle doit répondre.
C’est le seul moyen d’y inclure tout le nécessaire et seulement le nécessaire pour éviter le cannibalisme (voir [Keyword and content cannibalization: how to identify and fix it](https://yoast.com/keyword-cannibalization/)).

Quand la «localisation» et la fonction de la page sont limpides, le reste est plus facile:

- rédiger un [titre explicite](https://checklists.opquast.com/fr/qualite-numerique/le-titre-de-chaque-page-permet-didentifier-son-contenu) (cohérent avec son contexte)
- proposer une [description](https://checklists.opquast.com/fr/qualite-numerique/le-code-source-de-chaque-page-contient-une-metadonnee-qui-en-decrit-le-contenu) (cohérente avec son contexte)
- prévoir un [balisage sémantique simple et fort](/blog/semantique/) (intertitres, emphases, listes, tableaux, blocs de détails)
- proposer un maillage puissant avec des liens internes et externes précis en nombre raisonnable

En travaillant ainsi, il est fréquent de modifier des pages existantes au moment de la publication d’une nouvelle.
Je peux alors ajouter des liens spécifiques vers un nouveau contenu à la place d’anciens paragraphes moins précis.
Je peux influencer ma rédaction de la nouvelle page pour insérer au mieux ces liens dans le corps du texte.
Tout cela ne se voit pas immédiatement à la lecture.
Mais c’est ce qui fait à terme la force d’une page.

Pour le reste, on est en terrain connu.
À commencer par les réponses aux questions [QQOQCCP](https://fr.wikipedia.org/wiki/QQOQCCP) (qui? quoi? où? quand? comment? combien? pourquoi?) qui parcourent l’histoire de l’Antiquité au journalisme contemporain en passant par le référencement (SEO).
Et les classiques: phrases pas trop longues, si possible actives, paragraphes de taille raisonnable, intertitres qui rythment la lecture, etc.

En pratique, je constate avec l’expérience que l’écriture en ligne rend ce travail plus efficace (et peut-être même plus simple).

## Écrire en ligne

Ce que j’entends par «écrire en ligne», c’est effectuer la recherche et la rédaction sans passer par des outils intermédiaires.
Dans WordPress, je pourrais écrire directement dans l’éditeur Gutenberg.
Avec Hugo (comme pour ce site), je rédige en Markdown.

Si je passais par Word ou un de ses concurrents, je ne pourrais pas créer de blocs de détails directement.
Je n’aurais pas les mêmes options de mise en sens disponibles (les blocs de WordPress ou les *shortcodes* de Hugo).

Dans mon contexte d’écriture avec un éditeur de code, Git et Hugo, j’adopte une philosophie [Docs as Code](https://www.writethedocs.org/guide/docs-as-code/).
Mais qu’importent vos outils.
Il me semble qu’en 2026, écrire dans un CMS (système de gestion de contenu) est adéquat.

Dans le CMS (ou mon VS Code), il est facile de traiter directement tout l’invisible.
C’est notamment là que peuvent se traiter les métadonnées, ce que personne ne fera dans son traitement de texte.
Celles dont j’ai déjà parlé (description, titre alternatif si nécessaire, Open Graph, etc.), mais aussi d’autres comme les directives d’indexation pour les robots, la saisie de mots-clés (tags), voire du texte caché (en commentaire).

En travaillant ainsi, je minimise le nombre d’outils ouverts.
Je me simplifie la vie.
Je me concentre sur le contenu.
Et surtout sur tout ce qui n’est pas visible.
