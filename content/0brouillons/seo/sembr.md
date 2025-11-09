+++
title = "Sauts de ligne sémantiques"
description = "L’utilisation d’une convention de rédaction du code source facilite la collaboration et aide à gagner du temps et de l’énergie. Même quand le résultat final est absolument identique."
date = 2025-09-23
+++

J’en ai parlé dans des billets précédents, je travaille avec des langages de balisage léger qui distinguent fichier source et résultat produit.
J’utilise [Markdown](/blog/markdown/) pour produire les pages HTML de ce site.

Je vous conseille de jeter un œil à la [source de cette page dans GitHub](https://github.com/nfriedli/theologique.ch/blob/main/content/blog/sembr.md).
Pour voir le résultat en HTML, vous pouvez consulter le document envoyé dans votre navigateur avec `Ctrl U`.

## Exemple de sources

Je prends pour exemple le texte suivant:

> Voici un exemple de texte en Markdown.
Cette syntaxe ne tient pas compte des sauts de ligne ni des espaces multiples.
Ce qui fait que de fichiers différents peuvent présenter un sortie identique.
C’est ce que j’illustre sur cette page.

Les trois sources suivantes produiront le même résultat de sortie:

Tout le texte «au kilomètre», c’est mon éditeur de texte qui crée de faux sauts de ligne (*soft wrap*), comme dans un paragraphe de Word:

```markdown
Voici un exemple de texte en Markdown. Cette syntaxe ne tient pas compte des sauts de ligne. Des sources différentes présentent une sortie identique. C’est ce que j’illustre sur cette page.
```

Ou alors on peut artificiellement créer des sauts de ligne, pour avoir une colonne assez compacte:

```markdown
Voici un exemple de texte en Markdown. Cette
syntaxe ne tient pas compte des sauts de ligne.
Des sources différentes présentent une sortie
identique. C’est ce que j’illustre sur cette
page.
```

Enfin, on peut créer des sauts de lignes sémantiques, donc l’unité de sens est la phrase:

```markdown
Voici un exemple de texte en Markdown.
Cette syntaxe ne tient pas compte des sauts de ligne.
Des sources différentes présentent une sortie identique.
C’est ce que j’illustre sur cette page.

```

Comme la sortie est identique, le formatage de la source est uniquement une *convention*.
Nous pouvons nous entendre pour formatter le texte d’une certaine manière qui nous convient et que l’on partage.
C’est important pour la [collaboration](/blog/collaboration/)

## Visualisation des différences

En changeant une même phrase dans les 3 sources, je peux visualiser les différences dans GitHub ou avec un outil de `diff`.
Ce que l’on constate:

- dans le premier exemple, le logiciel considère que toute le paragraphe a été modifié (parce qu’il fonctionne par ligne) :shit:
- dans le deuxième exemple, il considère que 2 lignes ont été modifiées (alors qu’il s’agit d’une seule phrase) :thinking:
- dans le troisième exemple, il considère qu’une ligne (= une phrase) a été modifiée :smile:

Je vous propose d’observer les différences par le [commit 68a301a](https://github.com/nfriedli/theologique.ch/commit/68a301a6ffa9f8c2e0c0e465100c2cd78ac73d65) directement dans GitHub.

## Convention sémantique

Depuis longtemps, je fais des sauts de ligne en fin de phrase, parce ce que c’est ce qui produit le code source que je préfère.
Récemment, j’ai découvert qu’un site existait sur le sujet: [Semantic Line Breaks](https://sembr.org/).

Cette formalisation peut paraître artificielle aux internautes qui n’ont pas l’habitude du code.
Mais elle est très utile pour celles et ceux qui rédigent en commun et évitent de corriger le travail de leurs collègues.

Quand on utiliser un langage très courant comme Markdown, il existe même des outils qui harmonisent les sources pour coller aux conventions.
Celles et ceux qui ont une mentalité geek essaieront sans tarder quelque chose comme:

```bash
npx markdownlint-cli2 content/**/*.md --fix
```

Pour avoir édité des livres en «code» (à l’époque LaTeX) et en Word, je vous le dis en connaissance de cause.
Avec les sauts de ligne sémantique, on gagne en lisibilité, en collaboration et en facilité de maintenance d’un corpus.
