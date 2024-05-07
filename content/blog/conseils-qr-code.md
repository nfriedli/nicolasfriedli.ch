---
title: Conseils d’utilisation des QR codes
description: Les personnes qui proposent des QR codes peuvent aider à les rendre sûrs et fiables. Toute la responsabilité ne repose pas seulement sur les utilisateurs et utilisatrices.
date: 2024-02-14
lastMod: 2024-03-15
---

Les arnaques aux QR codes semblent se multiplier. Les médias généralistes en parlent et donnent quelques conseils, souvent aux utilisateurs et utilisatrices (par exemple: [Les arnaques aux QR codes se multiplient depuis quelques mois](https://www.rts.ch/info/sciences-tech/14581852-les-arnaques-aux-qr-codes-se-multiplient-depuis-quelques-mois.html)). Pourtant, j’estime que **l’effort de sécurisation et de fiabilité doit aussi être fait du côté des personnes qui créent les codes**.

Je parle en priorité des codes qui dirigent vers une page web, mais plein d’autres utilisations sont possibles. La page [Codes QR – applications et risques](https://www.ncsc.admin.ch/ncsc/fr/home/infos-fuer/infos-private/aktuelle-themen/qr-code-anwendungen-und-risiken.html) sur le site de la Confédération suisse donne quelques exemples d’utilisations et de problèmes potentiels.

## Petits et grands problèmes

Si un code qui ne fonctionne pas comme prévu est toujours un problème, il faut tout de même hiérarchiser les soucis:

Parfois, un QR code **ne fonctionne pas**. Il renvoie à une adresse (URL) qui n’existe pas ou plus. C’est frustrant, décevant, l’image de l’institution en prend un coup. Les conséquences sont toutefois limitées.

Dans d’autres cas, le QR code **renvoie à la mauvaise adresse**. Soit l’adresse a toujours été problématique, soit la destination (via une redirection) a été modifiée, intentionnellement ou non. Difficile de mesurer les conséquences: un détournement peut être amusant, insultant, sans intérêt, mauvais pour l’image, choquant, provocant, etc.

Finalement, un QR code est **utilisé pour une arnaque**. Le code de départ est remplacé ou le système de redirection piraté, et les internautes arrivent sur un faux site qui cherche à voler des informations. Le code n’est qu’un maillon de la chaîne d’un système organisé. Les conséquences peuvent être importantes et on sort du domaine technique pour entrer dans les questions de loi et de justice.

## Conseils lors de l’utilisation

Les utilisateurs et utilisatrices de QR codes ont intérêt à adopter quelques réflexes utiles.

### Avant de scanner

Il faut vérifier aussi bien que possible si **le code n’a pas été remplacé par un autre**. Un autocollant posé sur un ancien code est suspect, sans être forcément frauduleux.

Il vaut également la peine de se poser la question de la **pertinence du code**. Si on vous promet l’accès à un wifi gratuit en pleine rue, sur un petit autocollant collé sur un lampadaire, il n’est pas toujours judicieux de le scanner.

### Après avoir scanné mais avant de cliquer

Une fois le code scanné, le téléphone propose l’ouverture d’un lien, l’acceptation d’un réseau wifi, un paiement sur Twint, etc. Il est possible de **contrôler la destination** du code à ce moment-là. Quand une institution officielle propose un QR code, je trouve qu’elle devrait toujours renvoyer à son nom de domaine.

### En arrivant sur le site

Si le clic a été effectué mais que **le site de destination semble bizarre**, il est encore temps d’arrêter les frais. En particulier quand des informations personnelles ou de paiement sont demandées ou quand une application est proposée à l’installation (surtout si elle n’avait pas été mentionnée dans le texte qui accompagne souvent le code).

## Conseils lors de la création

Les conseils précédents sont destinés aux utilisateurs et utilisatrices. Les suivants sont destinés à celles et ceux qui créent et rendent publics des QR codes.

### Utiliser son propre nom de domaine

Je pense que **l’utilisation de raccourcisseurs d’URL est souvent une mauvaise idée**. Infomaniak vient de lancer son service [chk.me](https://chk.infomaniak.com/). Personne ne pourra savoir quelle sera l’URL finale qui se cache derrière cette version courte.

L’utilisation de **son propre nom de domaine est une garantie de sécurité**. Il peut être utilisé de 2 manières:

- en renvoyant à une URL directe (peut-être longue), en générant un code dans un outil tiers ou directement dans son navigateur
- en renvoyant à une URL spécifique (souvent plus courte), redirigée par `.htaccess`, son outil de gestion de contenu (par exemple [Redirection](https://fr.wordpress.org/plugins/redirection/) pour WordPress) voire par son propre système de redirection

**C’est sans discussion la solution la plus simple et la plus efficace.**

En complément, je propose de toujours écrire en toutes lettres l’adresse vers laquelle le code est censé renvoyer.

### Proposer un support non accessible

Quand un code est affiché quelque part, tout est bon pour le rendre non accessible directement:

- affichage dans une vitrine ou derrière une vitre
- affichage sur un écran ou en image projetée
- affichage dans un endroit inaccessible (en hauteur, derrière un guichet, au plafond, etc.)

### Rendre la substitution complexe

Si la modification d’un QR code est très difficile, **la génération d’un autre code et la substitution sont très simples** (sauf quand le support est difficilement accessible).

Plutôt que d’imprimer seulement un petit autocollant sur fond blanc, on peut imprimer le code sur un papier à entête officiel de l’institution, et pourquoi pas y ajouter une marque au tampon encreur. D’autres pistes existent comme le papier holographique ou la gravure sur une plaque métallique.

Comme pour l’argent liquide, **c’est la complexité et le coût de la falsification** qui la rendront moins intéressante.

### Modifier l’URL finale plutôt que remplacer

Parfois, des adresses changent. Plutôt que de coller un nouveau code (suspect) sur l’ancien, il est préférable de **modifier l’URL finale**. C’est une démarche facile avec son propre nom de domaine et des redirections. Ainsi, le support ne sera pas modifié par ajouts successifs.

De plus, c’est pertinent dans le cas où un QR code est utilisé à plusieurs endroits. Plutôt que de faire modifier le support à un moment précis, **la redirection est instantanée et généralisée**.

### Vérifier régulièrement le fonctionnement

Quand un code est utilisé par une organisation, une institution ou une entreprise, je conseille de **demander aux membres et employé·es de le vérifier régulièrement**. Un scan rapide permet de s’assurer qu’il fonctionne toujours et qu’il renvoie au bon endroit. C’est de plus une bonne incitation à utiliser régulièrement cet outil.

### Supprimer proprement les codes invalides

Finalement, quand une page de destination est désactivée, il faut agir intelligemment:

- s’il est certain que le QR code n’était affiché qu’en un endroit, il peut être simplement supprimé
- mais quand le code était utilisé à plusieurs endroits, il vaut mieux **conserver une redirection**, par exemple vers une page générique qui annonce sa désactivation (ou à défaut sur la page d’accueil de son site)

D’un point de vue technique, je pense que toutes les URL courtes (sur son nom de domaine) ne devraient jamais être utilisées pour renvoyer ailleurs après une désactivation. En version courte: **nouvelle redirection oui, réutilisation non**. C’est le principe d’un identifiant unique (*UID*).

----

Je suis preneur de tous vos conseils pratiques et retours d’expérience sur le sujet.

----

**Ajout du 15 mars 2024.** Quelques jours après la publication de ce billet, ma commune de Milvignes publiait sur son site un [problème de QR codes](https://web.archive.org/web/20240313084500/https://www.milvignes.ch/communications/detail/probleme-avec-les-qr-codes-du-milvignes-infos-de-mars-2024-ne-pas-les-utiliser). Elle avait utilisé un système de redirection (`qr.codes` ou `qr.io`) payant plutôt que de renvoyer directement à son propre nom de domaine. La période d’essai était expirée; les codes invalides...