---
title: htaccess chez Infomaniak
description: Gestion du cache, redirection propres, entêtes de sécurité, etc. Voici le .htaccess type que j’utilise pour mes sites hébergés chez Infomaniak. Une bonne configuration du cache peut améliorer les performances et le bilan carbone d’un site en quelques lignes.
---

Gestion du cache, redirection propres, entêtes de sécurité, etc.
Voici le *`.htaccess` type* que j’utilise pour mes sites hébergés chez Infomaniak.
**Une bonne configuration du cache peut améliorer les performances et le bilan carbone d’un site en quelques lignes.**

L’encodage et la langue par défaut sont directement envoyés en entête (voir [Opquast 228](https://checklists.opquast.com/fr/qualite-numerique/les-en-tetes-envoyes-par-le-serveur-contiennent-les-informations-relatives-au-jeu-de-caracteres-employe)):

```
AddDefaultCharset UTF-8
DefaultLanguage fr-ch
```

On impose d’utiliser le nom de domaine nicolasfriedli.ch (qui a des synonymes comme theologique.ch), en `https` (voir [Opquast 197](https://checklists.opquast.com/fr/qualite-numerique/toutes-les-pages-utilisent-le-protocole-https)) et sans sous-domaine.
Le site fonctionne avec ou sans `www` (voir [Opquast 218](https://checklists.opquast.com/fr/qualite-numerique/ladresse-du-site-fonctionne-avec-et-sans-prefixe-www)):

```
RewriteCond %{HTTPS} !=on [OR]
RewriteCond %{HTTP_HOST} !^nicolasfriedli\.ch$ [NC]
RewriteRule ^(.*)$ https://nicolasfriedli.ch/$1 [R=301,L]
```

On supprime tous les paramètres des URL avec des chaînes de requêtes (query string) qui n’ont pas de sens pour un site statique.
Je conseille cela sur un site statique, je le déconseille vivement avec un CMS classique:

```
RewriteCond %{QUERY_STRING} !^$
RewriteRule ^(.*)$ /$1? [R=301,L]

```

En cas d’erreur, on renvoie logiquement une erreur 404 (voir [Opquast 223](https://checklists.opquast.com/fr/qualite-numerique/le-serveur-envoie-une-page-derreur-404-personnalisee)):

```
ErrorDocument 404 /404.html

```

On envoie des entêtes pour la sécurité du site.
La première ligne existe [par défaut chez Infomaniak](https://www.infomaniak.com/fr/support/faq/2133/gerer-hsts-dun-site-webhebergement), mais en version trop limitée pour une soumission à [HSTS preload](https://hstspreload.org/).
Le reste peut être testé chez [Security Headers](https://securityheaders.com/).

```
Header always set Strict-Transport-Security "max-age=63072000; includeSubDomains; preload" env=HTTPS
Header always set X-Content-Type-Options "nosniff"
Header always set X-Frame-Options "deny"
Header always set X-XSS-Protection "1;mode=block"
Header always set Referrer-Policy "no-referrer"
Header always set X-Permitted-Cross-Domain-Policies "none"
Header always set Permissions-Policy "accelerometer=(), camera=(), geolocation=(), gyroscope=(), magnetometer=(), microphone=(), payment=(), usb=()"
```

On en profite pour supprimer les entêtes de cache inutiles ou contre-productifs (voir la conférence [Cache Rules Everything](https://www.youtube.com/watch?v=qVQjGwm_mmw) du génial Harry Roberts):

```
Header unset Pragma
Header unset Last-Modified
```

Je choisis de gérer le cache (voir [Opquast 227](https://checklists.opquast.com/fr/qualite-numerique/le-serveur-envoie-les-informations-permettant-la-mise-en-cache-des-contenus)) très simplement, par extension de fichier.
Les images reçoivent un cache de 1 mois:

```
<filesMatch ".(jpg|jpeg|png|gif|ico|svg|webp|avif)$">
Header set Cache-Control "max-age=2592000,public"
</filesMatch>
```

Pour les feuilles de style et les polices d’écriture locales, je choisis un cache `immutable`.
Ce qui signifie que ces fichiers ne seront jamais rechargés par le navigateur durant 2 ans.
Il faut utiliser un numéro de version (*cache busting*) pour ne pas se planter.
Avec Hugo, j’utilise un identifiant unique (*fingerprint*) pour les feuilles de style CSS externes.
Pour les polices d’écriture, je conseille de passer par [google-webfonts-helper](https://gwfh.mranftl.com/fonts) qui donne toujours des noms de fichier avec numéro de version.

En connaissance de cause, vous pouvez envoyer cette directive:

```
<filesMatch ".(css|woff2)$">
Header set Cache-Control "max-age=63072000,immutable"
</filesMatch>
```

Le [`.htaccess` utilisé pour ce site](https://github.com/nfriedli/nicolasfriedli.ch/blob/main/static/.htaccess) peut être repris presque sans modifications, mais n’oubliez pas de changer le nom de domaine ou d’utiliser `HTTP_HOST`.

----

Avec certains CMS, comme WordPress, il est possible de modifier le fichier `.htaccess` en ligne à partir de l’interface d’administration (*backend*).
C’est pratique et efficace.
Mais **si votre fichier produit une erreur, votre site ne sera plus du tout accessible**; ni le site public, ni l’interface d’administration.
Donc, avant de modifier un fichier via le *backend*, il faut s’assurer de **pouvoir y accéder par un autre moyen** (par exemple par FTP ou par l’interface d’administration de l’hébergeur).
