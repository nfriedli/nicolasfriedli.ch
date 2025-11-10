---
title: Données structurées pour un site personnel
description: Schema.org et JSON-LD pour aider les moteurs de recherche à comprendre le statut de son site et améliorer la compréhension des billets de blog.
aliases:
- /blog/json-ld-blog/
---

Les données structurées permettent de simplifier le travail des moteurs de recherche et d’améliorer la précision des informations fournies.
Après quelques généralités, je vous dis ce que j’ai implémenté sur ce site généré avec Hugo.

## JSON for Linking Data et Schema.org

JSON-LD (JSON for Linking Data) est un format recommandé pour intégrer des données structurées dans une page HTML.
Comme son nom l’indique, il utilise la syntaxe JSON (JavaScript Object Notation) répandue dans le domaine du web.

En HTML, des métadonnées existent déjà, mais elles sont des balises simples, sans structure.
Par exemple:

```
<meta name="author" content="Nicolas Friedli">
```

Mais qui est ce «Nicolas Friedli»? Impossible d’en dire plus avec les métadonnées habituelles.
[JSON-LD](https://json-ld.org/) permet de structurer les données et propose une *grammaire*.

[Schema.org](https://schema.org/) — une initiative commune de Google, Microsoft, Yahoo et Yandex — développe un *vocabulaire* pour remplir ces champs JSON.
Tout l’enjeu désormais, c’est de donner des informations utiles, ni trop ni trop peu.

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

Comme c’est un site personnel, il me paraît intéressant d’en dire plus sur l’auteur.
Je pourrais écrire:

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

Donc, nous avons désormais 2 ensembles JSON.
Le premier n’a qu’un seul niveau, le second est plus structuré (champ `address`).

### Structure simple

Mais ce qui est vraiment intéressant, c’est de lier la notion d’auteur au site.
Comme le nom du site est le même que le nom de l’auteur, je prends un autre exemple pour ce passage.
Voici ce qui se trouvait en page d’accueil du défunt theologique.ch (version simplifiée):

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

> Ce site s’appelle «Annuaire protestant», et aussi «theologique.ch».
Il est disponible à l’adresse `https://theologique.ch/`.
Il a pour auteur Nicolas Friedli, celui du site `https://nicolasfriedli.ch/`.

C’est clair, non?

### Schéma complet

Pour mon site personnel, j’ai essayé de créer un JSON un peu plus complet:

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
            "https://frdl.ch/",
            "https://github.com/nfriedli/"
        ],
        "nationality": "Suisse",
        "alumniOf": {
            "@type": "CollegeOrUniversity",
            "name": "Université de Neuchâtel"
        }
    }
}
```

L’interprétation du contenu devrait être simple.
Donc je ne commente pas en détail, mais signale que l’URL du site est la même que celle de l’auteur.
Ce balisage est conforme à Schema.org, même il est rarement utilisé ainsi.

### Intégration statique

Ce code est très simple à utiliser avec un site généré à la main, un générateur de site statique ou un CMS qui donne accès au code.
Dans un WordPress, un bloc HTML dans le texte de la page d’acceuil ou un widget en HTML font très bien le boulot.

Pour l’intégrer dans Hugo, c’est trivial, parce que ces données sont statiques.
Un fichier `schema.json` est placé dans le répertoire `/data/`.
Il est accessible par la variable `site.Data.schema`.

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

Pour les billets de blog, on peut donner quelques informations aux moteurs de recherche:

- distinguer clairement la date de publication de la date de dernière modification (non trivial en HTML)
- donner le titre du billet, pour éviter l’ambiguïté entre `h1` et `title`
- signifier que le contenu est gratuit
- compter le nombre de mots

### Structure du JSON-LD

Des données structurées minimales, ici écrites avec des variables Hugo (mais le principe est toujours le même):

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

Pour l’intégration, c’est un peu plus compliqué parce que dynamique.
Comme ce n’est pas le sujet de ce billet, je ne développe pas.

## Construction à la main

En passant la page d’accueil ou un billet de blog de ce site dans le [validateur Schema.org](https://validator.schema.org/), les données structurées sont rendues lisibles.
Elles me semblent suffisantes.
Il reste à voir comment elles seront prises en compte par les moteurs de recherche dans la durée.

En construisant ces schémas à la main, j’ai pu me rendre compte du potentiel de Schema.org pour documenter autre chose que des billets de blog.

Beaucoup de sites utilisent JSON-LD, souvent en excès (et dans le dos des propriétaires).
Je suis très réservé par la quantité astronomique de données structurées que propose l’extension de référencement Yoast SEO.
C’est un peu comme si le site était écrit 2 fois sur chacune de ses pages.

Si je vois bien l’intérêt de la chose pour un site commercial ou tout site qui cherche à [modifier l’apparence des résultats de recherche](https://developers.google.com/search/docs/appearance/structured-data/search-gallery?hl=fr) pour être plus visible, je pense que c’est inutile pour un blog ou un simple site personnel.
