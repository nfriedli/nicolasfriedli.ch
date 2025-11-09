+++
title = "Collaboration en ligne"
description = "Les fichiers textuels simples, par exemple en Markdown, permettent de collaborer de manière optimale. Avec Git, ils permettent la coopération sans coordination."
date = 2025-09-17
+++

Dans tout ce que j’écris ces temps sur le format texte, j’ai la question de la collaboration en ligne en arrière-plan.
Les formats [texte](/blog/txt/), en général, et [Markdown](/blog/markdown/), en particulier, sont favorables au travail collaboratif.
J’essaie de vous expliquer pourquoi sans entrer dans trop de détails techniques.

## Les problèmes des CMS & wikis

Quand une page mérite une modification, une correction ou un ajout, c’est une manœuvre facile dans un système de gestion de contenu (CMS) ou un wiki.
Mais cela ne va pas sans poser quelques soucis.

Avec un CMS, il faut que l’internaute dispose d’un compte ou crée un compte pour l’occasion.
Il faut ensuite gérer ce compte, lui donner les bons droits (quand c’est possible).
Dans un certain nombre de cas, un contact préalable sera nécessaire.
Cela complexifie les choses et la modification n’a souvent simplement pas lieu.

Certes, il est possible d’activer des commentaires.
On reçoit alors, parfois, des suggestions.
Mais j’estime que le bénéfice (les améliorations proposées) est faible par rapport aux coûts (gestion des spams, lourdeur du système de commentaires, etc.).

Avec un wiki, c’est souvent l’extrême inverse.
La modification est possible facilement, en tout temps, sans forcément nécessiter un compte.
Mais il faut alors gérer toutes les modifications inutiles ou franchement néfastes.
De plus, la logique du wiki n’est pas toujours bien comprise.
Sans compter que la grande majorité des internautes ne proposera rien et se contentera de déplorer la faiblesse de la page.

Clay Shirky propose un excellent passage sur les wikis dans son livre [Here Comes Everybody](https://fr.wikipedia.org/wiki/Here_Comes_Everybody).
Je signale que sous-titre du livre est *The Power of Organizing Without Organizations*; on y reviendra en fin de billet.

## Améliorer un fichier `txt`

En travaillant avec de simples fichiers textes, il est trivial de rendre les sources publiques.
Pour cette page, le [fichier source](https://github.com/nfriedli/theologique.ch/blob/main/content/blog/collaboration.md) est disponible dans GitHub en Markdown.

Pour proposer une modification, rien de plus simple.
Si vous souhaitez améliorer ce contenu, vous téléchargez le fichier, vous le modifiez dans n’importe quel éditeur de texte et vous m’envoyez le fichier final.

Je remplace l’ancien fichier et je liste toutes les modifications avec un outil qui me les surligne (`diff`).
Si tout me convient, je le garde.
Au besoin, je modifie des parties seulement.
Et je mets tout en ligne dans mon [site statique](https://nicolasfriedli.ch/blog/site-statique-generateur-hugo/).

## Travailler avec des patches

Avec des internautes un peu plus averti·e·s, je peux aussi recevoir un patch.
Vous allez charger toutes les sources, vous pouvez même compiler le site chez vous.
Puis vous créez un [patch](https://git-scm.com/docs/git-apply).

Le truc génial du patch, c’est qu’il peut porter sur un ensemble de fichiers (et pas seulement sur un seul).
Ainsi, vous pouvez modifier plein de pages, apporter des uniformisations, corriger mon orthographe, etc. et tout m’envoyer en une fois.

## Collaborer dans GitHub (ou un autre service similaire)

Les personnes les plus averties peuvent directement collaborer dans le [dépôt GitHub de ce site](https://github.com/nfriedli/theologique.ch).
Comme pour les patches, vous faites toutes les modifications utiles puis envoyez un [pull request](https://docs.github.com/fr/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests).

Toutes les modifications sont proposées dans une [branche](https://docs.github.com/fr/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-branches) propre, que je peux fusionner avec ma branche principale quand je les accepte.

Cela paraît technique, mais quand on y a goûté, on ne peut plus s’en passer.
On entre alors dans le monde coopération sans coordination, en utilisant la force de Git.
Pour comprendre de quoi il s’agit et imaginer la puissance du concept, je vous conseille de regarder [
Clay Shirky: Comment internet transformera un jour le gouvernement](https://www.youtube.com/watch?v=CEN4XNth61o).

----

J’ai expérimenté ce genre de collaboration dans le monde protestant avec [Olivier Keshavjee](https://www.theologeek.ch/) pour [Trouver ma paroisse](https://ma-paroisse.ch/).
Il a soumis 85 fichiers pour les paroisses vaudoises ([3926a4d](https://github.com/nfriedli/ma-paroisse.ch/commit/3926a4d3ecca78b1ae63c63ebfdf939eb203f5d3)) d’un coup, puis 48 pour les paroisses genevoises ([e75e9ad](https://github.com/nfriedli/ma-paroisse.ch/commit/e75e9adfab4d6d55133c57a5af2d6d16fb8dcf62)).
C’est extraordinaire d’efficacité.

---

Et, pour vous donner envie, je vous propose de [visualiser la modification](https://github.com/nfriedli/theologique.ch/commit/ba58254bf0100e1819e4fa593c37d8d4acc6f595) (`commit`) du passage en exemple ci-dessus.
