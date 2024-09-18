---
title: Remarques sur le protocole Gemini
description: 
date: 2024-09-18
draft: true
---

## Première approche... avec des erreurs!


```
 d888b  d88888b .88b  d88. d888888b d8b   db d888888b 
88' Y8b 88'     88'YbdP`88   `88'   888o  88   `88'   
88      88ooooo 88  88  88    88    88V8o 88    88    
88  ooo 88~~~~~ 88  88  88    88    88 V8o88    88    
88. ~8~ 88.     88  88  88   .88.   88  V888   .88.   
 Y888P  Y88888P YP  YP  YP Y888888P VP   V8P Y888888P 

```

## Présentation de Gemini

gemini://geminiprotocol.net/docs/specification.gmi

https://geminiprotocol.net/docs/specification.gmi

### Un protocole

[Le protocole Gemini, revenir à du simple et sûr pour distribuer l'information en ligne?](https://www.bortzmeyer.org/gemini.html)

[Gemini, le protocole du slow web](https://ploum.net/gemini-le-protocole-du-slow-web/index.html)

[La fin d’un blog et la dernière version de ploum.net](https://ploum.net/2022-12-04-fin-du-blog-et-derniere-version.html)

### Une syntaxe


[CommonMark](https://commonmark.org/)

[apprendre Markdown](https://commonmark.org/help/tutorial/)

En gros, ce qui est conservé de Markdown:

- des paragraphes
- des listes à puces (non imbriquées)
- des titres (3 niveaux)
- des liens (seuls sur une ligne)
- du texte préformaté

## Ce que je retiens de Gemini

Limitations fortes contre le délire du web.

Simplicité de mise en œuvre: serveur

Le navigateur graphique produit des pages belles et lisibles.

[Lagrange](https://gmi.skyjake.fi/lagrange/)

Tout est dans la page (et rien d'autre) y c. pas de métadatas (p.ex. date, auteur)

Absence d'images++

1 page = 1 chargement (un peu comme celle-ci...)

## Pourquoi Gemini ne me convient pas

Nombreux projets non maintenus

Pas de métadata

Qui l'utilise?

Vraiment plus performant? vraiment plus sûr?

[The Gemini protocol seen by this HTTP client person](https://daniel.haxx.se/blog/2023/05/28/the-gemini-protocol-seen-by-this-http-client-person/) par Daniel Stenberg.

Auteur de [curl://](https://curl.se/), un des logiciels les plus uitilisés au monde (plus de 20 milliards d'installations...).
Il fonctionne sur votre ordinateur, votre téléphone, votre télévision, etc.

## Ce qui m'interpelle

Liens sur une seule ligne, voire liens visibles.
Je trouve ceci très bien:

[{{< relref "contact" >}}]({{< relref "contact" >}})

Ou, mieux encore:

[{{< ref "contact" >}}]({{< ref "contact" >}})

Ou, pourquoi pas:

[Me contacter]({{< relref "contact" >}})

Absence de moteur de recherche, monde parallèle intéressant