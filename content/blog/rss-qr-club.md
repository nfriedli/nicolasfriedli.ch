---
title: Réflexions sur les RSS Club & QR Club 
description: Publications spéciales par RSS ou Atom, jeux de piste par QR codes ou géocaching culturel sont des pistes intéressantes pour la la culture, le tourisme, la théologie et l’Église. Mais la force de résistance brise bien des initiatives dans l’œuf.
date: 2026-06-22
---

Il reste plein de choses à inventer avec des outils très simples qui existent déjà.
J’avais publié une première version de ce billet dans le cadre de mes réflexions sur la théologie et les Églises protestantes.
Il est aujourd’hui généralisé à d’autres domaines, mais je conserve la conclusion initiale sur l’exclusion.

Il faut essayer de réenchanter le web, parfois contre l’immobilisme institutionnel (qui n’est pas réservé au monde ecclésial).

L’idée était partie de ces mots de Robin Masur dans [Liens repérés durant la semaine du 27 avril](https://www.cidoc.ch/component/acym/archive/151-liens-reperes-durant-la-semaine-du-27-avril?tmpl=component):

> [...] deux blogs protestants se mettent quasi-simultanément volontairement en jachère [...] ce qui pose évidemment la question de la dynamique des réseaux réformés francophones, et plus largement chrétiens.

Et au même moment je découvrais [sourcefeed](https://www.sourcefeed.app/) qui propose d’envoyer le contenu uniquement dans des flux RSS.
Pas de site web, pas de lettre de nouvelles (newsletter).

## RSS Club

C’est Dave Rupert qui a lancé l’idée dans [Welcome to RSS Club](https://daverupert.com/2018/01/welcome-to-rss-club/).
Le club est à la fois:

- ouvert, parce que flux RSS est accessible à toutes et tous, de manière gratuite et anonyme
- fermé, parce que ce qui apparaît dans le club reste dans le club

Il existe plein de mises en pratique de cette proposition.
Par exemple chez Terence Eden qui propose [ce billet](https://shkspr.mobi/blog/2026/04/rss-club-how-do-you-preserve-an-rss-feed/) uniquement dans son flux.

L’idée, c’est de valoriser les flux RSS et Atom et de dévaloriser les réseaux sociaux.
C’était pertinent en 2018, ça l’est plus encore aujourd’hui.

Un truc un peu *geek* et un peu exclusif attise ma curiosité.

Le site [Carnet de notes](https://n.survol.fr/) propose quelque chose de similaire avec un site sans contenus immédiatement visibles.

## QR Club

Avec des codes QR, on pourrait imaginer quelque chose de similaire.
La matérialité du code fait qu’il faut se rendre à un endroit précis pour le scanner.
Par exemple à la porte d’un lieu culturel (fermé), dans un endroit précis d’un bâtiment, dans un rayonnage particulier de bibliothèque.

L’information est disponible uniquement à celles et ceux qui se trouvent en cet endroit.
C’est utile pour donner une information très contextuelle comme un détail architectural.
Mais c’est aussi possible pour transmettre un petit bonus (par exemple un lien vers le livre du mois).

S’il vous prend l’idée de réaliser ce genre de chose, j’ai publié [Conseils d’utilisation des QR codes](/blog/qr-code/).

Ensuite, mon cerveau part dans tous les sens.
J’imagine instantanément une balade dans laquelle le code scanné donne les coordonnées du suivant.
Ou un système dans lequel scanner plusieurs codes est nécessaire pour passer à la suite.

Ce peut être informationnel ou ludique.
Tout est possible.

En passant, je signale que le même genre de chose pourrait être fait avec des [puces NFC](https://fr.wikipedia.org/wiki/Near-field_communication).

{{< details summary="Quid du géocaching" >}}

Comme je parle de lieux, je ne peux m’empêcher de signaler le [géocaching](https://fr.wikipedia.org/wiki/G%C3%A9ocaching).
Je vois chaque semaine des personnes qui cherchent des caches au bord du lac, qui découvrent des lieux insolites, qui s’amusent en apprenant.

C’est toutefois une démarche plus lourde puisqu’il faut créer un compte, faire accepter sa cache sur un site tiers, installer une application, etc.
Elle dépasse le cadre de ce billet.

Le géocaching a un potentiel immense pour faire découvrir du patrimoine culturel.
Les notices qui accompagnent les caches sont souvent intéressantes et bien fournies.

Je n’ai pas connaissance de caches maintenues par des communautés qui gèrent ces lieux.
Hélas.

{{</ details >}}

## Esquisse d’implémentation

Il y a une logique de base commune aux publications des RSS Club & QR Club:

- accessibles avec un lien précis
- pas listées dans la liste des dernières publications
- ne nécessitent pas de services tiers et sont anonymes

Toutefois les détails devraient être affinés:

- trouvables (ou non) par un moteur de recherche interne au site
- référencées (ou non) dans les moteurs de recherche externes
- accessibles (ou non) via un site tiers (par exemple un partage sur Facebook)
- RSS visibles aussi en version web (ou uniquement en flux)

Comme un flux RSS limite généralement ses publications en nombre, il faut se demander si les nouvelles personnes qui s’abonnent ont accès à tout l’historique ou seulement aux derniers contenus.

Pour intégrer cela dans Hugo, je procéderais ainsi:

- un répertoire `/rss-club/`: non référencé dans les moteurs de recherche et sans liste des derniers billets (mais sans aller jusqu’à tout cacher avec un dépôt GitHub privé), avec un RSS qui propose les 20 dernières publications
- un répertoire `/qr-club/` non référencé dans les moteurs de recherche mais avec une liste de billets sous forme de codes QR sans reprise des ces billets dans les flux RSS du site

Peut-être que j’accepterais de rendre les billets du RSS Club accessibles après une durée déterminée ou quand plusieurs nouvelles publications sont sorties.
Ce qui est clair, c’est que je voudrais qu’ils conservent une exclusivité durant quelques semaines.

## Bonus sur l’exclusion en Église

Dès que j’envoie en ligne des propositions un peu loufoques, j’entends des voix qui s’élèvent contre l’exclusion, notamment dans le monde protestant réformé:

> Des flux RSS?
> Et comment font celles et ceux qui ne les utilisent pas?

Remarque déjà entendue, il y bientôt 20 ans, aux *Assises du web protestant*...
Elle est toujours actuelle, l’immobilisme est une valeur sûre.
La première personne qui bouge a perdu.

> Des QR codes?
> Mais comment fait Madame Michu qui n’a pas de téléphone?

C’est épuisant, parce que celles et ceux qui défendent ces refus ont peu de scrupules à utiliser des messageries, des réseaux sociaux et des applications lourdes qui demandent installation et acceptation d’une licence.

Madame Michu, qui regarde les photos de ses petits enfants sur WhatsApp, n’a pas de téléphone, évidemment.

Monsieur Michu, conseiller paroissial, n’a aucun problème à fixer des rencontres l’après-midi, quand toutes les personnes non retraitées travaillent.
Mais ça, ce n’est pas de l’exclusion.

Je ne parle pas des sites problématiques du point de vue de l’accessibilité (A11Y), avec couleurs inadaptées aux personnes déficientes visuelles, navigation impossible à celles et ceux qui ont des troubles musculo-squelettiques et autres obstacles sonores sans retranscrition textuelle.
Là non plus, ce n’est pas de l’exclusion.

Sans parler, évidemment, du langage cryptique des Églises, souvent plus complexe que les énigmes de géocaching.
Le patois de Canaan – les doctes le savent – est un espéranto qui a réussi.

Contrairement à Robin Masur, dans la citation du début de billet, je pense qu’il n’y a aucune inquiétude pour le protestantisme en ligne.
Il s’autorégule avec efficacité.
Celles et ceux qui ont des idées hétérodoxes (mais pas hérétiques), se lassent avant les thuriféraires du «on a toujours fait comme ça».
Ouf!
