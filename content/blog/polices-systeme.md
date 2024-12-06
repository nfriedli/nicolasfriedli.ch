---
title: Utiliser des polices système
description: Les polices dites «web safe» n’existent plus vraiment aujourd’hui, mais des directives CSS comme system-ui et des listes de polices adaptées permettent de conserver un web écologique et rapide.
date: 2024-04-22
lastMod: 2024-10-25
categories:
- a11y
- performance
---

L’utilisation de polices du système d’exploitation (*system font stack*) permet une cohérence graphique sans téléchargements.
Mais la diversité des plateformes rend le travail relativement complexe.

## Problématique

Dans son billet [Are Web-Safe Fonts still relevant in 2024?](https://pimpmytype.com/web-safe-fonts/), Oliver Schöndorfer se demande si l’utilisation de polices système universelles est toujours pertinente aujourd’hui.
Sa question est bonne, parce que les systèmes d’exploitation sont nombreux.
Toutefois, sa réponse est imparfaite.

Il part du fait qu’il n’existe plus de polices présentes sur tous les périphériques.
Arial et Times New Roman avaient une disponibilité de virtuellement 100%, ce n’est plus vrai pour le système Android.

Les questions suivantes devraient toujours être posées:

- Est-ce qu’*une police précise* est nécessaire pour ce site web?  
- Est-ce qu’un *choix de polices proches* est suffisant?
- Faut-il laisser le *choix de la police au système d’exploitation*?
- Faut-il laisser le *choix de la police aux internautes*?
- Est-ce que les enjeux d’*écologie* et de *performance* permettent de télécharger plusieurs fichiers?

## Nécessité d’une police précise (*corporate identity*)

Quand une police doit être utilisée, il n’y a pas d’autre choix que de demander au navigateur de la télécharger.
En pratique, ce sont plusieurs fichiers qui vont être envoyés, en général:

- une police «normale»
- une police grasse
- une police italique
- une police grasse italique

Les fichiers seront mis à disposition par une directive CSS `@font-face` et ceux qui sont nécessaires seront téléchargés.
Lorsque ce cas se présente, il fait veilleur à une optimisation des fichiers et des chargements:

- bon format de fichier (`woff2`)
- blocage ou non de l’affichage (`font-display`)
- préchargement (`preload`)
- suppression des jeux de caractères inutiles
- une gestion du cache pertinente (`immutable`)
- utilisation de polices variables si disponibles

En général, il devrait être possible de s’en tirer autour de 100kB pour un jeu de police complet.
Pour en savoir plus sur cette thématique complexe, le billet [A Comprehensive Guide to Font Loading Strategies](https://www.zachleat.com/web/comprehensive-webfonts/) de Zach Leatherman est un point de départ précieux.

Quand ce chargement permet de répondre à une contrainte précise, c’est très bien.
Mais je reste surpris par le nombre de sites qui téléchargent de tas de fichiers qui sont sans rapport avec la charte graphique de l’entreprise ou l’institution.
Dans ces cas là, il y aurait peut-être mieux à faire.

## Choix de polices (*system font stack*)

Une *font stack* est une liste de polices possibles.
Autrement dit, le site *suggère* des polices au navigateur; il choisit la première de la liste disponible localement et l’affiche.

Le site [Modern Font Stacks](https://modernfontstacks.com/) propose des «piles de polices» toutes faites qui fonctionnent bien partout.
Par exemple:

```
font-family:  Inter, 
              Roboto, 
              "Helvetica Neue", 
              "Arial Nova", 
              "Nimbus Sans", 
              Arial, 
              sans-serif;
```

Ce qui se passe:

- Inter s’affiche si elle a été installée par l’internaute.
- ~~Sinon Roboto s’affiche sur Android (où elle est toujours disponible).
Ou ailleurs si elle a été installée.~~ En fait, Roboto s’affiche sur Android par `sans-serif` (dernier point ci-dessous).
- Sinon Helvetica Neue s’affiche sur Apple (où elle est toujours disponible).
Ou ailleurs si elle a été installée.
- ...
- Sinon Arial s’affiche sur Windows (où elle est toujours disponible).
Ou presque partout ailleurs.
- Finalement, si aucune n’est disponible, c’est la police de substitution, choisie par le navigateur ou l’internaute qui apparaît.

Franchement, il me parait acceptable d’afficher une des polices sans empattement présentes, que les internautes connaissent.
Dans tel cas, il n’y a aucune bande passante utilisée et aucune latence.
Pour tous les textes courants, c’est un excellent choix.

## Polices universelles (*web safe fonts*)

Comme Oliver Schöndorfer le signale, Arial et Times New Roman ne sont plus disponibles partout.
Mais il est facile de contourner le problème.
Si l’idée est d’obtenir simplement une police banale sans empattement, la directive CSS suivante suffit:

```
font-family: sans-serif;
```

Et avec empattement:

```
font-family: serif;
```

Cela va peut-être manquer un peu d’originalité, mais c’est léger.
Si les internautes n’ont pas configuré leur navigateur n’importe comment, ce sera très lisible.
J’estime que c’est toujours une bonne solution.

Les *polices universelles* aujourd’hui ne sont plus identifiables par un nom précis; ce sont simplement les écritures par défaut du système d’exploitation.

## La police d’interface (*system-ui*)

Depuis quelque temps, il est possible d’utiliser une police spéciale.
C’est celle du système d’exploitation.
Elle ne peut pas être modifiée dans le navigateur par les internautes, contrairement aux précédentes.
C’est tout simple:

```
font-family: system-ui, sans-serif;
```

La directive `sans-serif` reste à disposition si le navigateur -- cas très rare -- ne comprenait pas la directive `system-ui`.
Avec une police système, c’est une écriture parfaitement en phase avec le système utilisé qui sera choisie.
C’est celle de l’interface, d’où UI (*user interface*).

Au final, l’apparence laisse encore moins d’originalité que `sans-serif`, mais ce sont souvent des polices de grande qualité qui sont utilisées.
Le résultat est excellent.

## Périphériques Apple

Les périphériques Apple ont la particularité d’utiliser des directives spéciales comme la police UI.
Sur les systèmes récents, c’est l’excellente police San Francisco qui sera choisie.
Elle est élégante et dispose d’une large gamme de graisses et des tailles optiques.
Franchement, il n’y a pas à hésiter à utiliser:

``` 
font-family: ui-sans-serif, sans-serif;
```

La même logique existe pour les autres types de polices.
Donc, pour des périphériques Apple:

```
html {
  font-family: ui-sans-serif, sans-serif;
}

blockquote, h1, h2, h3 {
  font-family: ui-serif, serif;
}

code, pre {
  font-family: ui-monospace, monospace;
}
```

Tout le texte est sans empattement, sauf les citations et les titres avec empattement et le code en chasse fixe.

## Périphériques Android et Linux

Pour Android, Roboto est toujours disponible.

Elle s’affiche par les directives `system-ui` ou `sans-serif`, mais pas par `Roboto`! 
Pour Linux, Roboto est presque toujours disponible et Noto Sans aussi.

Donc, pour le corps du texte:

```
html {
  font-family: system-ui, sans-serif;
}

Et pour les citations et intertitres:

blockquote, h1, h2, h3 {
  font-family: "Noto Serif", serif;
}

Et pour le code:

code, pre {
  font-family: "Noto Sans Mono", "Roboto Mono", monospace;
}
```

Attention, avec Linux, il est possible de modifier `system-ui`, ce qui ne donne aucune certitude quant à la police choisie.
Mais on peut supposer que les internautes utilisent des fontes lisibles sur leur système.

## Périphériques Windows

Pour Windows, c’est un peu plus complexe, car différentes versions, avec des polices différentes, cohabitent.
Mais il serait possible d’utiliser des polices «universelles», par exemple:

```
html {
  font-family: Arial, sans-serif;
}

blockquote, h1, h2, h3 {
  font-family: Georgia, "Times New Roman", serif;
}

code, pre {
  font-family: Consolas, monospace;
}
```

Mon souci avec Windows, c’est que je n’aime pas Segoe UI pour les titres.
Et c’est la police `system-ui` pour certaines versions du système.
Mais Segoe UI est meilleure qu’Arial pour le texte.
J’essaie de tirer cela au clair dans ma proposition.

## Proposition

Évidemment, il faut que la feuille de style CSS fonctionne pour tous les systèmes.
En haut de la pile, il est possible d’ajouter des polices que je souhaiteras voir afficher.
Je pourrais utiliser, pour un site comme le mien, quelque chose comme:

```
html {
  font-family:  "Fira Sans",
                "Public Sans", 
                ui-sans-serif, 
                Inter,
                Roboto, 
                system-ui, 
                sans-serif;
}

code, pre {
  font-family:  "JetBrains Mono",
                "Hack",
                ui-monospace, 
                "Roboto Mono", 
                Menlo, 
                Consolas, 
                monospace;
}
```

La logique est:

- les premières lignes suggèrent des polices
- puis une directive règle le cas pour tous les périphériques Apple
- puis des propositions pour la majorité des Linux
- puis on laisse le système se débrouiller

En adoptant une telle démarche, on prend une posture de *suggestion de présentation*. J’en parle dans [Lire et relire les classiques du web
]({{% relref "lire-classiques-web#sur-le-design-web" %}})

## En conclusion

Il existe aujourd’hui d’autres manières de concilier écologie, esthétique et performance qu’en utilisant des polices dites «web safe» comme Arial et Times New Roman.
Entre les polices système (`sans-serif`, etc.), les nouvelles directives (comme `system-ui`), je pense qu’il n’est vraiment pas nécessaire d’envoyer systématiquement des fichiers à chaque internaute.

Sur ce site, j’utilise désormais:

```
html {
    font-family: ui-sans-serif, Roboto, system-ui, sans-serif;
}

code,
pre {
    font-family: ui-monospace, "Roboto Mono", "JetBrains Mono", Hack, Menlo, Consolas, monospace;

}
```
Les déclarations exactes de ma feuille de style sont toujours disponibles chez GitHub dans le fichier [`fonts.css`](https://github.com/nfriedli/nicolasfriedli.ch/blob/main/assets/css/fonts.css).

----

J’attends avec impatience l’arrivée de la directive [`prefers-reduced-data`](https://developer.mozilla.org/en-US/docs/Web/CSS/@media/prefers-reduced-data) qui permettra(it) de gérer les choses beaucoup plus simplement.

----

À ma connaissance, la police la plus légère actuellement disponible est [Geist](https://vercel.com/font).
Un seul fichier permet de remplacer les 4 variations dont je parlais ci-dessus.
Une fois passée par [Glyphhanger](https://github.com/zachleat/glyphhanger), elle pèse environ 20 kB.
Toutefois, la version elle ne dispose pas d’un vrai italique, mais d’une version oblique.

----

**Ajout du 30 avril 2024.** Les polices système (San Franciso, Segoe UI et Roboto) sont excellentes pour les personnes dyslexiques.
Elles sont bien meilleures que plusieurs polices prétendument optimisées.
Je vous conseille vivement la lecture et le visionnage de [Dyslexia friendly fonts: Are they any good?](https://pimpmytype.com/dyslexia-fonts/).
