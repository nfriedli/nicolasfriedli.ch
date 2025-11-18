---
title: Création & affichage d’une page web
description: À chaque fois qu’une page s’affiche dans un navigateur, des centaines d’opérations ont eu lieu avant pour établir la connexion au serveur, pour générer la page sur le serveur, pour transférer des tas de fichiers, pour mettre en forme le résultat final.
date: 2024-03-17
---

Dans le monde des Bisnounours: j’entre une adresse et le site est à l’écran.
Mais dans la vraie vie, à chaque fois qu’une page s’affiche dans un navigateur, des centaines d’opérations ont eu lieu avant cet affichage pour établir la connexion au serveur, pour générer la page sur le serveur, pour transférer des tas de fichiers, pour mettre en forme le résultat final.

**Note.** Ce billet est une vulgarisation du sujet.
Je fais l’impasse sur plusieurs étapes, je simplifie le propos et je commets des erreurs dans la chronologie des choses.
Ces approximations ont une visée pédagogique; ce sont les grands principes qui comptent.

## Se rendre sur le serveur

L’adresse `https://nicolasfriedli.ch/webperf/creation-affichage-page-web/` est saisie dans un navigateur ou un lien vers elle est suivi.
Voici ce qui se passe:

- Le navigateur va interroger un serveur de noms (DNS) pour savoir à quelle adresse IP correspond le nom de domaine `nicolasfriedli.ch`, par exemple `128.65.195.39`.
Le modem, le périphérique ou le navigateur vont garder ce résultat en mémoire un certain temps.
- Puis le navigateur va demander la création d’une connexion sécurisée `https` et va vérifier la validité d’un certificat, stocker des informations de chiffrement, etc.
Ici aussi, des informations sont conservées dans la durée.

✅ Désormais, le navigateur est prêt.

## Création de la page sur le serveur

Ce que demande le navigateur au serveur, c’est une page HTML (et rien d’autre pour le moment).
Voici ce qui va se passer dans 3 cas distincts.

### Avec un CMS comme WordPress

L’outil de gestion de contenu (CMS) va effectuer les opération suivantes:

- recherche dans une base de données à quel numéro de billet correspond `/webperf/creation-affichage-page-web/`
- recherche du contenu du billet dans une autre table de base de données
- à partir de là, recherche du nom de l’auteur ou de l’autrice, recherche des différentes taxonomies utilisées
- recherche des informations sur le menu du site
- recherche des contenus des *widgets*
- recherche de la liste des derniers billets publiés
- et si le blog utilise des commentaires, recherche de tous les commentaires attribués au billet
- et peut être aussi les derniers commentaires sur tout le site pour les afficher en barre latérale
- etc.

Puis il va lire les gabarits de mise en page (le thème WordPress, les squelettes SPIP, etc.) et assembler toutes les données reçues dans un seul fichier HTML.
Il est enfin prêt à répondre au navigateur.
**Toutes ces opérations ont lieu pour chaque page du site et à chaque visite.**

✅ Le HTML est envoyé.

### Quand le CMS utilise un système de cache

Afin de minimiser le travail inutile, un système de cache peut être utilisé.
Il n’est malheureusement pas présent par défaut chez WordPress.
Le principe est simple.
Quand une page est demandée:

- si la page existe déjà sur le serveur et si elle n’est pas trop ancienne, elle est envoyée telle quelle au navigateur
- si la page n’existe pas encore ou si elle est trop ancienne, elle est créée (en suivant toutes les étapes vues au point précédent) et stockée

**Les opérations sur le serveur ne sont pas réalisées à chaque visite, mais elles restent les même quand elles sont effectuées.**

Si le *principe* est simple, la mise en pratique est beaucoup plus compliquée.
Par exemple, lorsque la barre latérale d’un site liste les derniers billets et que le titre du dernier billet est modifié, il faut invalider le cache de toutes les pages (alors que seuls quelques mots d’une page ont changé).
Pour imaginer les enjeux pratiques: [Cache Invalidation and the Methods to Invalidate Cache](https://www.geeksforgeeks.org/system-design/cache-invalidation-and-the-methods-to-invalidate-cache/).

✅ Le HTML est envoyé.

### Avec un site statique

Quand une page est demandée:

- elle existe déjà et est livrée telle quelle
- sauf si le navigateur demande une page qui n’existe pas ou plus (une erreur 404 est retournée)

✅ Le HTML est envoyé.

## Affichage de la page dans le navigateur

Site dynamique, site statique, qu’importe désormais, le navigateur a reçu son fichier HTML.
Il pourra donc se lancer dans l’affichage de la page.

### Téléchargement des ressources

Dans un premier lieu, le code HTML est intégralement lu et tous les fichiers nécessaires à la page sont demandés au serveur:

- feuilles de style CSS (le modèle de mise en page)
- images
- code JavaScript

Le processus de création continue.

### Création de la page

Désormais, le navigateur utilise la structure (HTML) et la présentation (CSS) pour créer visuellement la page.
Selon les informations qu’il aura trouvées dans le fichier CSS, il va charger de nouvelles ressources (par exemple des polices d’écriture particulières ou des images de fond).

Si ces polices d’écriture se trouvent sur un autre nom de domaine, il va devoir refaire la requête DNS et la vérification des certificats de sécurité si ces données ne sont pas en mémoire.

Le processus de création continue.

### Interprétation du JavaScript

Le code JavaScript est interprété.
Le «logiciel navigateur» exécute un «logiciel JavaScript» pour avancer dans la création de la page.
Ce code peur servir à:

- afficher un menu dynamique
- envoyer des statistiques à un service tiers
- chercher des données utiles pour affichage sur la page

Mais aussi à inclure des *widgets* des réseaux sociaux, qui eux-mêmes vont rechercher plus de JavaScript, du code HTML et CSS, etc.

✅ En principe, la page est terminée.

### Quelques données statistiques

Le *Web Almanac 2024* donne les résultats de tests pour des millions de sites.
Quelques résultats extraits de la rubrique [Page Weight](https://almanac.httparchive.org/en/2024/page-weight):

- quand 1 page s’affiche, ce n’est pas 1 seul fichier qui voyage sur les réseaux, mais environ 70 (mesure médiane)
- et ce sont plus de 2.5MB de données qui sont envoyées
- en valeur médiane, ce sont 20 images pour une seule page
- et 23 fichiers en JavaScript (qui devront tous être exécutés dans le navigateur)
- le poids des pages web pour mobile a augmenté de 1.8MB 10 ans

Le souci que nous avons aujourd’hui, c’est que les serveurs, les réseaux et les périphériques (ordinateur, tablette, téléphone, etc.) sont devenus si performants que l’on ne voit plus tout ce qui y transite et tous les calculs effectués.
Pour maintenir un niveau de performance correct, au vu de la lourdeur des sites, il faut changer plus souvent de matériel.
Écologiquement, c’est lamentable.

## Après la visite

Lors de l’envoi des différentes ressources au navigateur, le serveur devrait lui transmettre des informations de conservation.
C’est un *cache local* du navigateur, différent de celui du serveur qui peut être utilisé dans les CMS.

Par exemple:

- l’image du logo de l’entreprise, qui s’affiche en haut à gauche de la page, peut être conservée durant 1 mois
- le feuille de style CSS est valable 1 semaine
- le polices d’écriture (si elles ne sont pas chargées chez Google Fonts), peuvent être conservées durant 6 mois

Ainsi, tous les fichiers ne sont pas chargés à chaque visite, ce qui est serait un gâchis immense.
Malheureusement, beaucoup de sites gèrent mal le cache ou ne l’utilisent pas du tout.

## Différence entre statique et dynamique

Pour faire simple, une page web, telle que nous la voyons, ne préexiste jamais.
**Une page est toujours assemblée dans le *navigateur*** à partir de HTML, de CSS, de JavaScript et des fichiers multimédia.
Mais:

- avec un site statique, tout ce qui peut l’être est déjà prêt et optimisé sur le *serveur*
- avec un site dynamique, toute une machinerie se met en route sur le *serveur* pour chaque page et chaque internaute

Le vrai problème avec les sites dynamiques, quel que soit l’outil (WordPress, Drupal, Typo3, etc.), c’est quand ils motorisent des *sites vitrines* qui évoluent peu.
À quoi bon calculer chaque page pour chaque internaute si rien de change d’une personne à l’autre.
C’est de la bande passante et de l’énergie jetées par les fenêtres.

Mais rien n’est perdu.
Il reste de nombreuses de possibilités de faire un site lent et peu écologique avec un générateur de sites statiques, car [La Jamstack n’est rapide que si vous y veillez](https://jamstatic.fr/2020/10/05/la-jamstack-n-est-rapide-que-si-vous-la-rendez-rapide/).
Tout est envisageable pour publier des images trop grandes, saturer le site de JavaScript, le pourrir de tierces parties inutiles et mal gérer son cache.
