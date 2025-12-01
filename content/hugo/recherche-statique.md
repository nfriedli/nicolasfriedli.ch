---
title: Recherche sur un site statique
description: PageFind, DuckDuckGo, Google ou Fuse.js permettent de proposer des excellents recherches sur les sites statiques (générés avec Hugo ou non).
date: 2025-12-01
---

La recherche sur son site (statique ou non) est bienvenue.
Pourtant, avec les sites statiques, ce n’est pas toujours évident.

La règle [Opquast 168](https://checklists.opquast.com/fr/qualite-numerique/le-site-propose-un-moteur-de-recherche-interne) est claire:

> Un moteur de recherche interne est proposé.
>
> Le moteur de recherche est, avec le plan du site, les menus et le lien de retour à l’accueil, un des moyens fondamentaux de réorientation et d’accès à l’information.
> Rendez-le présent et facile d’accès.

Il est possible de s’en passer et de se reposer sur les compétences des internautes, qui se formeront en lisant [Recherches Google avancées](/pratique/recherche-google-avancee/) (qui fonctionne avec d’autres moteurs de recherche).
Mais ce n’est qu’un palliatif.

## Recherche intégrée disponible

Un certain nombre de générateurs de sites statiques (SSG) proposent une recherche par défaut.
C’est le cas, par exemple, de:

- [MkDocs](https://www.mkdocs.org/) (peu mis à jour)
- [Zensical](https://zensical.org/) (remplaçant de *Material for MkDocs*)
- [Sphinx](https://www.sphinx-doc.org/en/master/)
- [Zola](https://www.getzola.org/)

Hugo, qui motorise ce site, ne propose pas de recherche interne.
Mais des solutions simples existent.

## PageFind

La solution la plus simple aujourd’hui, c’est [PageFind](https://pagefind.app/).

Il suffit d’inclure un code (en *partial* ou en *shortcode* avec Hugo):

```
<link href="/pagefind/pagefind-ui.css" rel="stylesheet">
<script src="/pagefind/pagefind-ui.js"></script>
<div id="search"></div>
<script>
    window.addEventListener("DOMContentLoaded", (event) => {
        new PagefindUI({ 
          element: "#search", 
          showSubResults: true 
          });
    });
</script>
```

Puis de générer tout le nécessaire *après* la compilation:

```
hugo && npx -y pagefind --site public

```

PageFind fonctionne plutôt bien, mais n’est pas parfait.
**Ce que je lui reproche, c’est de nécessiter Node.js.**
Si le SSG utilisé repose déjà sur cet outil (c’est le cas d’[Eleventy](https://www.11ty.dev/)), pourquoi pas.
Avec Hugo, on perd beaucoup en simplicité.

C’est toutefois une solution que j’ai utilisée un certain temps, mais j’ai renoncé à la maintenir au vu du très faible nombre de recherches.

## DuckDuckGo et Google

Aujourd’hui, **ce site s’appuie sur la recherche externe par DuckDuckGo**.
Elle est disponible en bas de chaque page.
Il me suffit d’un *shortcode* quelques lignes ([4 lignes dans mon code en production](https://github.com/nfriedli/nicolasfriedli.ch/blob/main/layouts/_shortcodes/search.html)) pour faire le boulot:

```
<form 
  method="get" 
  id="duckduckgo" 
  action="https://duckduckgo.com/" 
  target="_blank">
    <input 
      type="hidden" 
      name="sites" 
      value="nicolasfriedli.ch">
    <input 
      type="text" 
      name="q" 
      maxlength="255" 
      value="" 
      placeholder="Recherche" 
      autofocus
      required>
</form>
```

La recherche est lancée dans une nouvelle page, uniquement sur un nom de domaine précis (`site:nicolasfriedli.ch`).
C’est simple, , c’est rapide, ça ne demande aucune maintenance et ça fonctionne parfaitement.
La limitation, c’est qu’**il faut que vos pages soient indexées dans DuckDuckGo**.
Cette méthode peut donc être limitative s’il faut obtenir des résultats très rapidement après la mise en ligne d’une nouvelle page.

La même stratégie peut être utilisée avec Google:

```
<form 
  method="get"
  id="search-google"
  action="https://www.google.com/search"
  target="_blank">
    <input
      type="hidden"
      name="sitesearch"
      value="nicolasfriedli.ch">
    <input 
      type="text"
      name="q"
      maxlength="255"
      value=""
      placeholder="Recherche Google"
      autofocus 
      required>
</form>
```

La limitation concernant l’indexation est identique.
Le problème, c’est que **Google respecte très mal la vie privée**.
Dans ce cas, il est important de signaler avant la recherche qu’elle sera effectuée par Google.

## Recherche sur mesure (avec `fuse.js`)

Avec un site statique, il est aussi possible de créer une recherche sur mesure, avec ses forces et ses limites.

Pour [Trouver ma paroisse](https://ma-paroisse.ch/), j’ai développé une recherche très spécifique en utilisant [Fuse.js](https://www.fusejs.io/).
Elle est tolérante aux fautes de frappe ou aux coquilles orthographiques (*fuzzy search*).
Elle met un accent particulier sur les numéros postaux (NPA).
Et elle permet de trouver certaines pages avec des noms de personnes qui ne sont même pas visibles sur les pages de résultats.

Ce genre de recherche exige l’utilisation d’un fichier JSON qui fait office de base de données.
Pour un petit site, c’est parfait.
Pour un grand site, PageFind est un meilleur choix.

Zachary Betz donne propose un [exemple complet de recherche avec Fuse.js](https://github.com/zwbetz-gh/hugo-client-side-search-template) plus généraliste que celui de *Trouver ma paroisse*.

## Algolia

Des sites statiques utilisent l’outil externe [Algolia](https://www.algolia.com/fr).
Les résultats sont excellents.
Il est très performant sur des sites grands ou complexes.

Mais je ne souhaite pas utiliser ce genre d’outil payant pour un site comme le mien.
Et je reste sceptique sur l’accent mis sur l’intelligence artificielle.

----

Les méthodes externes comme DuckDuckGo et Google sont utilisables à l’identique sur un site dynamique.
Avec WordPress, il suffit d’un *widget* en HTML pour proposer mieux que le moteur de recherche par défaut.
