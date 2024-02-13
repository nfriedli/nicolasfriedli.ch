---
title: htaccess chez Infomaniak
description: Pour des sites générés avec Hugo et hébergés chez Infomaniak, voici le .htaccess type que j’utilise. C’est une version découpée en plusieurs parties avec des commentaires. 
date: 2024-02-12
---

Pour des sites générés avec Hugo et hébergés chez Infomaniak, voici le `.htaccess` type que j’utilise. C’est une version découpée en plusieurs parties avec des commentaires.

L’encodage et la langue par défaut sont directement envoyés en entête:

```
AddDefaultCharset UTF-8
DefaultLanguage fr-ch
```

Si la page est appellée en `http` ou s’il elle commence par `www`, on renvoie à un version en `https` sans `www` (voir [Opquast 192](https://checklists.opquast.com/fr/assurance-qualite-web/toutes-les-pages-utilisent-le-protocole-https) et [Opquast 211](https://checklists.opquast.com/fr/assurance-qualite-web/ladresse-du-site-fonctionne-avec-et-sans-prefixe-www)). On renvoie tout sur la page d’accueil et on impose le nom de domaine (plutôt que s’utiliser `HTTP_HOST`):

```
RewriteCond %{HTTPS} off [OR]
RewriteCond %{HTTP_HOST} ^www. [NC]
RewriteRule ^(.*)$ https://nicolasfriedli.ch/$1 [R=301,L]
```

On envoie des entêtes pour la sécurité du site. La première ligne existe [par défaut chez Infomaniak](https://www.infomaniak.com/fr/support/faq/2133/gerer-hsts-dun-site-webhebergement), mais en version trop limitée pour le soumettre à [HSTS preload](https://hstspreload.org/). Le reste peut être testé chez [Security Headers](https://securityheaders.com/).

```
Header always set Strict-Transport-Security "max-age=63072000; includeSubDomains; preload"
Header always set X-Content-Type-Options "nosniff"
Header always set X-Frame-Options "DENY"
Header always set X-XSS-Protection "1;mode=block"
Header always set Referrer-Policy "same-origin"
Header always set X-Permitted-Cross-Domain-Policies "none"
```

En cas d’erreur, on renvoie logiquement une erreur 404, mais pas de page personnalisée pour le moment (voir [Opquast 216](https://checklists.opquast.com/fr/assurance-qualite-web/le-serveur-envoie-une-page-derreur-404-personnalisee)):

```
ErrorDocument 404 https://nicolasfriedli.ch/
```

On redirige le flux RSS de WordPress (qui a été utilisé ici) vers le flux produit par Hugo. C’est une redirection permanente:

```
Redirect 301 /feed/ /index.xml
```

Je choisis de gérer le cache (voir [Opquast 220](https://checklists.opquast.com/fr/assurance-qualite-web/le-serveur-envoie-les-informations-permettant-la-mise-en-cache-des-contenus)) très simplement, par extension de fichier. Les images reçoivent un cache de 1 mois:

```
<filesMatch ".(jpg|jpeg|png|gif|ico|svg|webp|avif)$">
Header set Cache-Control "max-age=2592000,public"
</filesMatch>
```

Pour les feuilles de style et les polices d’écriture locales, je choisis un cache `immutable`. Ce qui signifie que ces fichiers ne seront jamais rechargés par le navigateur durant 2 ans. Il faut utiliser un numéro de version (*cache busting*) pour ne pas se planter. Avec Hugo, j’utilise un identifiant unique (*fingerprint*) pour les feuilles de style CSS externes. Pour les polices d’écriture, je conseille de passer par [google-webfonts-helper](https://gwfh.mranftl.com/fonts) qui donne toujours des noms de fichier avec numéro de version. Voici la directive:

```
<filesMatch ".(css|woff2)$">
Header set Cache-Control "max-age=63072000,immutable"
</filesMatch>
```

Le [`.htaccess` utilisé pour ce site](https://github.com/nfriedli/nicolasfriedli.ch/blob/main/static/.htaccess) peut être repris presque sans modifications, mais n’oubliez pas de changer le nom de domaine ou d’utiliser `HTTP_HOST`.

Avant de modifier un fichier `.htaccess` en ligne, il faut s’assurer de **pouvoir y accéder par un autre moyen** (par exemple par FTP). Si Wordpress est utilisé pour modifier un tel fichier, en cas d’erreur il ne sera plus du tout accessible (et votre site non plus).
