---
title: Introduction aux flux RSS et Atom
description: Quelques notes sur les flux RSS pour rappeler que ce n’est pas un outil des spécialistes.
date: 2025-12-14
lastMod: 2025-11-17
---

Les flux RSS (Really Simple Syndication) existent depuis 25 ans. Ils sont simples, efficaces et fiables, mais ils restent méconnus par beaucoup d’internautes pour qui c’est un truc de spécialistes.

Deux remarques introductives:

- prendre en main les flux RSS et constituer une première liste de sites prend un peu de temps (mais permet d’en gagner beaucoup par la suite)
- je ne ferai pas de distinction entre RSS et Atom (Atom Syndication Format) qui sont identiques à l’utilisation

## Ça sert à quoi

Pour commencer ce petit parcours, j’ai demandé à ma femme [Diane Friedli](https://dianefriedli.ch/) de me dire spontanément comment elle définirait les RSS:

> Les flux RSS, ça te permet de savoir qu’il y a des nouveautés sur les sites qui t’intéressent sans avoir besoin d’aller voir chacun d’eux.

Ma définition, un peu plus complète, mais moins limpide:

> Les flux RSS permettent de s’abonner aux nouvelles publications de sites choisis. Ils sont consultés dans un logiciel spécifique (agrégateur) qui permet de gérer ses lectures. Les nouveautés s’affichent de manière chronologique ou selon un classement personnel. C’est une méthode de consultation fiable, rapide, écologique et anonyme.

Pour répondre à la question spécifique de l’utilité:

> Les flux RSS permettent d’organiser facilement une veille personnalisée et systématique.

## Comment ça se présente (pratique)

Voici ce qui se passe quand je me connecte à mon agrégateur de flux:

- je vois la liste des nouvelles publications depuis ma dernière connexion
- l’instant, j’ai 47 nouvelles publications issues des 340 sites j’ai décidé de suivre
- ces nouveautés sont réparties dans des rubriques (selon ma propre organisation):
  - 4 billets publiés sur des blogs protestants
  - 2 dans ma rubrique culture
  - 2 dans ma rubrique web en français
  - 6 dans ma rubrique consacrée aux médias
  - etc.
- je vais les consulter soit de manière globale, soit par rubrique:
  - je vais parcourir les 32 publications de ma rubrique web en anglais
  - puis les 15 restantes de manière antéchronologique
- quand un article m’intéresse, mais que je n’ai pas le temps de le lire, je vais le stocker dans «Lire plus tard»
- à la fin de ma visite, j’aurai en principe tout lu (sauf les publications à lire plus tard)
- parfois, je ne fais que survoler des articles (mais je sais de quoi ils parlent et ça me suffit)
- j’ai aussi la possibilité de laisser des articles non lus pour ma prochaine visite (comme dans une boîte mail)

Autrement dit, ce matin, c’est comme si j’avais parcouru 340 sites pour chercher les (éventuelles) nouvelles publications. Puis que je les avais classées par catégories, puis que je les avais survolées (ou lues). Enfin que j’avais enregistrées celles que je souhaitais conserver pour plus tard en un lieu accessible de tous mes périphériques (ordinateur, téléphone ou tablette).

Franchement, nous avons mieux à faire que parcourir des centaines de sites, dont beaucoup n’ont pas de nouveautés depuis hier ou la semaine dernière. Les logiciels font ça mieux que nous.

## Comment ça fonctionne (technique)

Les flux RSS sont des fichiers qui ne sont pas faits pour être lus directement par vous et moi, mais pour être transformés et affichés par des logiciels comme des agrégateurs.

Ce qui fait leur force, c’est qu’ils sont bien codifiés (et peuvent être [validés](https://validator.w3.org/feed/check.cgi?url=https%3A%2F%2Fnicolasfriedli.ch%2Findex.xml) comme celui de ce site). Ils ressemblent à quelque chose comme ceci:

```
titre du site
description
date de dernière modification
lien (page d’accueil)

billet de blog 1:
    titre
    description (ou contenu complet)
    date de publication
    lien

...

billet de blog 10:
    titre
    description (ou contenu complet)
    date de publication
    lien
```

Ce formalisme permet:

rapidité
: c’est un fichier léger à télécharger et simple à analyser (c’est pourquoi un agrégateur peut vérifier des centaines de sites en quelques secondes)

écologie
: ce fichier léger minimise les ressources utilisées et il évite de se rendre sur un site web, beaucoup plus lourd, s’il n’y a pas de nouveauté à consulter

fiabilité
: la lecture d’un fichier bien formaté est beaucoup plus fiable que la consultation humaine d’un site pour découvrir des nouveautés (qui ne sont pas toujours visibles en page d’accueil)

## Pourquoi c’est génial

Comme l’écrivait Thierry Crouzet dans [La mécanique du texte](https://tcrouzet.com/books/la-mecanique-du-texte/):

> Le RSS est presque trop génial. [...] Il laisse imaginer un monde où chacun serait sa propre agence de presse, où chacun recevrait les informations sélectionnées par lui. Ce serait en quelque sorte un monde trop beau, et trop peu rentable.

Un système tout simple permet de lire de l’actualité sans passer par un moteur de recherche ni par un réseau social. Des sources peuvent être ajoutées ou supprimées en tout temps. Et surtout, la lecture n’est pas polluée par des algorithmes qui:

- censurent des contenus (selon des critères souvent douteux)
- proposent des tris ridicules (ce qui fait réagir est toujours mis en évidence)
- suggèrent des nouveautés sans arrêt (même quand tout est lu, il ne faut pas que les internautes repartent)

Voilà ce que permettent les flux RSS:

- la consultation de ce que je souhaite (et *tout* ce que je souhaite)
- la possibilité de trier les contenus selon mes préférences
- le droit d’arriver au bout de ma liste de lectures (et *seulement* de celles voulues)

## Comment lire des flux RSS

Je conseille l’utilisation d’un agrégateur en ligne, parce qu’il permet de reprendre la lecture au même endroit, quel que soit le périphérique utilisé.

J’utilise [Inoreader](https://www.inoreader.com/) en version pro. C’est à mon avis le meilleur lecteur en termes de possibilités, même si l’interface est parfois un peu tordue. La version basique gratuite permet de suivre jusqu’à 150 sites.

Un agrégateur très utilisé est [Feedly](https://feedly.com/news-reader). Je ne le recommande que dans sa version gratuite, limitée à 3 répertoires et 100 sites. J’ai utilisé la version payante il y a quelques années, mais mes tests avec la dernière version Pro+ et son intelligence artificielle ne sont pas concluants.

J’ai beaucoup de bons échos de [Feedbin](https://feedbin.com/), un agrégateur simple avec quelques options intéressantes. Je l’ai testé, mais il me manquait quelques possibilités plus pointues. Uniquement en version payante; à prix raisonnable.

On peut aussi installer un logiciel sur son propre serveur (par exemple [KrISS feed](https://tontof.net/kriss/feed/)), utiliser un logiciel dédié sur son ordinateur (par exemple [Thunderbird](https://support.mozilla.org/en-US/products/thunderbird/news-feeds-rss-blogs-and-social-thunderbird)) ou publier des flux RSS dans WordPress (par exemple [RSS Block](https://wordpress.org/documentation/article/rss-block/)).

## Pourquoi c’est irremplaçable

À mon avis, les flux RSS sont irremplaçables:

- Ils permettent un abonnement ou un désabonnement complètement anonyme par défaut, alors que les lettres de nouvelles (newsletter) donnent une adresse ou demandent des efforts pour cacher la sienne. Aucune crainte de ne pas pouvoir se désabonner ou de recevoir du spam.

- Ils permettent une veille exhaustive. Je peux partir 2 semaines en vacances et lire tous les billets publiés en mon absence. C’est presque impossible sur les réseaux sociaux.

- Ils respectent mes propres règles du jeu. Je peux les trier dans l’ordre souhaité, les filtrer, marquer des articles lus ou non lus, créer des hiérarchies, etc. Des automatismes bien conçus sont souvent meilleurs qui des intelligences artificielles qui ne cherchent qu’à impressionner.

- La liste des flux auxquels je suis abonné peut être exportée facilement. Je peux la sauvegarder, la partager à d’autres, l’importer dans un autre logiciel, etc. La liberté, c’est de pouvoir changer de plateforme et d’outil librement.

- La présentation unifiée permet une lecture rapide et agréable, même quand des flux proviennent de sites peu accessibles ou inconfortables. La légèreté des flux permet d’oublier la lenteur des sites qui les produisent. Plutôt que l’originalité, c’est l’efficacité qui compte.

----

Dans son excellente newsletter [Own Your Web](https://buttondown.email/ownyourweb), Matthias Ott propose [Issue 9: We ❤️ RSS](https://buttondown.email/ownyourweb/archive/issue-09/). Il vaut la peine de suivre les liens proposés pour approfondir le sujet. Les internautes qui ne maîtrisent pas assez l’anglais auront intérêt à lire au moins l’article [Investing in RSS](https://timkadlec.com/remembers/2023-02-23-investing-in-rss/) de Tim Kadlec en traduction automatique.

----

Cory Doctorow a publié le 16 octobre 2024 un billet de qualité sur les flux RSS comme résistance à la [merdification des choses](https://ploum.net/2023-06-15-merdification.html): [You should be using an RSS reader](https://pluralistic.net/2024/10/16/keep-it-really-simple-stupid/).
