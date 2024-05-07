---
title: Tester un site web
description: Proposition de tests techniques et pratiques à effectuer pour une première appréciation d’un site web.
date: 2024-02-13
---

Il n’est pas rare que l’on me demande ce que je pense d’un site web personnel ou professionnel. Une petite phrase lâchée dans une discussion informelle:

> J’ai un nouveau site, est-ce que tu jettes un coup d’œil et tu me dis ce que tu en penses?

Voici quelques tests que je vais effectuer sans délai pour me faire une idée. Car je ne vais pas me contenter de *regarder* le site et de naviguer sur quelques pages. L’ordre des tests dépendra de ce que je vais trouver dans mes investigations.

## Ouvrir le site

Dans un premier temps, je vais me rendre sur le site, sur sa page d’accueil. Je vais jeter un premier regard rapide, m’intéresser à la taille de la police, aux contrastes, à la mise en page, etc. afin de voir si tout semble normal. En principe, jusqu’ici, tout va plutôt bien.

Puis je vais désactiver le cache du navigateur et limiter la bande passante. Je vais contrôler le poids des ressources qu’il télécharge et leur provenance au rechargement de la page. J’aurai une idée de la vitesse d’affichage. Il n’est pas rare que des lenteurs et des lourdeurs soient déjà perceptibles.

## Lancer PageSpeed Insights

Ensuite, je vais coller l’adresse du site dans [PageSpeed Insights](https://pagespeed.web.dev/). Si les 4 résultats sont verts, c’est bon signe. Si certains résultats sont orange, ils deviendront naturellement des points d’attention. Si des résultats sont rouges, je vais focaliser mes investigations dans ces domaines avant tout.

## Regarder l’état du référencement

Puis je me rendrai dans Google et effectuerai une recherche du type`site:nicolasfriedli.ch`. Ainsi j’aurai une idée:

- du nombre de pages référencées
- de la qualité de l’affichage des résultats de recherche (SERP)

Si le site est très récent et qu’il n’est pas affiché, je le signalerai. Si le site est ancien et peu présent (ou mal affiché), je lancerai la thématique du référencement. À quoi bon un site, même excellent, que l’on ne trouve pas.

## Naviguer sur plusieurs périphériques

Par la suite, je vais ouvrir le site sur plusieurs ordinateurs, avec des écrans de plusieurs tailles, différents systèmes d’exploitation et navigateurs. Je vais y naviguer sur ma tablette et sur mon smartphone.

Je vais redimensionner la fenêtre manuellement, essayer de zoomer le texte, vérifier des contrastes. J’essaierai de m’y rendre à plusieurs moments de la journée, parce qu’un site n’est pas le même en plein soleil ou dans la pénombre.

## Tester la navigation au clavier et l’accessibilité

Je vais retourner sur la page d’accueil et tenter de naviguer en utilisant mon seul clavier. Je verrai si l’utilisation des menus est fluide, si l’ordre des liens est correct, s’ils sont visibles à la sélection, etc.

C’est un test d’accessibilité (A11Y) basique, que je vais compléter par un passage dans [WAVE Web Accessibility Evaluation Tools](https://wave.webaim.org/) pour contrôler la structure de la page, les textes alternatifs des images, etc.

## Lire quelques contenus

Si je trouve un page à fort contenu, je vais la lire intégralement. Je pourrai me rendre compte en pratique de la lisibilité de la police choisie (sur plusieurs systèmes d’exploitation), des choix de contraste, de la mise en évidence des liens, de l’usage des intertitres et des listes.

Je vérifierai aussi si les lignes de textes ne sont pas trop longues ou trop courtes, si l’interligne est pertinent. Si, à la moitié de la page, j’ai une impression de fatigue, je suppose que d’autres internautes l’auront aussi.

## Se faire une idée du bilan carbone

Par la suite, je vais tester le bilan carbone du site dans [Website Carbon Calculator](https://www.websitecarbon.com/). À vrai dire, j’aurai déjà une idée du résultat en fonction de tous les tests précédents, mais cette vérification n’est pas de trop.

C’est un test que je trouve particulièrement important pour tous les sites qui parlent de ressources, d’écologie, de respect de la Création, etc. Un peu de cohérence ne fait jamais de mal.

## Contrôler la validité du code

Un passage par les validateurs du World Wide Web Consortium (W3C) me permettra de vérifier l’état du code:

- [validation HTML](https://validator.w3.org/)
- [validation CSS](https://jigsaw.w3.org/css-validator/)
- [validation RSS ou Atom](https://validator.w3.org/feed/)

Avec le dernier test, je contrôlerai si un flux RSS ou Atom peut être découvert automatiquement. Et s’il est absent, je me demanderai s’il serait pertinent d’en proposer un.

## Parcourir l’entier du site

Par la suite, je lancerai encore un outil qui parcourt l’entier du site (*crawl*), par exemple [SEO Spider Tool](https://www.screamingfrog.co.uk/seo-spider/). Je découvrirai les éventuels liens morts, les répétitions fautives dans les titres ou les descriptions, etc.

Un site en ligne depuis longtemps et avec beaucoup de pages aura souvent plus de liens morts qu’un site tout frais. Mais cette vue d’ensemble permet souvent de découvrir des scories qu’il est facile de corriger.

## Passer aux règles Opquast

Si tout s’est bien passé jusque là, je vérifierai certaines [règles Opquast](https://checklists.opquast.com/fr/assurance-qualite-web/). En particulier celles que je trouve les plus pertinentes sur ce site précis sur lequel j’aurai déjà passé quelques minutes.

Par exemple, si le site présente beaucoup d’adresses de contact, je contrôlerai leur contenu. Si le site est en plusieurs langues, je regarderai la gestion du multilinguisme.

## Envoyer un retour

Cette petite analyse n’est pas un audit au sens strict. Je ne vais donc pas rendre un document complet qui détaille tous les points. En fonction de ce que j’ai vu dans mon parcours, je choisirai sur quoi portera mon retour.

J’essaierai toujours de dire le plus simplement possible:

- ce qui m’a plu dans le site testé
- les problèmes les plus importants qu’il pose

Envie d’essayer? Testez vous-même votre site par les différentes étapes proposées. Ou prenez le risque de me demander de «jeter un coup d’œil rapide».
