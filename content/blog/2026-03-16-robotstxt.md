+++
description = "Beaucoup parlent intelligences artificielles (IA) mais peu sont explicites sur les droits qu’elles ont sur les contenus de leurs sites."
lastMod = 2026-05-01
title = "Accepter (ou non) que les IA se nourrissent de nos contenus"
+++

Beaucoup parlent des intelligences artificielles (IA) mais peu sont explicites sur les droits qu’elles ont ou n’ont pas sur les contenus de leurs sites.
Quand les entreprises respectent les règles du jeu, il est possible de régler la situation avec un seul fichier.

Mais, surtout, la discussion mérite d’avoir lieu en interne sans délai.
L’ignorance n’est plus une option.

## La problématique

Pour alimenter les immenses bases de données, les intelligences artificielles siphonnent les sites web.
Les grandes modèles de langage (LLM) des IA génératives (IAg) se construisent sur toutes les données disponibles.
Parfois, c’est légal; parfois pas du tout.

En pratique, des robots (aussi appelés *crawlers* ou *spiders*) consultent tout ce qui est en ligne.
Le trafic généré devient un [sérieux problème](https://next.ink/178942/les-crawlers-des-ia-deviennent-un-serieux-probleme-pour-le-web-meme-pour-wikimedia/) pour de nombreux sites qui élaborent des stratégies de résistance pour ne pas tomber.

Il existe 2 raisons, qui peuvent s’additionner, de refuser les spiders des IA sur son site:

- limiter la bande passante et les coûts de calcul
- interdire le vol pur et simple de contenu

Heureusement, certains robots jouent le jeu honnêtement et respectent encore les règles.
C’est de cela que parle le passage suivant.

## Bloquer par un fichier robots.txt

Le fichier `/robots.txt`, à la racine d’un site, donne des directives aux crawlers qui parcourent le site.
Initialement, ils visaient les robots d’indexation des moteurs de recherche.
Ce [protocole d’exclusion des robots](https://fr.wikipedia.org/wiki/Protocole_d%27exclusion_des_robots) a plus de 30 ans.
L’idée, toute simple, c’est de dire à ces spiders de ne pas parcourir certaines sections du site ou de ne pas référencer certains types de contenus.

En principe, il est possible d’utiliser le même type de règles pour limiter l’accès aux robots des IA.
Il existe des [listes d’exclusion](https://github.com/ai-robots-txt/ai.robots.txt/blob/main/robots.txt) prêtes à l’emploi pour qui souhaite exclure les IA de son site.
Quand les robots sont honnêtes, il respectent ces directives et tout va bien.

Donc, dans un monde honnête, on pourrait donc passer à la réflexion de fond sur l’utilisation des données par les intelligences artificielles.
En sachant que notre position sera prise en compte.

Notre monde n’est plus très honnête, mais la réflexion doit quand même avoir lieu, pour agir en connaissance de cause.

## Positions protestantes réformées sur les IA

Même si [les Églises s’expriment volontiers sur les IA](https://www.eks-eers.ch/fr/blogpost/ia-et-les-eglises/), il n’existe pas de traces de débats sur l’entraînement des LLM par leurs propres sites.

{{< details summary="Problème de l’*opt-out*">}}
L’utilisation des sites par les IA pour l’entraînement de leurs LLM est autorisé tant qu’il n’est pas interdit.
C’est le principe de l’[*opt-out*](https://fr.wikipedia.org/wiki/Opt-out_(marketing)).
En conséquence, il est impossible de savoir si certaines institutions ont accordé un accès complet aux robots à la suite d’une discussion sérieuse.
Elles ne l’ont pas explicitement interdit; il n’y a aucune trace.
{{< /details >}}

### État des lieux

Par sondage, aucune directive pour les IAg n’existe sur des sites protestants à fort contenu.
Par exemple:

- [`robots.txt` de *Je cherche Dieu*](https://jecherchedieu.ch/robots.txt)
- [`robots.txt` de l’EERS (Église évangélique réformée de Suisse)](https://eers.ch/robots.txt)
- [`robots.txt` de *Réformés*](https://www.reformes.ch/robots.txt)
- [`robots.txt` de *Réforme*](https://www.reforme.net/robots.txt)
- [`robots.txt` de *Regards protestants*](https://regardsprotestants.com/robots.txt)

Par contraste, le [`robots.txt` du chercheur Arthur Perret](https://www.arthurperret.fr/robots.txt), qui s’exprime souvent sur les IA, fournit une liste d’exclusion.

{{< details summary="Limites de `robots.txt`">}}
Le fichier `robots.txt` situé à la racine du site est visible par toutes et tous (internautes et robots).
L’état des lieux est construit sur ce qui se trouve dans ce fichier.
Mais rien ne permet d’affirmer qu’il n’existe pas de blocage des IA par d’autres moyens techniques invisibles.
Les sondages qui précèdent ne sont que des sondages.
{{< /details >}}

Mais avant d’exclure les IAg, il faudrait se demander si c’est ce qui est souhaité.
En contexte protestant, théologique, spirituel, etc., la réponse n’est pas toujours triviale.

### Arguments pour la consultation du site

Il est possible d’accorder un accès complet aux crawlers pour alimenter les IA pour des bonnes ou de mauvaises raisons.

La bonne raison, c’est de considérer que du contenu protestant réformé de première main entrera dans leurs bases des données.
Elles fourniront des «réponses protestantes» de meilleure qualité avec de telles sources.

La mauvais raison, c’est d’accorder ce droit par défaut, par paresse ou par ignorance, sans en mesurer les conséquences.

### Arguments contre le siphonnage des données

Le refus de l’entraînement des IA sur un site institionnel protestant peut aussi avoir plusieurs raisons, plus ou moins bonnes:

- pour éviter que des «réponses protestantes» soient proposées après compilation et transformation dans un magma complet.
- parce que le coût énergétique des IA et de leurs centres des données est immense et que l’utilisation des LLM n’est simplement pas souhaitée.
- pour des questions de droits d’auteur

Acceptation ou refus, la décision demande une réflexion de fond, sans délai.
Les contenus théologiques sont-ils un bien commun?
Devraient-ils toujours être libres au sens où j’en parlais dans [Licence Creative Commons (CC)](/blog/cc/)?

Celles et ceux qui produisent des contenus doivent en tout cas être tenus au courant de leur réutilisation possible.
L’ignorance n’est pas une réponse, dans ce domaine comme dans d’autres.

Malheureusement, le respect et l’honnêteté ne font pas partie des vertus cardinales des boîtes de la Big Tech et il faudra aller plus loin.

## Pour aller plus loin

Je vous propose une autre piste avec `robots.txt` ainsi que des possibilités d’action avec d’autres moyens.

### Limitation des moteurs de recherche

La question écologique est au centre des préoccupations de nombreuses associations et institutions.
La cohérence n’est malheureusement pas toujours au rendez-vous sur le web.
J’en avais dit quelques mots dans [Écologie et cohérence sur le web](https://nicolasfriedli.ch/blog/ecologie-coherence/).

Comme l’avait signalé Joost de Valk dans sa conférence [Improve the environment. Start with your website!](https://joost.blog/videos/improve-the-environment-start-with-your-website/), il est possible de limiter les spiders d’indexation par `robots.txt`.
Par exemple, un site local en français peut parfaitement exclure les moteurs de recherche russes et chinois pour diminuer l’utilisation de bande passant et minimiser les calculs inutiles.

Les sites [Détox la Terre](https://detoxlaterre.ch/), [EcoEglise](https://ecoeglise.ch/) et [œcu](https://oeku.ch/fr/) pourraient commencer l’amélioration de leur bilan carbone par là.
Ainsi qu’en refusant les IA qui ne doivent pas leur apporter beaucoup.

### Solution juridique

Cette directive ne bloque aucun robot mais elle affirme votre *opt-out*:

```
<meta name="tdm-reservation" content="1">
```

Elle semble avoir une valeur juridique, mais qu’en est-il en Suisse?
Le juriste [François Charlet](https://francoischarlet.ch/) me signale qu’il faut avant tout que les indications soient claires tant pour les internautes que pour les machines.

En revanche, elle ne résout pas forcément la question de la bande passante.
On peut parfaitement imaginer que les crawlers lisent tout un site (sans en stocker les données) pour trouver des liens externes.

### Exclusion technique des tricheurs

Quand les robots ne respectent pas les règles, il faut trouver d’autres solutions, par exemple:

- la solution [StupidAntibot](https://sebsauvage.net/wiki/doku.php?id=stupidantibot) de sebsauvage, proposée juste après la première publication de ce billet, parce que certains acteurs de l’IA ne respectent rien ni personne
- le [filtre pur et simple dans `.htaccess`](https://github.com/ai-robots-txt/ai.robots.txt/blob/main/.htaccess) plutôt que la liste de directives `robots.txt`
- l’ajout d’un «obstacle» comme [Botcheck](https://github.com/splitbrain/botcheck) d’Andi Gohr ou [Anubis](https://anubis.techaro.lol/)
- le pourrissement volontaire des contenus qui ne devraient pas être lus (si les robots respectaient les règles), c’est la proposition [Poisoning well](https://heydonworks.com/article/poisoning-well/) d’Heydon Pickering
- les [bombes de décompression](https://fr.wikipedia.org/wiki/Bombe_de_d%C3%A9compression) ou *zip bombs* (un tout petit fichier qui devient immense et sature les ordinateurs qui analysent les données, mais qui peut être considéré comme une attaque)

Ces solutions visent toutes à ralentir ou arrêter les crawlers des grandes entreprises qui saturent la bande passante ou ne jouent pas le jeu.
Elles sont discutables parce qu’elles dérangent les internautes.
Certaines sont très consommatrices d’énergie; c’est le but, hélas.

Je suis très réticent à l’utilisation d’une solution trop centralisée comme CloudFlare.
C’est une entreprise si tentaculaire qu’elle fait tomber la moitié du web à chaque problème, elle ne refuse pas la censure, etc.

----

Comme c’est un sujet en mutation permanente, je suis preneur de vos réflexions et de vos solutions.
Et je reste disponible pour parler de votre propre `robots.txt` ou votre `.htaccess`.
À ce jour, je ne limite rien sur theologique.ch, parce qu’il est statique et ultra-léger.
