---
title: Adresses mail avec le signe + (plus)
description: L’utilisation du site + (plus) dans une adresse de messagerie permet de créer instantanément un nombre illimité d’alias, de détecter des fuites de données et de filtrer ses messages avec efficacité.
date: 2025-01-04
lastMod: 2025-01-07
---

L’utilisation du signe `+` (plus) dans une adresse de messagerie permet de créer un nombre illimité d’alias.
C’est intéressant pour la détection des fuites de données et le filtrage avancé de sa boîte de réception.
Mais cette méthode a aussi ses limites.

## Caractères autorisés (et interdits)

La constitution d’une adresse mail répond à la fois à des normes et aux critères adoptés par son hébergeur.
Les hébergeurs peuvent être plus restrictifs que les règles définies par l’IETF (Internet Engineering Task Force).

La page Wikipédia sur les adresses de messagerie (en anglais) donne une excellente [liste d’exemples d’adresse valides et invalides](https://en.wikipedia.org/wiki/Email_address#Examples).
La validité de ces adresses est celle des normes dans les [RFC (Request for comments)](https://fr.wikipedia.org/wiki/Request_for_comments) de l’IETF.

Ensuite, votre hébergeur peut restreindre ces choix.
Par exemple, Infomaniak, l’excellent hébergeur de ce site: [Découvrir les caractères admis pour une adresse mail](https://www.infomaniak.com/fr/support/faq/438/decouvrir-les-caracteres-admis-pour-une-adresse-mail).

Pour moi, une adresse bien pensée est constituée uniquement de:

- **Lettres minuscules.**
  La partie à droite de l’arobase `@` (adresse du serveur) peut utiliser des minuscules comme des majuscules, c’est toujours équivalent.
  Les serveurs ne font *en général* pas de distinction entre majuscules et minuscules pour la partie à gauche de `@` (partie locale).
  Les variations de type [CamelCase](https://fr.wikipedia.org/wiki/Camel_case) apportent plus de confusion que de clarté.
- **Points.**
  Ils remplacent les espaces (s’il est souhaité de rendre visible les «espaces» dans une adresse).
  Ils sont, par exemple, la séparation logique entre prénom et nom.
- **Traits d’union.**
  Je conseille de les utiliser seulement quand ils existent déjà dans la graphie courante.
  Par exemple, l’adresse mail de Jean-Alcide Nanchen pourrait être `jean-alcide.nanchen@gmail.com`.

En plus de ces 3 types de caractères, il existe le fameux signe `+` ou plus.
L’idée est à la fois simple et géniale.
Le serveur considère comme synonyme les adresses suivantes:

```
prenom.nom@frdl.ch
prenom.nom+newsletter@frdl.ch
prenom.nom+anti.spam@frdl.ch
```

Les 3 courriers arriveront bien à l’adresse `prenom.nom@frdl.ch`.
C’est utile car simple à mettre en œuvre, voici pourquoi.

## Les alias mail

### Alias «classique»

Créer un alias mail, c’est équivalent à coller un nom supplémentaire sur sa boîte aux lettres.
Par exemple, sous mon nom, je peux ajouter un autocollant «Association Libido Dièse».
Les courriers adressés à cette remarquable association seront déposés dans ma boîte personnelle.

Sur le serveur `frdl.ch`, je pourrais créer:

```
prenom.nom@frdl.ch      <- mon adresse
libido.diese@frdl.ch    <- un alias
```
Cela signifie que, avant de recevoir un courrier papier ou mail:

- dans la vie physique, je dois créer un autocollant et l’apposer sur ma boîte aux lettres
- sur le serveur, je dois créer l’alias avant qu’il soit utilisable

### Alias par `+` (plus)

Pour reprendre l’analogie du courrier postal, il faut que l’adresse soit quelque chose comme: «Association Libido Dièse - Nicolas Friedli».

En version serveur mail:

```
prenom.nom@frdl.ch                  <- mon adresse
prenom.nom+libido.diese@frdl.ch     <- un alias
```

Cela signifie que:

- dans la vie physique, je n’ai pas besoin d’ajouter un autocollant sur ma boîte aux lettres
- sur le serveur, je n’ai rien à créer pour que cela fonctionne (à condition que mon hébergeur gère bien les `+`)

C’est génial parce que je «crée» un alias au moment même de l’écriture de l’adresse.

### Tracer les fuites de données

Par exemple, lorsque je m’abonne à une lettre de nouvelles, j’ajoute toujours un `+`.
Et j’utilise une adresse Gmail.

Donc, pour les lettres de nouvelles la commune de Pétaouchnok:

```
nicolas.friedli+petaouchnok@gmail.com
```

Désormais, si je reçois un spam à cette adresse, je sais que la fuite de données provient de la commune Pétaouchnok.
Peut-être qu’elle a donné mon adresse à des tiers (contrairement à sa promesse de ne pas le faire).
Peut-être que son serveur a été piraté.

### Trier efficacement ses mails

Comme `nicolas.friedli+petaouchnok@gmail.com` est désormais utilisée pour du spam, je peux ajouter un filtre qui balance automatiquement à la poubelle tout ce qui contient `+petaouchnok@`.

Si je recouvre confiance en cette commune, je peux toujours me risquer à un réabonnement avec:

```
nicolas.friedli+le.retour.de.petaouchnok@gmail.com
```

Mais je peux aussi utiliser d’autres alias utiles.
Par exemple, pour déplacer automatiquement dans un répertoire donné:

```
prenom.nom+urgent@frdl.ch
prenom.nom+reservation2025@frdl.ch
```

À défaut de filtrer ou trier automatiquement, une recherche avec une adresse précise est diablement efficace.

### Créer des comptes multiples

Autre utilité des alias par `+`, la possibilité de créer plusieurs comptes:

- tu joues à Brawl Stars et tu souhaites 2 comptes
- une administration exige une adresse différente pour chaque membre de la famille
- tu veux profiter d’une offre gratuite limitée...

## Limites de l’utilisation du `+`

Maintenant que l’on a vu plein de belles choses à faire avec `+`, voici pourquoi tout n’est pas complètement rose.

### Configuration des serveurs

La règle [Opquast 23](https://checklists.opquast.com/fr/assurance-qualite-web/le-site-accepte-les-alias-mail-contenant-le-signe) est claire:

> Le site accepte les **alias** mail contenant le signe +.

La règle parle bien du serveur sur lequel vous souhaitez vous inscrire avec une adresse mail.
C’est une mauvaise idée de ne pas l’accepter, mais ça arrive.
Difficile de faire plier certaines entreprises et administrations.

En passant, si votre hébergeur n’accepte pas les adresses avec `+`, changez d’hébergeur!

### Changement de propriétaire

Un «vrai» alias permet de rediriger ailleurs lorsque les propriétaires changent.
Ce n’est pas le cas avec une adresse en `+` qui reste toujours liée à l’adresse de départ.

Dans mon exemple de l’Association Libido Dièse, l’alias en `+` sera toujours lié aux mêmes prénom et nom:

```
prenom.nom@frdl.ch                  <- mon adresse
prenom.nom+libido.diese@frdl.ch     <- un alias
```

Alors qu’un alias

```
prenom.nom@frdl.ch       <- mon adresse
libido.diese@frdl.ch     <- alias original vers prenom.nom@frdl.ch  
libido.diese@frdl.ch     <- alias modifié vers prenom2.nom2@frdl.ch
libido.diese@frdl.ch     <- ou redirection vers libidodiese@gmail.com
```

L’alias «classique» demande de la maintenance (création, suppression, gestion des redirections), mais est très souple.
L’alias `+` ne demande aucun travail, mais offre moins de possibilités.

### Malices des spammeurs et spammeuses

Si j’étais spammeur, je m’empresserais de nettoyer tous les `+` pour limiter les possibilités de filtrage de mes victimes.
C’est facile avec [expression régulière](https://fr.wikipedia.org/wiki/Expression_r%C3%A9guli%C3%A8re).
Si vous ne savez pas ce que c’est, vous pouvez vous amuser avec [regular expressions 101](https://regex101.com/).

Dans mon éditeur VS Code, j’efface ce qui correspond à `\+[^@]*`.

En français:

> Sélectionne le `+` puis tous les caractères qui suivent à condition que ce ne soit pas un `@`.
> Puis remplace cette chaîne par... rien.

Vous pouvez voir le résultat dans dans [regexr.com](https://regexr.com/8an1s).

### Adresse temporaire

Avec un alias classique, il est possible de créer un mail temporaire, qui sera détruit une fois devenu inutile.
Par exemple, pour envoyer des sa candidature à un emploi précis:

```
postulation237@frdl.ch
``` 
Une fois le délai passé cet alias est détruit.

Alors que qu’avec les adresses en `+`, l’adresse originale est toujours dévoilée.
Pour un même type d’usage:

```
rh+postulation237@frdl.ch 
```
D’une part l’adresse d’origine est dévoilée (`rh@frdl.ch`), d’autre part l’alias n’est pas désactivable une fois le délai passé et tous les messages envoyés à cette adresse arriveront bien dans la boîte des ressources humaines.

Un alias classique permet aussi d’anonymiser l’adresse de destination.
Personne ne pourra savoir où atterit l’adresse `qwertz@frdl.ch`, alors que `prenom.nom+qwertz@frdl.ch` dévoile sa destination.

## Note sur les adresses Gmail

En lisant des normes et pratiques pour rédiger cet article, je me suis souvenu d’une particularité de Gmail.

Les points n’ont aucune importance dans les adresses `@gmail.com`.
Ainsi, les mails envoyés à toutes ces adresses arriveront au même endroit:

```
prenom.nom@gmail.com
prenomnom@gmail.com
p.r.enom.n.om@gmail.com
```

C’est plutôt intéressant du point de vue de la sécurité, parce qu’il est difficile d’usurper une identité par l’ajout de `.` (points).

Et, bien entendu: Gmail permet l’utilisation des adresses en `+`.

----

Je reçois volontiers un message avec vos cas d’utilisation intéressants.
Le mail en `+` se trouve en pied de page.

----

## Antispam

[Matthieu Amiguet](https://matthieuamiguet.ch/) me signale à juste titre que pour lutter sérieusement contre le spam, il est bien d’utiliser un service dédié.
Par exemple [spamgourmet](https://www.spamgourmet.com/) qui permet de créer une adresse unique qui se détruit automatiquement après avoir mangé assez de messages.

Il existe aussi l’idée de l’adresse jetable, qui cache complètement votre mail, quand vous vous abonnez à des newsletters dans des lecteurs de flux RSS en ligne.
C’est le cas chez Inoreader, Feedbin et Feedly (au moins).

Pour d’autres services, lancez une [recherche Google]({{% relref "recherche-google-avancees" %}}) (ou autre) sur `mail jetable` ou `adresse mail unique`.
