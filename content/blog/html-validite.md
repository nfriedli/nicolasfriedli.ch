---
title: Triple validation du code HTML
description: 
date: 2025-01-08
draft: true
---

## Code correctement formé

Imbrication incorrecte des balises:

```
<strong><em>code invalide</strong></em>
```

Alors que la version correcte serait:

```
<strong><em>code valide</em></strong>
```

Tim Berners-Lee, en 1998, dans les [Principles of Design](https://www.w3.org/DesignIssues/Principles.html):

> Be liberal in what you require but conservative in what you do.

En traduction très libre:

> Soyez tolérant·e· dans ce qui vous exigez (pour fonctionner), mais soyez strict·e dans ce que vous faites!

Retrouvez quelques bonnes lectures dans [Lire et relire les classiques du web]({{% relref "lire-classiques-web" %}})!

Tolérance bievenue, mais

Les éditeurs comme celui de WordPress ou le Markdown sont plutôt bons.

## Respect de la DTD

La DTD (document type definition) exprime les règles de grammaire du document.

Utilisation de balises dans certains contextes seulement:

```
<h2><p>Texte</p></h2>
```

Règles de structure hiérarchique de la page:

```
<h1>Titre de la page</h1>
<p>Texte introductif...</p>
<h3>Intertitre fautif</h3>
<p>Suite du texte...</p>
```

Tolérance bienvenue, mais

Pour reprendre Tim Berners-Lee:

> Le principe de tolérance n’est pas une excuse pour contrevenir aux normes.

Les éditeurs comme celui de WordPress ou le Markdown sont moyens, mais des outils existent.

## Validité sémantique

Premier exemple douteux:

```
<strong><em>code valide</em></strong>
```

Parce que `strong` signifie «forte mise en évidence» alors que `em` signifie «mise en évidence».

Mais rien ne dit que `strong` soit être **gras**, respectivement que `em` soit de l’*italique*.

Mais c’est du raffinement.

En revanche, c’est différent pour les listes à puces.
Un liste, c’est

- liste
- à
- puces

```
<ul>
    <li>liste</li>
    <li>à</li>
    <li>puces</li>
</ul>
```

1. liste
1. avec
1. étapes

```
<ol>
    <li>liste</li>
    <li>avec</li>
    <li>étapes</li>
</ol>
```

lignes  
avec  
sauts

```
<p>
    lignes<br>
    avec<br>
    sauts
</p>
```

Les éditeurs comme celui de WordPress ou le Markdown ne valident rien!

Tolérance bienvenue, mais...

Parfois simplement incompréhensible. A11Y, etc.

----

En principe, cette page est valide dans les 3 sens du terme.
