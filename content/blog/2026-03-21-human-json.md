+++
description = "Le protocole human.json permet de signaler que des contenus sont humains. Il permet aussi d’attester que d’autres sites sont humains. On crée ainsi une «chaîne de confiance»."
title = "Humaniser le web avec human.json"
+++

[Beto Dealmeida](https://robida.net/) vient de proposer le [protocole `human.json`](https://codeberg.org/robida/human.json) pour signaler que les contenus de certains sites sont humains.
L’originalité de la chose, c’est que je peux attester que d’autres sites sont aussi humains.
Je crée ainsi une «chaîne de confiance».
Explication.

Je peux facilement, sur mon site, signaler que je suis un véritable être humain.
Je peux dire aussi que je rédige mes contenus.
Mais toute intelligence artificielle générative (IAg) pourrait faire de même.

La bonne idée de `human.json`, c’est que je peux signaler que d’autres sites sont générés par des vraies personnes dans mon propre fichier.
Je cautionne leur patte humaine.

Ensuite, avec une extension de navigateur (Firefox ou Chrome), je peux lister cette «chaîne de confiance».
Et je peux manuellement donner ma confiance à un site ou la retirer à un autre.

Le truc plutôt sympa, c’est la simplicité de mise en œuvre.
J’ajoute un fichier JSON basique sur mon site, par exemple: [`/human.json`](/human.json).
Puis je signale par une ligne dans mes entêtes HTML l’emplacement du fichier:

```
<link rel="human-json" href="/human.json">
```

C’est tout, ça fonctionne.

Pour le moment, dans le fichier de ce site, j’ai aujouté d’autres de mes sites et celui de ma femme [Diane Friedli](https://dianefriedli.ch/).

Je me verrais bien compléter le liste avec des sites protestants réformés.
Cette démarche compléterait bien ce qui est présenté dans [Sites protestants réformés de Suisse romande](/blog/blogroll/)

**Si vous possédez un site personnel protestant réformé et que vous me connaissez «en vrai», n’hésitez pas à le signaler et je l’ajouterai à ma liste.**
Je vous invite évidemment à ajouter un `human.json` à votre site afin de voir si cette initiative intéressante s’installe dans le paysage.
