---
title: Données structurées pour un blog personnel
description: Schema.org et JSON-LD pour aider les moteurs de recherche à comprendre le statut de son site et améliorer la compréhension des billets de blog.
date: 2024-03-21
categories: 
- json
---

Les données structurées permettent de simplifier le travail des moteurs de recherche et d’améliorer la précision des informations fournies. Après quelques généralités, je vous dis ce que j’ai implémenté sur ce site généré avec Hugo.

## JSON for Linking Data et Schema.org

JSON-LD (JSON for Linking Data) est un format recommandé pour intégrer des données structurées dans une page HTML. Comme son nom l’indique, il utilise la syntaxe JSON (JavaScript Object Notation) répandue dans le domaine du web.

En HTML, des métadonnées existent déjà, mais elles sont des balises simples, sans structure. Par exemple: 

```
<meta name="author" content="Nicolas Friedli">
```

Mais qui est ce «Nicolas Friedli»? Impossible d’en dire plus dans les métadonnées habituelles. [JSON-LD](https://json-ld.org/) permet de structurer les données et propose une *grammaire*.

[Schema.org](https://schema.org/) — une initiative commune de Google, Microsoft, Yahoo et Yandex — développe un *vocabulaire* pour remplir ces champs JSON. Tout l’enjeu désormais, c’est de donner des informations utiles, ni trop ni trop peu.

## Données en page d’accueil

Sur la page d’accueil de ce site, je tiens à ajouter quelques métadonnées pour:

- définir clairement le nom du site
- identifier son auteur sans hésitation

Il est possible de générer des petits fichiers avec [Steal Our JSON-LD](https://jsonld.com/), mais j’ai préféré le faire à la main en lisant la documentation de Schema.org.

### Nom du site

En suivant les indications de [Fournir un nom de site pour la recherche Google](https://developers.google.com/search/docs/appearance/site-names?hl=fr), je pourrais écrire:


```
{
    "@context": "http://schema.org",
    "@type": "WebSite",
    "name": "Nicolas Friedli",
    "url": "https://nicolasfriedli.ch/"
}
```

### Auteur du site

Comme c’est un site personnel, il me paraît intéressant d’en dire plus sur l’auteur. Je pourrais écrire:

```
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
```

Donc, nous avons désormais 2 ensembles JSON. Le premier a un seul niveau, le second est plus structuré (champ `address`).

### Structure simple

Mais ce qui est vraiment intéressant, c’est de lier la notion d’auteur au site. Comme le nom du site est le même que le nom de l’auteur, je prends un autre exemple pour ce passage. Voici ce qui se trouve en page d’accueil de l’[annuaire protestant theologique.ch](https://theologique.ch/) (version simplifiée):

```
{
    "@context": "http://schema.org",
    "@type": "WebSite",
    "name": "Annuaire protestant",
    "alternateName": "theologique.ch",
    "url": "https://theologique.ch/",
    "author": {
        "@context": "https://schema.org",
        "@type": "Person",
        "name": "Nicolas Friedli",
        "url": "https://nicolasfriedli.ch/"
    }
}
```

En français: 

> Ce site s’appelle «Annuaire protestant», et aussi «theologique.ch». Il est disponible à l’adresse `https://theologique.ch/`. Il a pour auteur Nicolas Friedli, celui du site `https://nicolasfriedli.ch/`.

C’est clair, non?


### Schéma complet

Pour mon blog, j’ai essayé de créer un JSON un peu plus complet:

```
{
    "@context": "http://schema.org",
    "@type": "WebSite",
    "name": "Nicolas Friedli",
    "alternateName": "NF",
    "description": "Consultant web à Neuchâtel (Suisse).",
    "url": "https://nicolasfriedli.ch/",
    "image": "/images/nicolas-friedli.jpg",
    "author": {
        "@context": "https://schema.org",
        "@type": "Person",
        "name": "Nicolas Friedli",
        "alternateName": "NF",
        "givenName": "Nicolas",
        "familyName": "Friedli",
        "jobTitle": "Consultant web",
        "address": {
            "@type": "PostalAddress",
            "streetAddress": "Rue du Château 3",
            "postalCode": "2013",
            "addressLocality": "Colombier",
            "addressRegion": "Neuchâtel",
            "addressCountry": "CH"
        },
        "email": "hello@nicolasfriedli.ch",
        "image": "/images/nicolas-friedli.jpg",
        "telephone": [
            "+41328414874",
            "+41793443382"
        ],
        "spouse": {
            "@context": "https://schema.org",
            "@type": "Person",
            "name": "Diane Friedli",
            "url": "https://dianefriedli.ch/"
        },
        "url": "https://nicolasfriedli.ch/",
        "sameAs": [
            "https://github.com/nfriedli/",
            "https://keybase.io/nicolasfriedli",
            "https://www.facebook.com/frdl.ch/"
        ],
        "nationality": "Suisse",
        "alumniOf": {
            "@type": "CollegeOrUniversity",
            "name": "Université de Neuchâtel"
        }
    }
}
```

L’interprétation du contenu devrait être simple. Donc je ne commente pas en détail, mais signale que l’URL du site est la même que celle de l’auteur. Ce balisage est conforme à Schema.org, même il est rarement utilisé ainsi.

### Intégration statique dans Hugo

Pour intégrer cela dans Hugo, c’est trivial, parce que ces données sont statiques. Un fichier `schema.json` est placé dans le répertoire `/data/`. Il est accessible par la variable `site.Data.schema`.

Donc, pour ne l’afficher que sur la page d’accueil, ce sera quelque chose comme:

```
{{ if .IsHome }}
    <script type="application/ld+json">
        {{ site.Data.schema }}
    </script>
{{ end }}
```

Tous les détails sont toujours disponibles dans les [sources du site sur GitHub](https://github.com/nfriedli/nicolasfriedli.ch/).


## Pour les billets de blog

Pour les billets de blog, je souhaite donner quelques informations aux moteurs de recherche:

- distinguer clairement la date de publication de la date de dernière modification (non trivial en HTML)
- donner le titre du billet, pour éviter l’ambiguïté entre `h1`et `title`
- signifier que le contenu est gratuit
- compter le nombre de mots

### Structure du JSON-LD

Voici comment je le formule avec les variables Hugo:

```
{
    "@context": "https://schema.org",
    "@type": "BlogPosting",
    "headline": "{{ .Title }}",
    "wordCount": "{{ .WordCount }}",
    {{ with .PublishDate }}
        "datePublished": "{{ .Format "2006-01-02" }}",
    {{ end }}
    {{ with .Lastmod }}
    "dateModified": "{{ .Format "2006-01-02" }}",
    {{ end }}
    "author": [{
        "@type": "Person",
        "name": "Nicolas Friedli",
        "url": "https://nicolasfriedli.ch/"
    }],
    "isAccessibleForFree": true
}
```

La version courante est elle aussi toujours disponible dans les sources.

### Intégration dynamique dans Hugo

Pour l’intégrer dans Hugo, vu que c’est quelque chose de dynamique, je déclare un bloc sur toutes les pages du site, mais le laisse vide par défaut:

  ```
  {{ block "json-ld" . }}{{ end }}
  ```

Puis, uniquement pour les articles de blog, je redéfinis (ou surcharge) le bloc dans le modèle `blog/single.html`:

```
{{ define "json-ld" }}
<script type="application/ld+json">
{
    "@context": "https://schema.org",
    "@type": "BlogPosting",
    ...
}
</script>
{{ end }}
```

L’existence du bloc `json-ld` sur toutes les pages permettrait d’injecter d’autres données à d’autres endroits du site.

## Construction à la main 

En passant la page d’accueil ou un billet de blog de ce site dans le [validateur Schema.org](https://validator.schema.org/), les données structurées sont rendues lisibles. Elles me semblent suffisantes. Il reste à voir comment elles seront prises en compte par les moteurs de recherche dans la durée.

En construisant ces schémas à la main, j’ai pu me rendre compte du potentiel de Schema.org pour documenter autre chose que des billets de blog. C’est ce que j’ai utilisé sur le site *Églises ouvertes en Suisse romande*. En exemple, les [données structurées du temple de Colombier](https://validator.schema.org/#url=https%3A%2F%2Feglises-ouvertes.ch%2Fneuchatel%2Fcolombier%2F).

Beaucoup de sites utilisent JSON-LD, souvent en excès (et dans le dos des propriétaires). Je suis très réservé par la quantité astronomique de données structurées que propose l’extension de référencement Yoast SEO. C’est un peu comme si le site était réécrit 2 fois sur chacune de ses pages.

Si je vois bien l’intérêt de la chose pour un site commercial ou tout site qui cherche à [modifier l’apparence des résultats de recherche](https://developers.google.com/search/docs/appearance/structured-data/search-gallery?hl=fr) pour être plus visible, je pense que c’est inutile pour un blog ou un simple site personnel.
