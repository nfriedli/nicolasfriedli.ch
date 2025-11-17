---
title: Optimisation efficace d’images et dithering
description: Les images tramées (dithering) sont à la mode. Souvent présentées comme écologiques, elle sont parfois plus lourdes que de simples fichiers JPG bien optimisés.
images:
- /images/dithering-8.jpg
---

De plus en plus de site utilisent des images tramées en se prétendant écoresponsables.
Elles utilisent la technique du *dithering* (ou diffusion d’erreur).
Dans la majorité des cas, c’est du pur bullshit.
Le discours, aussi dithyrambique soit-il, ne fait pas un site écologique.

À moins de prendre quantité de précautions, **une image pixelisée en PNG sera presque toujours plus lourde qu’un simple fichier JPG**.

Ce billet n’invente rien.
Le sujet a déjà été bien documenté par HTeuMeuLeu dans [Éco-conception et dithering](https://www.hteumeuleu.fr/eco-conception-et-dithering/), qu’il vaut la peine de lire et dont il vaut la peine de citer la conclusion:

> Moralité: si on vous a vendu du dithering en guise d’éco-conception mais que vos images sont aussi lourdes que des JPG bien compressés, alors... votre tramage se rapporte à votre plumage.

Pour voir les images en taille réelle, il faut utiliser une option comme «Ouvrir l’image dans un nouvel onglet».
Cette page devrait être vue sur un écran d’ordinateur plutôt que celui d’un téléphone pour bien visualiser les différences (parfois ténues).

Elle ne peut pas obtenir les meilleurs résultats de performance parce qu’elle présente certaines images volontairement mal «optimisées».

## Images en JPG

Comme exemple, une image libre qui fait «jardin numérique aux Pays-Bas», trouvée chez Pixabay:

{{< figure
  src="/images/dithering-1.jpg"
  alt="Image originale de Pixabay en JPG"
  width=1280
  height=853
  caption="Image originale de Pixabay, en JPG, 1280X853px, 221Ko."
>}}

L’image passe dans [Squoosh](https://squoosh.app/), sans paramètres particuliers.
Elle est 2 fois plus légère, sans différences notables:

{{< figure
  src="/images/dithering-2.jpg"
  alt="Image optimisée avec Squoosh en JPG"
  width=1280
  height=853
  caption="Image optimisée avec Squoosh, en JPG, 1280X853px, 104Ko."
  loading="lazy"
>}}

## Nouveaux formats d’image (WebP et AVIF)

Toujours dans Squoosh, toujours sans paramètres particuliers, elle est transformée en WebP (qui fonctionne partout), elle perd encore 40% de sa taille:

{{< figure
  src="/images/dithering-3.webp"
  alt="Image optimisée avec Squoosh en WebP"
  width=1280
  height=853
  caption="Image optimisée avec Squoosh, en WebP, 1280X853px, 67Ko."
  loading="lazy"
>}}

Puis en AVIF (dont le support dans les navigateurs est moins bon), et encore un gros rabais sur la quantité de données transférées:

{{< figure
  src="/images/dithering-4.avif"
  alt="Image optimisée avec Squoosh en AVIF"
  width=1280
  height=853
  caption="Image optimisée avec Squoosh, en AVIF, 1280X853px, 37Ko."
  loading="lazy"
>}}

## Images en PNG

Comme les images «branchées et (prétendument) écoresponsables» sont en PNG, notre image de départ est transformée dans Squoosh avec les valeurs par défaut:

{{< figure
  src="/images/dithering-5.png"
  alt="Image «optimisée» avec Squoosh en PNG"
  width=1280
  height=853
  caption="Image «optimisée» avec Squoosh, en PNG, 1280X853px, 1.3Mo."
  loading="lazy"
>}}

Puis le nombre de couleur est réduit et elle est 8 fois plus légère que la précédente.
Mais elle reste plus lourde que le JPG (optimisé), le WebP et l’AVIF.
C’est le problème.
Par contre, elle a un «style» (et pourrait faire illusion):

{{< figure
  src="/images/dithering-6.png"
  alt="Image «optimisée» avec Squoosh en PNG 8 couleurs"
  width=1280
  height=853
  caption="Image «optimisée» avec Squoosh, en PNG, 8 couleurs 1280X853px, 152Ko."
  loading="lazy"
>}}

Pour alléger vraiment l’image, elle est cette fois très réduite en taille et passe en 4 couleurs:

{{< figure
  src="/images/dithering-7.png"
  alt="Image optimisée avec Squoosh, réduite et en 4 couleurs"
  width=320
  height=213
  caption="Image optimisée avec Squoosh, en PNG, 4 couleurs 320X213px, 9Ko."
  loading="lazy"
>}}

L’astuce 1, c’est de l’**agrandir artificiellement** dans le navigateur.
Cette image est la même que la précédente, mais forcée à la même largeur alors qu’elle est bien plus petite.
C’est pas mal mais le rendu est un peu flou:

{{< figure
  src="/images/dithering-7.png"
  alt="Image optimisée avec Squoosh, réduite et en 4 couleurs, agrandie artificiellement"
  width=320
  height=213
  caption="Image optimisée avec Squoosh, en PNG, 4 couleurs 320X213px, 9Ko, en largeur forcée à 100%."
  class="full"
  loading="lazy"
>}}

L’astuce 2, c’est de l’agrandir **en forçant sa pixelisation** avec la directive CSS `image-rendering: pixelated`.
Et là, c’est vraiment net:

{{< figure
  src="/images/dithering-7.png"
  alt="Image optimisée avec Squoosh, réduite et en 4 couleurs, agrandie et pixelisée"
  width=320
  height=213
  caption="Image optimisée avec Squoosh, en PNG, 4 couleurs 320X213px, 9Ko, en largeur forcée à 100%, rendu pixelisé."
  class="full pixelated"
  loading="lazy"
>}}

Le problème de toute la démarche, c’est de produire des images assez particulières, qui peuvent paraître «moches» à des internautes.
Mais on se rassurera en sachant que d’autres les trouveront «remarquablement tendance».

## Image optimisée en JPG

Si on souhaite afficher une **belle «image normale» et légère**, rien de tel que **bien choisir sa taille** et de **forcer un peu sa compression**, en simple JPG:

{{< figure
  src="/images/dithering-8.jpg"
  alt="Image optimisée avec Squoosh, de taille décente et bien compressée"
  width=800
  height=533
  caption="Image optimisée avec Squoosh, en JPG, qualité 50, 800X533px, 36Ko."
  class="full"
  loading="lazy"
>}}

Elle fait 36Ko, c’est peu.
Et c’est très bien ainsi.
Le **rendu visuel est suffisant** pour la grande majorité des usages.

## Conclusion

Il est important de **s’appuyer sur des mesures fiables plutôt que sur ce que l’on voit** (et ce que l’on vous dit).
La performance et l’écoconception se mesurent.
On ne déclare pas un site web accessible.
On ne déclare pas un site rapide.
On ne déclare pas un site écologique.

[Low-tech Magazine](https://solar.lowtechmagazine.com/), avec ses images tramées, a faussé plein de choses en partant d’une bonne intention (et alors qu’il faut les choses bien).
Aujourd’hui, on croit que copier (visuellement) des idées de ce site, c’est être écoresponsable.
Eh bien non!

Les images beaucoup trop lourdes ne sont pas de simples accidents.
La maladie est plus grave.
Nous sommes dans un monde où **le verbiage suffit à convaincre et se convaincre de son excellence**.
C’est triste.

En attendant de faire les choses mieux, on consomme beaucoup trop de bande passante.
Le discours se verdit; le discours seulement.

**Ce qui compte**, ce n’est pas le «style écologique», mais le **poids du fichier** et la **justesse de son usage** (utilité réelle, taille, format, compression, chargement différé et politique de cache).
