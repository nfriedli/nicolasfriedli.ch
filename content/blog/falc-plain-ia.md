---
title: Notes sur les textes faciles à lire et à comprendre et sur le langage clair
description: 
date: 2024-09-02
categories:
- a11y
---

Cette page n'est pas écrite en langage simple, claire, FALC, etc.

## Mis en contexte

Extrait du *Premier chant* de l'*Art poétique* de Nicolas Boileau:

> Il est certains esprits dont les sombres pensées  
> Sont d’un nuage épais toujours embarrassées;  
> Le jour de la raison ne le saurait percer.  
> Avant donc que d’écrire, apprenez à penser.  
>
> Selon que notre idée est plus ou moins obscure,  
> L’expression la suit, ou moins nette, ou plus pure.  
> Ce que l’on conçoit bien s’énonce clairement,  
> Et les mots pour le dire arrivent aisément.

## Contenus en FALC

Voici deux exemples réussis qui m'ont incité à aller plus loin:

- La ville de La Chaux-de-Fonds propose une [brochure scolaire d'information aux parents en FALC](https://www.chaux-de-fonds.ch/ecoles-formations/ecole-obligatoire/documents-liens)
- Le Festival de bande dessinée de Lausanne (BDFIL) propose une [présentation en FALC](https://bdfil.ch/falc/)

Ces deux contenus me paraissent exemplaires.
Ils donnent des informations précises et rapide.
Je le trouve plus efficaces que les contenus «normaux».

## Pour démarrer

- Pour lancer vos recherches sur cette thématique, je conseille la conférence [Le contenu doit être rédigé de la manière la plus claire et la plus simple possible: les textes dans l’accessibilité numérique](https://www.paris-web.fr/2023/conference/-le-contenu-doit-etre-redige-de-la-maniere-la-plus-claire-et-la-plus-simple-possible-la-question-des-1) donnée par Morganie Hauguel à Paris Web 2023
- Le billet [Le contenu doit être rédigé clairement: retour sur la conférence Paris Web 2023](https://blog.whoz.me/non-classe/le-contenu-doit-etre-redige-clairement-retour-sur-la-conference-paris-web-2023/) est un excellent complément
- Morgane Hauguel s'est aussi exprimée à MiXiT 2024: [Ce que l'on conçoit bien s'écrit clairement: les textes et l'accessibilité numérique](https://mixitconf.org/2024/ce-que-l-on-concoit-bien-s-ecrit-clairement-les-textes-et-l-accessibilite-numerique)

## Analyse de lisibilité

- [Scholarius](https://www.scolarius.com/) est un outil gratuit d'analys ede la lisibilité des textes en français
- Microsoft Word semble propose le [score Fleisch-Kincaid](https://fr.wikipedia.org/wiki/Tests_de_lisibilit%C3%A9_Flesch-Kincaid) dans ses statistiques

## Accessibilité

Les écritures simplifiées font partie du domaine plus large de l'accessibilité.
Dans le domaine du web, je considère que l'accessibilité (A11Y) a au moins 4 composantes:

- l'accessibilité du contenu (dont on parle sur cette page)
- la lisibilité du contenu (choix de la police, taille, contraste, interligne, longueur de lignes, etc.)
- la structure du site (architecture d'information, navigation, complexité des pages, etc.)
- la technique (validité du code, sémantique des balises HTML, ARIA, etc.)

## Simplification par IA

Mes recherches sont en cours suite à la demande d'une administration pour la simplifications de certaines contenus administratifs.

Je ne parle pas ici des questions de confidentialité, des questions écologiques, des problèmes éthiques, etc. 

- La qualité du travail dépend de qualité des demandes adressées (prompts).
  Je propose quelques pistes de prompts.

- Une intelligence artificielle (IA) comme ChatGPT permet de simplifier des textes de manière efficace.
  Elle est souvent meilleure à la simplification qu'à la génération.
  Il faut tout faire pour éviter les délires et hallucinations, par exemple ainsi:
  
      Il ne faut rien ajouter au contenu de départ.

- On peut ajouter les règles principles qui doivent être appliquées au texte:

      Réécrire le texte en langage clair (PLAIN) ou facile à lire et à comprendre (FALC)
      Passer les phrases à la forme active.
      S'adresse aux personnes en «vous».
      Simplifier les mots complexes (ou les expliquer entre parenthèses)

- Au départ,on peut demander à ChatGPT de calculer le score Fleisch-Kincaid.
  Puis demander un nouveau calcul en fin de travail.

- Affiner le travail en cours de route:

      Passer les énumérations en listes à puces
      Mettre en gras les idées les plus importantes

  Et pourquoi pas relancer:

      Le texte doit être encore plus simple

- On peut aussi demander des mises en forme:

      Saut de ligne à la fin de chaque phrase (mais pas de saut de paragraphe)

D'après mes premiers tests, ChatGPT (version gratuite) permet d'excellents résultats.
C'est rapide et précis.

## Critères de Yoast