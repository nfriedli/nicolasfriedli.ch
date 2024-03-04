---
title: Données structurées pour un blog personnel
description:
date: 2024-04-15
draft: true
---


## JSON-LD est sans limite

Donc travail de recherche, compilation, etc.

## Données en page d’accueil

Où (et quoi)?

[Steal Our JSON-LD](https://jsonld.com/)

Minimum:

```
{
    "@context": "http://schema.org",
    "@type": "WebSite",
    "name": "Nicolas Friedli",
    "description": "Consultant web à Neuchâtel (Suisse).",
    "url": "https://nicolasfriedli.ch/"
}
```

Utile:

```
<script type=’application/ld+json’>
{
  "@context": "http://www.schema.org",
  "@type": "person",
  "name": "Nicolas Friedli",
  "address": {
     "@type": "PostalAddress",
     "streetAddress": "Rue du Château 3",
     "addressLocality": "Colombier",
     "addressRegion": "Neuchâtel",
     "postalCode": "2013",
     "addressCountry": "CH"
  },
  "email": "hello@nicolasfriedli.ch",
  "telephone": "+41793443382"
}
</script>
```

## Structure simple

Trop de données chez Yoast Mais l’imbrication est un plus du schéma.

```
{
    "@context": "http://schema.org",
    "@type": "WebSite",
    "name": "Nicolas Friedli",
    "description": "Consultant web à Neuchâtel (Suisse).",
    "url": "https://nicolasfriedli.ch/",
    "author": "Nicolas Friedli"
}
```

## Construction à la main

Construire à la main pour comprendre schema.org

## Intégration dans Hugo

Pure fichier JSON, dans le répertoire des données

Intégration sans transformation (sauf minification)

Par partial uniquement sur la page d’acceuil