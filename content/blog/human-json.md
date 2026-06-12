---
title: Suppression de human.json
description: human.json est un protocole léger pour affirmer que des sites sont bien tenus par des personnes et humaniser le web. C’est un outil simple et clair, mais il ne me semble ni pertinent dans la durée, ni utilisé.
date: 2026-06-12
images:
- https://cdn.pixabay.com/photo/2024/04/25/17/36/robot-8720359_1280.jpg
---

`human.json` est un protocole léger pour affirmer que des sites sont bien tenus par des personnes et humaniser le web.
C’est un outil simple et clair, mais il ne me semble ni pertinent dans la durée, ni utilisé.
C’est pourquoi j’ai supprimé `human.json` de ce site.

## Principe

L’idée toute simple, c’est de publier un fichier JSON, par exemple à la racine de son site, avec des informations du type:

```
{
  "version": "0.1.1",
  "url": "https://nicolasfriedli.ch",
  "vouches": [
    {
      "url": "https://frdl.ch",
      "vouched_at": "2026-06-12"
    },
    {
      "url": "https://dianefriedli.ch",
      "vouched_at": "2026-06-12"
    }
  ]
}
```

Avec ce petit fichier, j’affirme ou atteste ou signale que [frdl.ch](https://frdl.ch/) et [dianefriedli.ch](https://dianefriedli.ch/) sont bien des présences humaines sur le web.

En installant une extension de navigateur, disponible pour Firefox et Chrome sur la [page de présentation du protocole](https://codeberg.org/robida/human.json), je sais quels sites sont:

- verts (validés par un site déjà validé)
- jaunes (validées par un site déjà validé via 1 ou 2 autres sites)
- oranges (validés avec 3+ étapes)
- gris (non validés)
- bleus (disposent d’un `human.json` mais pas validés par d’autres)

Le truc est clair et simple, il permet de créer progressivement un réseau de confiance.

## Avantage

L’avantage de ce protocole, c’est sa simplicité de mise en œuvre.
Il suffit d’un fichier JSON et d’un appel dans le code de la page, comme:

```
<link rel="human-json" href="/human.json">
```

Il suffit de voir comment je l’ai supprimé par le [commit 4757986](https://github.com/nfriedli/nicolasfriedli.ch/commit/4757986441e4a8d71a525823f929a1549d4a9fb3) pour comprendre à quel point c’est facile.

La bonne idée, c’est qu’il va plus loin que les liens de type `rel="me"` qui se limite à signaler mes présences sur le web.
Il permet de signifier celles d’autres personnes, sans besoin de le leur demander (bonne ou mauvaise idée?).

## Souci

Mais, parce qu’il y a bien un «mais», je n’ai presque jamais vu de ronds autres que gris dans l’extension de navigateur.
Personne ou presque ne l’utilise.
Je suis donc très réservé à ce qu’il nécessite le développement d’une «application», sa mise à jour, etc. pour quelque chose qui ne trouve pas son public.

Et surtout, je me sens peu à l’aise de signifier la responsabilité humaine de site dont je ne m’occupe pas.
Je n’ai aucune idée de la manière réelle de générer ces sites.
Je ne peux pas m’engager sur les pratiques futures.

## Réponse

**Franchement, la meilleure réponse aux intelligences artificielles (IA) et pour parler de l’«humanité des sites», c’est de continuer à faire des liens contextuels, dans les articles, vers des pages intéressantes.**

En second lieu, c’est de proposer un [blogroll](/blogroll/) de sites que l’on consulte dans la durée et qui nous stimulent.

Toutes les autres solutions ne sont, au final, que des artifices techniques, parfois élégants, rarement efficaces.
Beaucoup suscitent de petit enthousiasme de geeks, peu s’imposent.
Il faut avoir l’honnêteté d’abandonner l’inutile, mais quand c’est simple et léger.
