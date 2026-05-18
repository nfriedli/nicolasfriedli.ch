+++
description = "La lisibilité du texte long laisse parfois à désirer. Mais je trouve que c’est le critère plus important, avec le contenu, pour aimer passer du temps sur un site. Voici quelques conseils."
title = "Lisibilité des sites web"
+++

Quand je me trouve sur un site depuis quelques minutes et que je l’apprécie, j’essaie toujours de comprendre pourquoi.
Dans une très grande majorité des cas, je constate que ce site se lit très bien.
Il propose un véritable «confort de lecture», comme certains livres.
Je pense que c’est ce qu’il y a de plus important pour un site de contenu.

C’est de la lisibilité du texte dont je parle ici.
Ces considérations s’appliquent donc à des textes longs, appelés aussi «textes de labeur».
Par expérience, je peux affirmer ce qui suit.

La police d’écriture doit faire au moins 100% de la taille par défaut du navigateur.
En règle générale, il s’agit de 16 pixels.
Je pense qu’il est toujours bien de fixer la taille à `font-size: 100%` ou `font-size: 1rem` plutôt qu’à `font-size: 16px`.
Ainsi, le choix des internautes qui auront précisé une autre grandeur sera respecté.

Des polices qui sont plus grandes sur un écran de bonne taille peut être un bon choix, mais pas une nécessité.
Sur ce site, j’utilise une variation fluide créée avec [Utopia](https://utopia.fyi/) pour la taille de base.

Les lignes ne doivent pas être trop longues.
J’apprécie celles qui comptent environ 80 caractères.
Je tolère une fourchette entre 60 et 100.

L’interligne devrait être fixé à 1.5, voire 1.6.
Sauf pour les titres (`h1`) et intertitres (`h2`, `h3`, etc.) où l’interligne devrait être réduit à 1.1 ou 1.2.

Mataj Latin propose le jeu [Triangle — a web typography learning game](https://betterwebtype.com/triangle/) pour exercer les interlignes et les longueurs de ligne.

Je trouve que la titraille trop espacée n’est pas du tout lisible; elle donne un aspect négligé.
En bonus, on peut appliquer un `text-wrap: balance` qui équilibre la longeur les lignes.

Le contraste entre l’écriture et le fond doit être suffisamment élevé.
C’est une évidence pour des questions d’accessibilité (A11Y).
Mais je pense qu’il faut aller plus loin que les exigences minimales et obtenir des contrastes de 12 ou plus.

La police d’écriture m’importe assez peu.
Je trouve des sites très bon en Arial, d’autres en Georgia, d’autres enfin en police à chasse fixe.
Mais il faut qu’il contraste suffisamment avec le fond.
Je déconseille de choisir des fontes trop fines.
`font-weight: 400` ou `font-weight: normal` fonctionnent bien, c’est le choix par défaut des navigateurs et ce n’est pas un hasard.

Les couleurs m’importent peu, tant que les contrastes sont suffisants.
J’apprécie les liens soulignés, au moins dans le corps du texte, et souhaite que rien d’autre que les liens ne le soit ([Opquast 139](https://checklists.opquast.com/fr/qualite-numerique/le-soulignement-est-reserve-aux-liens)).

En général, je ne respecte pas les règles typographiques qui exigent des espaces avant les ponctuations doubles.
L’absence d’espaces me paraît mieux adapté au web.
Mais si vous appliquez les règles classiques, il faut veiller à utiliser des insécables.
Le «deux-points» ou le «point-virgule» en début de ligne ne montrent pas un grand soin.
Il n’est pas rare de trouver des médias très laxistes dans ce domaine.

J’apprécie que les blancs structurent la page, avec un espacement correct entre les paragraphes.
Les intertitres méritent souvent un peu plus d’«air» avant, voire après.

Je n’ai pas utilisé d’intertitres sur cette page; ni d’italique, ni de gras.
Mais si vous êtes arrivé·e ici, c’est peut-être qu’elle était suffisamment agréable (et intéressante) à lire.

---

Retours bienvenus pour m’aider à compléter la page.
On pourrait parler de guillemets, d’apostrophes typographiques, de ligatures, de listes, de citations, etc. selon vos envies et vos besoins.

Je suis aussi prêt à évaluer votre propre site et à vous fournir quelques règles en CSS pour l’améliorer.
