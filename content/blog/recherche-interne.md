---
title: Recherche interne avec Google
description: Proposer une recherche propre à son site en utilisant la puissance de Google. 4 lignes de codes suffisent. Ce n’est pas parfait, mais c’est efficace.
date: 2025-10-20
lastMod: 2025-10-23
categories:
- recherche
---

J’ai testé un système de recherche statique.
J’en parle dans [Recherche statique performante avec PageFind](/blog/recherche-statique-pagefind/).
En fin de billet, je posais 2 questions sur la qualité des réponses et son utilisation par les internautes.
J’ai les réponses:

- la recherche est très peu utilisée (ce qui m’a incité à ne pas maintenir les outils nécessaires)
- les résultats ne sont pas toujours bons (notamment pour des mots avec accentuation)

J’ai donc abandonné ce système pour ce site.
Et je me contente de proposer un formulaire de recherche qui utilise un moteur externe.

## Rercherche Google sur nicolasfriedli.ch

Quand vous utilisez ce moteur de recherche, vous arrivez chez Google.
Si vous souhaitez absolument éviter ce géant du web, n’utilisez pas ce formulaire!

{{< search >}}

Désormais, c’est cette recherche qui est accessible de chaque page du site via le menu.

## Pourquoi une recherche externe

J’utilise un générateur de site statique (Hugo).
Ce qui signifie qu’il ne dispose pas par défaut de toute l’artillerie nécessaire.
C’est un choix parfaitement assumé.

Bien entendu, on peut développer quelque chose de spécifique.
C’est ce que j’ai fait pour [Trouver ma paroisse](https://ma-paroisse.ch/) par exemple, avec [Fuse.js](https://www.fusejs.io/).
Et c’est ce que j’ai tenté ici avec PageFind sans en trouver satisfaction.

Je souhaite quelque chose de simple à mettre en œuvre pour nicolasfriedli.ch.
Je ne souhaite pas dépender d’outils autres qu’Hugo pour compiler le site.
C’est pourquoi je me repose sur Google.
Ce qui signifie:

- qu’il faut que les pages soient indexées pour être trouvables
- qu’il faut éviter de garder dans l’index des pages qui n’existent plus

Cette double contrainte me pousse à gérer l’indexation du site dans [Google Search Console](https://search.google.com/search-console/about).
Et c’est très bien ainsi.
Ainsi, je profite des performances de Google, dont la recherche a été le métier, en 4 lignes de code.

## Code

Cette méthode est en principe utilisable sur tout site, statique comme dynamique.
N’hésitez pas à réutiliser ces lignes en n’oubliant pas de préciser votre nom de domaine (il faut remplacer `nicolasfriedli.ch`).

```
<form method="get" id="search-google" action="https://www.google.com/search" target="_blank">
    <input type="hidden" name="sitesearch" value="nicolasfriedli.ch">
    <input type="text" name="q" maxlength="255" value="" placeholder="Recherche Google" class="form-control">
</form>
```

Dans WordPress, cela fonctionne très bien en insérant le code dans un article, une page ou un *widget*.
Il faut choisir un bloc HTML et éviter de copier le code comme texte.

## Recherches avancées

Pour aller plus loin dans vos recherche, sur n’importe quel site indexé dans Google, je vous invite à consulter mon billet sur les recherches avancées proposé en bas de page.

C’est très utile quand le moteur de recherche interne est défaillant, quand il gère mal les coquilles (*fuzzy search*) ou quand on veut affiner son travail.
Vous remarquerez que la recherche qui a lieu en utilisant le formulaire de cette page utilise tout simplement le motif `+nicolasfriedli.ch`.

Le même type de requête est possible avec d’autres moteurs, mais leur indexation n’est, hélas, pas toujours aussi bonne que celle de Google.
Je concède que si j’optimise mon indexation chez l’ogre de la recherche, c’est aussi un peu de ma faute.
Mais je reste pragmatique, à défaut d’être complètement cohérent.
