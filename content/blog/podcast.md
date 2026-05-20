+++
title = "Sur les podcasts"
description = "Réflexion en cours sur les podcasts: génération par intelligence artificielle, publication d’un texte d’accompagnement utile, poids des fichiers produits, choix des outils de diffusion et risque de merdification."
date = 2026-02-11
+++

Je me pose pas mal de questions sur le podcasts.
Ce n’est pas complètement nouveau, j’avais publié un billet sur une ancienne version de ce blog il y a 5 ans…
Mais je remarque que c’est un format qui a pas mal de succès ces temps, auprès des toutes les tranches d’âges.
Peut-être un moyen de [rejoindre les gens où ils sont](/blog/rejoindre/).

**Ce billet est une simple prise de note.**
Il ne parle que de podcasts audio.
Tout y est provisoire.
:tada: Surprise en toute fin de billet. :tada:

## Préciser la notion de «podcast»

Lorsque nous parlons de «podcast», nous parlons de plusieurs choses différentes, par abus de langage.
J’essaie de poser les termes pour mieux se comprendre ensuite:

épisode
: un contenu d’un podcast, qui contient un titre, une date, une description et un fichier audio (et parfois une image)

podcast
: un ensemble d’épisodes, auquel il est possible de s’abonner, qui a un titre et une description (et parfois une image)

flux
: un fichier RSS qui comprend la définition du podcast et de chaque épisode, c’est en fait au flux que l’on s’abonne (sans forcément s’en rendre compte)

Ce qui est définitoire du podcast pour moi, c’est l’abonnement.
Je peux m’abonner pour obtenir automatiquement les nouveaux épisodes.
Je peux les écouter quand je veux, ce qui diffère de la radio (classique) ou de la télévision (avant le replay).
C’est asynchrone; je n’ai pas besoin d’écouter un épisode au moment exact de sa mise en ligne.
Cet abonnement, je peux le faire dans un logiciel ou sur une plateforme, mais toujours via un flux RSS.

C’est tellement simple et génial qu’il est possible de s’abonner dans un simple agrégateur (Feedly, Inoreader, Feedbin, etc.).
Si c’est pour quelques abonnements, pas besoin de créer un compte sur une plateforme obscure.

Je conseille le passage [Concept](https://fr.wikipedia.org/wiki/Podcasting#Concept) de la page Wikipédia sur le sujet.

## Retour sur le podcast «Explore» de l’EERS

Sur la page [Podcast EERS Explore Saison 2](https://www.eks-eers.ch/fr/themenseite/podcast-eers-explore-saison-2-le-partage-de-la-foi/), Elio Jaillet propose un regard rétrospectif sur «Explore» de l’Église évangélique réformée de Suisse (EERS).
Sa réflexion porte sur le fond du processus créatif, je l’ai trouvée intéressante, critique et honnête.
C’est précieux pour toute personne ou toute institution qui cherchera à se lancer dans la production d’un podcast.

Sans surprise, je vais m’intéresser aux aspects techniques, qui ne sont pas l’objet de l’analyse d’Elio Jaillet.
Je remarque:

- que la page en question propose plein de fichiers audio, mais sans possibilité de s’abonner (ce n’est pas un podcast)
- qu’un flux RSS (c’est un podcast) est disponible (bravo), mais sur la page [Explore chez podigee.io](https://kteexplore.podigee.io/) seulement
- que les abonnements sont possible par des plateformes, avec toutes les [merdifications](https://nicolasfriedli.ch/blog/merdification/) à venir

Mes question toutes simples:

- Pourquoi ne pas héberger le podcast directement sur son nom de domaine?
- Le succès de «Explore» est-il la raison pour décentraliser la diffusion?

## Remarques techniques

Formellement, un podcast est donc uniquement un flux RSS comme le rappelle Jeremy Keith (Adactio) dans [Spaceships, atoms, and cybernetics](https://adactio.com/journal/22301):

> The common belief is that nobody uses RSS feeds these days. And while it’s true that I wish more people used feed readers—[the perfect antidote to being fed from an algorithm](https://www.citationneeded.news/curate-with-rss/)—the truth is that millions of people use RSS feeds every time they listen to a podcast. That’s what a podcast is: an RSS feed with enclosure elements that point to audio files.

En détail, un RSS propose:

- une entrée générale pour tout le podcast (au sens de la définition ci-dessus)
- une entrée pour chaque épisode (idem)

Ce que je trouve intéressant, c’est que chaque épisode comprend notamment:

- un titre
- un fichier audio
- une description (courte?)
- un texte (long?)

J’ai l’impression que c’est sous-utilisé et j’essaie d’esquisser quelques pistes.

## Test avec NotebookLM

J’ai publié [Enjeux de la curation de contenu](https://theologique.ch/blog/curation/) il y a quelques jours.
Une thématique dont parle aussi le lien dans la citation d’Adaction ci-dessus.

Puis j’ai demandé à NotebookLM de me générer un épisode.
C’était sur un site de démo, mais le fichier audio est toujours disponible en archive: :loudspeaker: [Épisode de podcast sur la curation généré par NotebookLM](https://web.archive.org/web/20260113091024/https://spip.theologique.ch/IMG/m4a/curation.m4a).

Il était hébergé sur un site de test en sous-domaine, qui produisait un RSS qui était un vrai podcast, repris automatiquement sur Spotify.
Je n’ai pas l’intention de le faire pour le moment, mais j’ai expérimenté la possibilité d’héberger son podcast complet pour échapper à la merdification.

Je vous laisse juger le résultat.
Tout n’est pas parfait, mais c’est intéressant d’entendre un dialogue à partir d’un simple billet de blog.

Mais j’ai aussi des questions:

- Est-il intéressant de créer un audio de presque 13 minutes à partir d’un billet qui se lit 3 ou 4 minutes?
- Est-il légitime de transmettre ce contenu par un fichier de plus de 20Mo alors que la page textuelle est 1000 fois (!) plus légère?

Pourtant, entre les possibilités offertes nativement par les flux RSS et celles proposées par les intelligences artificielles (IA) génératives, il me semble qu’il faut se poser plus de questions.

## Du podcast au texte

Quand l’audio précède le texte:

- Faut-il proposer un résumé seulement?
- Faut-il proposer un texte complet (avec des liens, éventuellement des images ou des fichiers à télécharger)?
- Faut-il publier une transcription exacte?
- Faut-il lancer une IA générative (IAg) pour transcrire ou résumer?
- Faut-il laisser les internautes lancer une IA générative (IAg) pour transcrire ou résumer?

Aujourd’hui, toutes ces questions se posent.
Les 2 dernières sont les plus importantes, parce qu’elles peuvent changer le coût énergétique de manière gigantesque.
Je dois simplement être conscient que, si je ne propose pas de contenu textuel sérieux, je laisse chaque internaute qui le souhaite produire le sien.

## Du texte au podcast

Nous avons vu avec mon test de NotebookLM que l’on peut aussi lancer une IAg pour créer un épisode.

Quand un épisode est rédigé avant l’audio (scripté), d’autres questions se posent:

- Faut-il encore produire un épisode de podcast humain ou laisser faire les machine?
- Faut-il se contenter de bons textes et lasser les synthèses vocales (locales et légères) lire le contenu?
- Faut-il suggérer aux internautes de créer leur propre podcast, avec l’IAg de leur choix (et espérer une écoute après 10 minutes de génération)?

Je ne soutiens évidemment pas la dernière piste qui est une horreur de consommation et d’utilisation de son temps, mais je mentionne son existence.

## Ce qu’il faudrait traiter

Au fond, je crois que je suis bien avec mes billets textuels.

Mais si le sujet intéresse, je réfléchirai peut être à ceci:

- le risque de merdification :poop: des services tiers
- le plateformes privatrices :lock:
- des meilleurs pistes pour créer des textes de description et de contenu plus utiles (qui accompagne vraiment l’écoute plutôt que d’y inciter seulement) :compass:
- les outils pour autohéberger son podcast (le vieux SPIP le fait nativement…) :toolbox:

----

Je suis intéressé à toutes questions, remarques, critiques, retours, etc. pour essayer de me construite un avis plus éclairé sur le sujet.

----

Pour l’exercice, j’ai généré un :loudspeaker: [épisode sur le contenu de cette page](https://archive.org/details/l-independance-du-podcast-face-a-l-ia) par NotebookLM.
