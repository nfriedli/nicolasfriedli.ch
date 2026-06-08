---
title: htaccess pour site statique chez Infomaniak
description: Gestion du cache, redirection propres, entêtes de sécurité, etc. Voici le .htaccess type que j’utilise pour mes sites statiques hébergés chez Infomaniak. Une bonne configuration du cache peut améliorer les performances et le bilan carbone d’un site en quelques lignes.
date: 2026-06-08
images:
- https://cdn.pixabay.com/photo/2018/01/26/18/21/matrix-3109378_1280.jpg
---

Gestion du cache, redirection propres, entêtes de sécurité, etc.
Voici le *`.htaccess` type* que j’utilise pour mes sites hébergés chez Infomaniak.
**Une bonne configuration du cache peut améliorer les performances et le bilan carbone d’un site en quelques lignes.**

Ma configuration courante est toujours [disponible chez GitHub](https://github.com/nfriedli/nicolasfriedli.ch/blob/main/static/.htaccess).
Je suis disponible pour vous donner un coup de main dans la rédaction de votre `.htaccess` pour site statique.

Merci de lire l'avertissement final avant de faire des modifications hasardeuses!

## Généralités

L’encodage et la langue par défaut sont directement envoyés en entête (voir [Opquast 228](https://checklists.opquast.com/fr/qualite-numerique/les-en-tetes-envoyes-par-le-serveur-contiennent-les-informations-relatives-au-jeu-de-caracteres-employe)):

```
AddDefaultCharset UTF-8
DefaultLanguage fr-CH
```

## Nom de domaine, `https` & redirections

On utilise le nom de domaine nicolasfriedli.ch sans l’imposer (le site est aussi accesible par ses synonymes comme theologique.ch), sans sous-domaine et en `https` (voir [Opquast 197](https://checklists.opquast.com/fr/qualite-numerique/toutes-les-pages-utilisent-le-protocole-https)) 
Le site fonctionne avec ou sans `www` (voir [Opquast 218](https://checklists.opquast.com/fr/qualite-numerique/ladresse-du-site-fonctionne-avec-et-sans-prefixe-www)):

```
RewriteEngine On

# Suppression des www pour tous les domaines
RewriteCond %{HTTP_HOST} ^www\.(.+)$ [NC]
RewriteRule ^(.*)$ https://%1/$1 [R=301,L]

# Passage au HTTPS obligatoire
RewriteCond %{HTTPS} !=on
RewriteRule ^(.*)$ https://%{HTTP_HOST}/$1 [R=301,L]
```

Je précise que toutes les pages du site possèdent une balise de type [canonical](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Attributes/rel#canonical) pour éviter les contenus dupliqués:

```
<link rel="canonical" href="https://nicolasfriedli.ch/[...]">
```

On supprime tous les paramètres des URL avec des chaînes de requêtes (query string) qui n’ont pas de sens pour un site statique.
Je conseille cela sur un site statique, je le déconseille vivement avec un CMS classique.
Si vous avez la certitude de ne pas utiliser de *query strings*, vous pouvez envoyer:

```
RewriteCond %{QUERY_STRING} !^$
RewriteRule ^(.*)$ /$1? [R=301,L]
```


Si un dossier existe mais qu’il n’a pas d’`index.html`, on affiche une erreur 404:

```
RewriteCond %{REQUEST_FILENAME} -d
RewriteCond %{REQUEST_FILENAME}/index.html !-f
RewriteRule ^.*$ /404.html [L]
```


En cas d’erreur (en général), on renvoie aussi une erreur 404 (voir [Opquast 223](https://checklists.opquast.com/fr/qualite-numerique/le-serveur-envoie-une-page-derreur-404-personnalisee)):

```
ErrorDocument 404 /404.html
```
On affiche le flux RSS généré par Hugo aussi s’il est appelé par une URL *à la WordPress*, mais sans redirection:

```
RewriteRule ^feed/?$ /index.xml [L]
```

## Entêtes de sécurité

On permet l’accès aux flux pour des agrégateurs comme [Blogs Are Back](https://www.blogsareback.com/):

```
<FilesMatch "\.(xml|rss|atom)$">
    Header set Access-Control-Allow-Origin "*"
    Header set Access-Control-Allow-Methods "GET, HEAD, OPTIONS"
</FilesMatch>
```

On envoie des entêtes pour la sécurité du site.
La première ligne existe [par défaut chez Infomaniak](https://www.infomaniak.com/fr/support/faq/2133/gerer-hsts-dun-site-webhebergement), mais en version trop limitée pour une soumission à [HSTS preload](https://hstspreload.org/).
Le reste peut être testé chez [Security Headers](https://securityheaders.com/).

```
Header always set Strict-Transport-Security "max-age=63072000; includeSubDomains; preload" env=HTTPS
Header always set X-Content-Type-Options "nosniff"
Header always set X-Frame-Options "deny"
Header always set Referrer-Policy "no-referrer"
Header always set X-Permitted-Cross-Domain-Policies "none"
Header always set Permissions-Policy "accelerometer=(), camera=(), geolocation=(), gyroscope=(), magnetometer=(), microphone=(), payment=(), usb=()"
```

Je n’utilise pas d’entêtes de sécurité de type [Content Security Policy (CSP)](https://developer.mozilla.org/fr/docs/Web/HTTP/Guides/CSP) que je trouve pénibles à gérer quand la feuille de style CSS n’est pas externe.

## Gestion du cache

On en profite pour supprimer les entêtes de cache inutiles ou contre-productifs (voir la conférence [Cache Rules Everything](https://www.youtube.com/watch?v=qVQjGwm_mmw) du génial Harry Roberts):

```
Header unset Pragma
Header unset Last-Modified
```

Je choisis de gérer le cache (voir [Opquast 227](https://checklists.opquast.com/fr/qualite-numerique/le-serveur-envoie-les-informations-permettant-la-mise-en-cache-des-contenus)) très simplement, par extension de fichier.
Les images reçoivent un cache de 1 an:

```
<filesMatch ".(jpg|jpeg|png|gif|ico|svg|webp|avif)$">
    Header set Cache-Control "max-age=31536000,public"
</filesMatch>
```

Pour les feuilles de style et les polices d’écriture locales, je choisis un cache `immutable`.
Ce qui signifie que ces fichiers ne seront jamais rechargés par le navigateur durant 2 ans.
Il faut utiliser un numéro de version (*cache busting*) pour ne pas se planter.
Avec Hugo, j’utilise un identifiant unique (*fingerprint*) pour les feuilles de style CSS externes.
Pour les polices d’écriture, je conseille de passer par [google-webfonts-helper](https://gwfh.mranftl.com/fonts) qui donne toujours des noms de fichier avec numéro de version.

Si vous avez bien compris de quoi il s’agit, vous pouvez envoyer cette directive (même si, actuellement, mon site n’utilise ni CSS externes, ni polices web):

```
<filesMatch ".(css|woff2)$">
    Header set Cache-Control "max-age=63072000,immutable"
</filesMatch>
```

## Avertissement technique amical

Si vous ne suivez pas vos fichiers avec un système de gestion de version (comme Git) ou si votre hébergeur ne permet pas de retrouver la version de la veille, **sauvegardez le `.htaccess` qui fonctionne avant toute modification**!

Avec certains CMS, comme WordPress, il est possible de modifier le fichier `.htaccess` en ligne dans l’interface d’administration (*backend*).
C’est pratique et efficace.
Mais **si votre fichier produit une seule erreur, votre site ne sera plus du tout accessible**; ni le site public, ni l’interface d’administration.
Donc, avant de modifier un fichier via le *backend* du CMS, il faut s’assurer de **pouvoir y accéder par un autre moyen** (par exemple par FTP ou par l’interface d’administration de l’hébergeur).


