---
title: Sur le protocole Gemini
description: Remarques sur le protocole Gemini qui propose une alternative simple et légère au web. Les constats sont bons, mais la réponse n’est pas la bonne.
date: 2024-09-19
---

Mes remarques sur le protocole Gemini qui propose une alternative au web devenu complexe, lourd et qui nous traque en permanence.
Les observations de départ sont bonnes, mais le résultat ne me convainc pas.

⚠️ Ce billet ne parle pas du chatbot de Google!

## Première approche

Une explication simple (mais avec des d’erreurs):

> Gemini, c’est un site web très simple, avec des éléments HTML limités, qui demande peu de ressources, respecte votre vie privée et est facile à mettre en œuvre.

Parce que dans la réalité, Gemini:

- n’est pas sur le web (mais dans un «monde parallèle»)
- n’est pas codé en HTML (mais dans un Markdown simplifé)
- n’est pas trivial à mettre en œuvre

Ce passage résume tout le problème.
Présenté en une phrase, ça fait rêver.
Mais dès que l’on entre dans les détails, ça devient complexe à vulgariser.

## Présentation de Gemini

Pour comprendre techniquement Gemini, il faut se rendre à l’adresse:

[gemini: //geminiprotocol.net/docs/specification.gmi](gemini://geminiprotocol.net/docs/specification.gmi)

Clic.
Rien ne se passe.
Comme Gemini n’est pas le web, le navigateur habituel ne permet pas d’ouvrir la page.
Une adresse qui commence par `gemini://`, ce n’est pas fait pour un navigateur web.

Dans Firefox, Safari ou Chrome, il faut choisir une version web du site.
Dans le cas présent, cette version `https://` existe:

<https://geminiprotocol.net/docs/specification.gmi>

Et là, un site apparaît.
Mais pas besoin de le lire pour le moment.

### Un protocole

Gemini, c’est donc un protocole: `gemini://`.
Un protocole de communication, c’est un ensemble de règles de fonctionnement entre un serveur et un client (ici un navigateur).

Les informations qui transitent `gemini://` sont très limitées pour éviter le flicage, la publicité ciblée, etc.

Il vous faudra donc un navigateur spécial capable d’utiliser ce protocole.
Par exemple [Lagrange](https://gmi.skyjake.fi/lagrange/) en version graphique.

Stéphane Bortzmeyer en dit bien plus dans la première partie de: [Le protocole Gemini, revenir à du simple et sûr pour distribuer l’information en ligne?](https://www.bortzmeyer.org/gemini.html).

### Une syntaxe

Gemini, c’est aussi une syntaxe: gemtext.

Pour faire simple, c’est un [Markdown](https://commonmark.org/) simplifié qui conserve:

- des paragraphes sans formatage
- des listes à puces (non imbriquées)
- des titres (sur 3 niveaux)
- des liens (seuls sur une ligne)
- des citations
- du texte préformaté

La page transférée, c’est un fichier `.gmi`, et rien d’autre.
Il n’y a pas de feuille de style CSS, pas de JavaScript, pas même de métadonnées (comme une date de publication).

Une page, c’est donc un seul fichier envoyé, puis la mise en page sera faite par le navigateur (s’il le souhaite).

## Ce que je retiens de Gemini

Je reprends ces lignes d’une note écrite il y a quelques années, parce que rien n’a vraiment changé.

- **L’importance du texte sur le web.**
  Le texte est et reste un magnifique véhicule de contenu, surtout quand il est bien structuré par des intertitres.
  Il peut être lu sur n’importe quel périphérique, agrandi, copié-collé, dit par une synthèse vocale, etc.
- **Les liens sur une seule ligne.**
  L’obligation de proposer des liens sur une ligne (sans autre contenu), valorise l’hypertexte.
  En les mettant ainsi en valeur, ils sont facilement visibles.
  Les URL publiées seules incitent à créer des adresses immédiatement compréhensibles.
  Et on évitera peut-être les terribles: cliquez *ici*.
- **L’absence de menus.**
  En imposant tous les liens dans le corps de la page (il n’existe rien d’autre que le *corps* de la page), le rapport entre contenus et pages cibles est valorisé.
  Les *méga menus*, palliatifs de mauvaises structures de site, sont bannis de fait.
- **La mise ne page côté client.**
  C’est le navigateur qui *esthétise* la page, et j’adore ça.
  Je souhaite que les internautes installent de bonnes polices sur leurs systèmes et configurent leurs navigateurs.
  Le web aurait tout intérêt à utiliser un peu plus les [polices déjà installées]({{% relref "polices-systeme" %}}) sur les périphériques.
- **Le retour du *vieux web*.**
  Après quelques tests de Gemini, je remarque combien il est perturbant de ne pas disposer de moteur de recherche.
  La navigation se fait de proche en proche; les favoris (*bookmarks*) reprennent tout leur sens.

## Pourquoi Gemini ne me convient pas

Pourtant, après un nouvel essai, je ne suis toujours pas convaincu.

J’ai **installé un serveur** [Agate](https://github.com/mbrubeck/agate) en 3 minutes sur un Raspeberry Pi et mis un site en ligne.
Et ça fonctionne.
Du côté du serveur, la promesse de simplicité est tenue.

En revanche, l’**installation d’un navigateur** n’est pas aussi facile.
Sur mon ordinateur Linux, c’est bon.
Sur Android et iOS, il n’est pas possible de passer par les outils d’installation «normaux».
Faire reposer la complexité sur les internautes ne me convient pas!

En naviguant dans l’écosystème Gemini, j’ai trouvé beaucoup de **serveurs et navigateurs non maintenus**.
On a l’impression que tout est en test, comme il y a quelques années.

**Est-ce que Gemini est vraiment léger?**
Est-ce que ce site en version Gemini sur mon Raspberry serait plus léger que la version HTML hébergée chez Infomaniak?
Est-ce qu’il est vraiment pertinent d’installer un navigateur graphique de plus?

Et quand je lis Daniel Stenberg dans [The Gemini protocol seen by this HTTP client person](https://daniel.haxx.se/blog/2023/05/28/the-gemini-protocol-seen-by-this-http-client-person/), je me dis que la **simplicité affichée** n’est pas la réalité.
Quand l’auteur de [curl://](https://curl.se/), un des logiciels les plus utilisés au monde, soulève ce genre de questions, il me semble qu’il faut l’écouter.

Dans certains cas, Gemini est aussi un **moyen de fuir ses responsabilités**.
Proposer un site principal pourri, avec du JavaScript inutile partout, des traqueurs et des images qui clignotent.
Puis publier une capsule Gemini à côté (avec très peu de contenus) pour afficher sa mesure et sa sobriété.
Faire un bon site principal (unique) serait une meilleure idée.

Ploum (Lionel Dricot) est une des rares personnes à avoir complètement assumé le passage à Gemini.
Il en parle dans [La fin d’un blog et la dernière version de ploum.net](https://ploum.net/2022-12-04-fin-du-blog-et-derniere-version.html).
Mais en pratique, c’est bien sa version web que je lis…
