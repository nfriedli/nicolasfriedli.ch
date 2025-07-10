---
title: Site web écoconçu (ou pas) pour l’UNIL
description: L’Université de Lausanne présente son site comme écoconçu. Pourtant, sa version prétendument écologique consomme plus de ressources que sa version «normale». Le discours ne fait pas du bon web, une fois de plus.
date: 2025-07-10
categories:
- performance
- eco
---

L’Université de Lausanne (UNIL) a lancé son nouveau site il y a quelques mois.
En consultant la [page d’accueil de la Faculté de théologie et de sciences de religions](https://www.unil.ch/ftsr/fr/home.html), je prends le temps de regarder les nouveautés sérieusement.

## Le discours

Et là, surprise, une fenêtre surgit (pop-up) et me parle d’images écoresponsables.
Je peux *Continuer en mode éco* ou *Afficher les images sans compression*.
Je peux aussi lire plein de verbiage sur la page [Navigation durable](https://www.unil.ch/unil/fr/home/termes/conditions/navigation-durable.html).

Quand un site se prétend éco-truc ou éco-machin, il vaut toujours la peine de vérifier la cohérence entre le discours et les actes.
J’avais écrit quelques lignes sur ce sujet dans [Écologie et cohérence sur le web]({{% relref "ecologie-coherence" %}}).
Le discours est bien là, dans le communiqué [Le site internet de l’UNIL fait peau neuve](https://www.unil.ch/news/fr/1732014278676): «volonté affichée de sobriété», «écoresponsable», «durable», «sobre», etc.
Il y en a tellement que c’est suspect.

## Les faits

Dans le [Website Carbon Calculator](https://www.websitecarbon.com/website/unil-ch-ftsr-fr-home-html/), le bilan est moyen.
Chez [Ecograder](https://ecograder.com/report/pI19izXBKOrB3ZkKS5SLqZqr), ce n’est pas bon non plus.

Chez [PageSpeed Insights](https://pagespeed.web.dev/analysis/https-www-unil-ch-ftsr-fr-home-html/u3xlnlntv8?form_factor=mobile), ce n’est pas plus glorieux.
Plusieurs problèmes concernent directement la problématique de ce billet, notamment:

- la mauvaise gestion du cache (des fichier sont rechargés trop souvent)
- des images sont peu optimisées

**En fait, c’est catastrophique: 2 versions de chaque image sont chargées simultanément!**
L’image est chargée en version lourde (sans être affichée) et version légère (qui est affichée).
Quel gâchis!
**Au final, la version avec les images non comprimées (qui n’est soi-disant pas éco-machin-chose) est plus légère (1682ko) que la version éco-truc (2448ko)!**

En conclusion, si vous voulez faire un geste écologique, choisissez l’option *Afficher les images sans compression*!
Le discours, aussi dithyrambique soit-il, ne fait pas le site.
Ici, ce n’est pas écologique, c’est 100% *bullshit*.

## Remarques sur les images

Le sujet a été brillament expliqué par HTeuMeuLeu dans [Éco-conception et dithering](https://www.hteumeuleu.fr/eco-conception-et-dithering/).
Je ne reviens pas sur son billet mais cite sa conclusion («dithering» signifie «tramage»):

> C’est moche, hein?
> Mais c’est peut-être justement le signe que cette image n’est pas utile en premier lieu.
> Et peut-être que la vraie éco-conception, ce sont les images qu’on abandonne en chemin.
>
> Moralité: si on vous a vendu du dithering en guise d’éco-conception mais que vos images sont aussi lourdes que des JPG bien compressés, alors... votre tramage se rapporte à votre plumage.

Pour illustrer le propose avec le site de l’UNIL, sur la page d’accueil théologique citée précédemment (les images sont sauvegardées en la Wayback Machine au besoin):

- l’[image «éco»](https://api.unil.ch/newsunil/v1/api-newsunil/resources/image/1746635380490.M?2025-05-13T08:42:32.409&eco=true) pèse 86ko
- l’[image «normale»](https://api.unil.ch/newsunil/v1/api-newsunil/resources/image/1746635380490.M?2025-05-13T08:42:32.409) pèse 193ko
- le site qui se dit écoconçu charge les 2 images, donc environ 280ko

Le vrai probème, c’est que l’image «normale», passée dans [Squoosh](https://squoosh.app/) (gratuit):

- pèse 65ko en JPEG (options par défaut), donc 3 fois moins que la «normale» du site de l’UNIL... est moins que l’image «éco»
- pèse 43ko en AVIF (qui n’est pas compatible partout, certes)
- pourrait peser 10ko ou 20ko si elle était en PNG vraiment bien fait

Le plus simple, ce serait donc d’arrêter de nous prendre pour des idiot·e·s, de ne pas nous envoyer un *pop-up* de bonne conscience et d’utiliser une seule image JPEG ou WebP bien optimisée.

Ou alors de réfléchir sérieusement à l’utilisation (ou la non utilisation) des images.
Ce n’est pas impossible pour une institution, comme le prouve brillamment le [site gouvernemental GOV.UK](https://www.gov.uk/).

Un conseil quand même, quand on décide d’utiliser du PNG tramé:

- utiliser une image plus petite (en pixels) que sa taille finale à l’écran
- puis l’agrandir artificiellement

Le truc magique, en CSS, c’est quelque chose comme:

```
img.dither {
    width: 100%;
    height: auto;
    image-rendering: pixelated; /* c’est l’astuce qui va bien */
}
```

## Conclusion

Il me paraît plus important que jamais de **s’appuyer sur des mesures fiables plutôt que sur ce que l’on voit**.
On ne déclare pas un site web accessible.
On ne déclare pas un site rapide.
On ne déclare pas un site écologique.

J’ai l’impression que [Low-tech Magazine](https://solar.lowtechmagazine.com/), avec ses images tramées, a faussé plein de choses en partant d’une bonne intention (et de bonnes pratiques).
Aujourd’hui, on croit que copier (visuellement) des idées de ce site, c’est être écoresponsable.
Eh bien non!

Comme le site de l’UNIL est en ligne depuis un moment, je pense que ce ne sont plus des erreurs de déploiement (qui arrivent toujours).
C’est plus grave.
Nous sommes dans un monde où le verbiage suffit à convaincre et se convaincre de son excellence.
C’est triste.

En attendant de faire les choses mieux, on continue à consommer beaucoup trop de bande passante...
