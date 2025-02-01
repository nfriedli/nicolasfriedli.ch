---
title: Notes sur la création d’un site d’urgence
description: Il y aura bien un problème de site web un jour ou l’autre. L’urgence ne se prévoit pas, mais il est possible de s’y préparer.
date: 2024-06-03
---

Entre les pannes de serveur, les incertitudes concernant l’approvisionnement énergétique, les pics d’affluence et les catastrophes naturelles, nous avons toutes les raisons de penser qu’il y aura bien une urgence un jour ou l’autre. L’urgence, par définition, comporte sa part d’imprévisible. Mais ce n’est pas une raison pour ne pas s’y préparer.

## Travail de Max Böck

Le développeur autrichien Max Böck a déjà très bien balisé le terrain. Je me suis inspiré de ces réflexions et ses solutions pour rédiger ce billet.

Je vous conseille en particulier la lecture de ses articles:

- [The Hurricane Web](https://mxb.dev/blog/hurricane-web/) qui pose les problèmes à la suite de l’ouragan Florence
- [The Emergency Website Kit](https://mxb.dev/blog/emergency-website-kit/) qui propose une solution technique complète viable

Par la suite, je développe ces thématiques à ma sauce.

## Types d’urgences

Il me semble qu’il existe 3 types d’urgences dont je vous donne une typologie.

### Crash du serveur

**Votre serveur tombe en panne et votre site n’est plus fonctionnel.** L’hébergeur subit une avarie, votre serveur de nom de domaine est cassé, la base de données hébergée chez vous est en panne, etc. Qu’importe, votre site ne peut pas être consulté.

En fonction de la réalité du bug, il faudra renvoyer les internautes ailleurs. Dans ce cas, **un site d’urgence préexistant** est une bénédiction. Il y a déjà un lien à donner aux médias et à publier sur les réseaux sociaux.

### Faiblesse des infrastructures

**Les réseaux sont affaiblis.** Une grande panne électrique, une inondation ou un ouragan mettent à mal les réseaux. Les internautes consulteront le web avec un faible débit, en grand nombre sur les antennes relais encore fonctionnelles. 

La légereté du site sera un critère déterminant pour le rendre accessible dans de mauvaises conditions. Un **site simple et léger** à afficher videra moins rapidement les batteries des utilisateurs et utilisatrices qui peinent à recharger leurs téléphones.

### Affluence extraordinaire

**Un nombre exceptionnel d’internautes consulte votre site sur une courte période.** Une annonce sanitaire comme celles de la crise du Coronavirus, des résultats d’élections ou l’ouverture d’une billetterie peuvent provoquer un nombre de visites considérable.

Les équipes techniques disent souvent que tout est prévu... mais les sites tombent régulièrement. **Ces pics d’affluence sont souvent prévisibles** quelques jours ou quelques jours à l’avance. Mais la solution prévue est-elle suffisante?

### Tout en même temps

Ces différents cas peuvent s’accumuler, mieux vaut mettre toutes les chances de son côté. Une grande innodation peut parfaitement faire tomber l’infrastructure locale (il faut arrêter le serveur), affaiblir les réseaux (l’alimentation électrique des relais est coupée) et provoquer un pic d’affluence (toutes les personnes qui subissent les pannes essaient de trouver des informations au même moment).

Pour répondre à ce scénario catastrophe, il vaut la peine d’envisager une **solution technique radicale**.

## Choix techniques

Il me semble que la réponse à apporter exige les choix suivants:

- réserver un domaine de secours chez un autre prestataire que le domaine courant
- héberger ses serveurs de nom (DNS) dans une autre région géographique
- disposer d’un serveur prêt à l’emploi à distance
- être capable d’administrer le site dans passer par son adresse mail courante

Pour tenir la charge, je conseille:

- un [site statique](/blog/site-statique-generateur-hugo/)
- des pages légères
- la suppression tièrces parties inutiles en cas d’urgence: polices d’écritures distantes, plugins des réseaux sociaux ou images «décoratives», voire l’outil statistique s’il charge le même serveur

Quand une très forte affluence est prévisible, plutôt que de remplacer le site, je propose:

- de publier une page statique en tant que page accueil
- puis de renvoyer au site normal pour la petite proporition d’internautes qui cherche d’autres informations

Je travaille généralement avec Hugo, mais tous les générateurs de sites statiques peuvent convenir, à condition d’un **résultat léger**. La page peut aussi être créée à la main, dans un éditeur de texte.


## Exemple de réalisation

Pour une ville suisse qui prenait ses précaution suite aux incertitudes énergétiques suite à l’invasion russe en Ukraine, j’ai élaboré un site de secours. Avec les servicess de la ville, nous avons pris le temps, paradoxalement, de **ne pas travailler dans l’urgence**.

Le résultat:

- un site en ligne (mais volontairement non référencé), dont le nom de domaine est distinct du site principal et réservé chez un autre prestataire
- une gestion des contenus sur GitHub
- un hébergement sur le CDN CloudFlare qui peut encaisser d’énormes charges

Au quotidien, ce site existe. Il est utilisé comme système de liens (à la Linktree). Les internautes ne s’aperçoivent pas son potentiel dans les cas particuliers.

Quand c’est nécessaire, le site officiel de la ville est basculé sur le site d’urgence (si les DNS fonctionnent encore) ou les liens sont envoyés dans les réseaux sociaux. **Un message apparaît avec les informations immédiatement utiles.** Il a été activé une fois, pendant quelques heures, pour pallier l’absence du site officiel durant une migration technique.

Évidemment, pour que cela fonctionne, il est important que les équipes de communication disposent d’**une documentation sérieuse** pour prendre en main la solution sans hésitation et en toute confiance.

----

Je dispose d’une version [Hugo](https://gohugo.io/) du site d’urgence de Max Böck qui peut être déployée très rapidement.


