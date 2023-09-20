---
title: Adopter une typographie fluide
description: Une typographie fluide permet d’optimiser son texte à toutes les tailles d’écran. Il ne suffit pas de proposer du texte lisible, il faut donner aux internautes du contenu agréable à voir.
date: 2023-05-16
---

Une typographie fluide permet d’optimiser son texte à toutes les tailles d’écran. Il ne suffit pas de proposer du texte lisible, il faut donner aux internautes du contenu agréable à voir.

## Tailles relatives et zoom possible

Une feuille de style CSS bien conçue évite de donner au texte des tailles fixe pour favoriser les tailles relatives. Pour faire simple, la taille principale du texte devrait être celle choisie par le navigateur (par défaut) ou par l’internaute:

```
html {
    font-size: 100%;
}
```

Puis, toutes les autres tailles devraient être calculées de manière relative, par exemple:

```
font-size: 90%      /* 90% du parent */
font-size: 1.5rem   /* 1.5x la taille par défaut */
```

Si tel est le cas, il est possible de changer la taille d’écriture ou de zoomer dans son navigateur. On veillera à respecter la règle [Opquast 188](https://checklists.opquast.com/fr/assurance-qualite-web/le-site-ne-bloque-pas-les-fonctionnalites-de-zoom-du-navigateur):

> Le site ne bloque pas les fonctionnalités de zoom du navigateur.

On ne peut pas encore parler de *typographie fluide*, mais c’est un bon premier pas.

## Version minimale

Pour améliorer la lecture à l’écran, il vaut la peine d’agrandir un peu les écritures lorsque le périphérique est plus grand. Il s’agit notamment d’une question de distance de lecture. Oliver Schöndorfer aborde le sujet dans [What’s the right font size in web design?](https://pimpmytype.com/font-size/) sur son site *Pimp my Type*.

La technique traditionnelle, c’est d’utiliser des conditions, par exemple:

- si l’écran fait moins de 640 pixels de large, l’écriture de base fera 100% (en général 16px par défaut sur un ordinateur, modifiable pour les internautes)
- si l’écran fait entre 640 et 1280 pixels, elle fera 110%
- si sinon elle fera 120%

Il faut utiliser des [media queries](https://developer.mozilla.org/fr/docs/Web/CSS/Media_Queries/Using_media_queries), comme:

```
html { font-size: 100%; }

@media (min-width: 640px) { 
    html { font-size: 110%; } 
}

@media (min-width: 1281px) { 
    html { font-size: 120%; } 
}
```

Désormais, il existe la fonction [clamp](https://developer.mozilla.org/fr/docs/Web/CSS/clamp) qui simplifie tout cela. Par exemple, sur ce site:

```
html {
     clamp(1.00rem,  calc(0.88rem + 0.31vw),  1.13rem) 
}
```

En langue ordinaire: la taille de la police est «proportionnelle» à la largeur de l’écran (au sens strict, c’est ici une fonction affine) et varie en continu (de manière fluide). Mais avec un minimum de 100% et un maximum de 113%.

Donc, si un site est construit avec des valeurs relatives, il suffit d’une ligne de CSS pour rendre sa typo fluide. Il reste la question de cette formule un peu bizarre. Certes plus comptacte que les *media queries*, mais moins intuitive. 

Sur un site simple comme mon blog (une colonne, flux vertical), si toutes les valeurs sont relatives, **faire varier la taille principale de police revient à créer un zoom automatique**. Avec les *media queries*, le «zoom» a des positions prédifinies; avec `clamp`, il est continu.

## Échelle de tailles 

Classiquement, les titres et intertitres se présentent ainsi. Chaque niveau supérieur de 30% plus grand que le précédent:

```
html    { font-size: 100%; }
h1      { font-size: 2.197rem; }
h2      { font-size: 1.69rem; }
h3      { font-size: 1.3rem; }
```

Avec Utopia, on pourrait avoir quelque chose comme:

```
html    { font-size: clamp(1.00rem, calc(0.88rem + 0.31vw), 1.13rem); }
h1      { font-size: clamp(1.73rem, calc(0.79rem + 2.34vw), 2.66rem); }
h2      { font-size: clamp(1.44rem, calc(0.88rem + 1.40vw), 2.00rem); }
h3      { font-size: clamp(1.20rem, calc(0.90rem + 0.75vw), 1.50rem); }
```

La grande différence, c’est que le titre `h1` n’est pas figé à une taille 30% supérieure à `h2`. Quand l’écrant est petit, il est supérieur d’un cinquième; quand l’écran est grand, il est supérieur d’un tiers. Il suffit de redimmensionner la fenêtre du navigateur sur votre ordinateur pour vous en rendre compte.

On reprend l’idée de `clamp` pour la réclaration générale, mais aussi pour les titres et intertitres. Ce qui signifie que l’échelle entre eux varie aussi en fonction de la taille de l’écran.

## Version Utopia complète

Et voici qu’intervient le projet [Utopia](https://utopia.fyi/) de James Gilyead et Trys Mudford. Il change la vie. Il suffit de lui donner:

- la taille en dessous de laquelle un écran est «petit», une taille de police principale pour cette résolution et une échelle pour les titres
- la taille en dessus de laquelle un écran est «grand», une taille de police principale pour cette résolution

Puis Utopia créer toutes les règles CSS avec `clamp` pour faire varier les tailles de manière fluide entre ces deux valeurs. L’article [Designing with fluid type scales](https://utopia.fyi/blog/designing-with-fluid-type-scales) montre graphiquement le fonctionnement de la chose.

C’est donc différent d’un simple zoom de l’écran, c’est toute la mise en page qui devient fluide. La bonne nouvelle, c’est que le [Fluid type scale calculator](https://utopia.fyi/type/calculator/) se charge de tout. 

Sur mon blog site, avec des variables CSS :

```
:root{
    --step--1: clamp(0.83rem, calc(0.82rem + 0.03vw), 0.84rem);
    --step-0: clamp(1.00rem, calc(0.88rem + 0.31vw), 1.13rem);
    --step-1: clamp(1.20rem, calc(0.90rem + 0.75vw), 1.50rem);
    --step-2: clamp(1.44rem, calc(0.88rem + 1.40vw), 2.00rem);
    --step-3: clamp(1.73rem, calc(0.79rem + 2.34vw), 2.66rem); 
}

html    { font-size: var(--step-0); }
header,
footer,
time    { font-size: var(--step--1); }
h1      { font-size: var(--step-3); }
h2      { font-size: var(--step-2); }
h3      { font-size: var(--step-1); }
```

Il y a 5 lignes (un peu) complexes dans les déclarations initiales. Et ça fonctionne.

## En conclusion


L’ajustement au pixel près ([The Myth of Pixel Perfection](https://www.kelliekowalski.com/articles/the-myth-of-pixel-perfection)) ne fonctionne pas. La mise en page en adaptant avec peine des images faites sur Photoshop est caduque depuis longtemps. Toutefois, des *designers* proposent encore ce genre d’horreurs. Fuyez-les!

Je crois que l’expérience de lecture peut être meilleure sur un écran que sur un papier journal. Trop de médias continuent de proposer des sites qui s’adaptent plus ou moins mal à la diversité des périphériques. Les internautes qui souhaient lire des formats longs et acceptent de payer des abonnement, ne se satisfont plus de sites *qu’il est possible de lire*. 

La typographie fluide est un changement de paradigme. En acceptant *vraiment* de ne pas me soucier de l’apparence exacte de mon site, je me focalise sur le contenu. La seule chose qui m’importe est qu’il puisse être bien consulté. Non comme je le veux, mais comme l’internaute le souhaite.

Pour un site plus complexe, il faudra envisager de généraliser la démarche à toute la mise en page. Une piste: [Designing Intrinsic Layouts](https://www.youtube.com/watch?v=AMPKmh98XLY) de Jen Simmons. Bon CSS!
