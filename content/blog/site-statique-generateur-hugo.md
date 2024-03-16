---
title: Site statique, générateur de site & Hugo
description: Je vous dit pourquoi j’ai choisi Hugo parmi les générateurs de sites statiques. Mais aussi pourquoi les sites statiques sont pertinents aujourd’hui encore.
date: 2024-03-16
categories:
- hugo
---

Ce site est motorisé par Hugo, je vous dis pourquoi j’ai choisi ce générateur de sites statiques. Mais avant, je vous dit pourquoi je pense qu’un générateur de sites statiques est une bonne idée. Et avant, je vous dit pourquoi un site statique – même généré à la main – est intéressant. Bon voyage dans ce billet en 3 étapes.

## Pourquoi un site statique?

Un site statique envoie au client **les contenus exacts qui existent déjà sur le serveur**, sans modifications autre qu’une éventuelle compression à la volée. Voici ce que je considère comme les principales forces des sites statiques:

- Un site statique est **pérenne**. S’il fonctionne un jour, il fonctionnera de la même manière le lendemain. Le site restera valable tant que les navigateurs sauront interpréter HTML, CSS et Javascript. Les navigateurs arrivent toujours se débrouiller du vieux code ou ils n’arrêteront pas de le comprendrendre soudainement.

- Un site statique est **performant** par nature. Parce que le contenu qui sera envoyé est déjà prêt sur le serveur, il n’est pas possible de faire plus léger. Mais il reste possible de faire un site statique problématique, parce que [La Jamstack n’est rapide que si vous y veillez](https://jamstatic.fr/2020/10/05/la-jamstack-n-est-rapide-que-si-vous-la-rendez-rapide/).

- Un site statique est **écologique**, parce qu’il ne demande pas de calculs inutiles au serveur. Ils sont faits une fois pour pour toutes. Bien évidemment, il sera encore plus écologique chez un hébergeur écoresponsable, sans envoyer des vidéos inutiles, avec des images correctement dimmensionnées, en faisant l’impasse sur les *plugins* des réseaux sociaux ou les statiques gourmandes en énérgie, avec des polices système, etc.

- Une **sauvegarde** d’un site statique existe quelque part. Si le code est géré par sur GitHub par exemple, il est probable que des copies se trouvent sur au moins un ordinateur, sur le serveur de GitHub et sur le serveur Apache de l’hébergeur. Même sans systeme de gestion de versions, il existe probablement un site local et un site distant. En gros, à part si tout est géré à distance par FTP, il existe une sauvegarde exacte du site.

- L’**historique** du site est entièrement disponible si le développement utilise un outil comme Git (distant ou local).

- La **sécurité** d’un site statique est assurée. Il n’offre pas d’accès à une interface d’administration distante, il ne stocke pas de données, etc.

- Finalement, un site statique est **portable**. Sa migration d’un serveur à un autre se résume à la copier de fichiers. En cas de problème, c’est une démarche facile et rapide; le temps étant proporitionnel à la masse de données à copier.

Mais avant de mettre son site sur un serveur, il faut le créer. Passons au point suivant.

## Pourquoi un générateur de sites statiques?

Fondamentalement, un générateur de sites statiques ou SSG (*static site generator*) est un outil qui permet d’**automatiser des tâches répétitives**. Il existe [des centaines de générateurs de sites](https://jamstack.org/generators/), avec différentes visées et dans différents langages. Mais voici quelques généralités sur le sujet:

- Un générateur de sites statiques permet de **simplifier la rédaction** de contenus. L’utilisation de Markdown ou un autre [langage de balisage léger](https://fr.wikipedia.org/wiki/Langage_de_balisage_l%C3%A9ger) facilite et accélère le travail laborieux de saisie de code HTML.

- La **mise en page est automatisée** par un système de gabarits (*templates*), par exemple en réutilisant le même entête ou le même pied sur chaque du site. Et en répercutant chaque modification sur toutes les pages.

- Les **tâches répétitives sont réalisées par une machine** plutôt que par un cerveau humain. Un ordinateur sera beaucoup plus efficace et fiable que vous et moi pour créer une liste de pages d’un répertoire triée par dates, pour générer un fichier RSS ou Atom valide, pour exporter les contenus de tous le site en format JSON pour un moteur de recherche, etc.

- Des **optimisations sur les fichiers texte** (HTML, CSS, Javascript, XML, etc.) sont effectuées à la génération: minification, nettoyage, concaténation, etc.

- Les **images** sont redimmensionnées, allégées, modifiées au moment de la création du site. Le travail fastidieux de création d’[images adaptatives](https://developer.mozilla.org/fr/docs/Learn/HTML/Multimedia_and_embedding/Responsive_images) est effectuée par une machine.

- Le développement avec un générateur des sites statiques rend agréable la **prévisualisation du site en local**. C’est aussi possible sans SGG, mais souvent moins agréable.

- D’autres automatisations existent, comme la **colorisation sytaxique** du code pour en simplifier la lecture, la **génération d’images** pour les réseaux sociaux, l’activation d’un **moteur de recherche interne**, etc.

Beaucoup d’outils permettent tout ou partie de ces opérations (et d’autres). Parmi ceux que j’ai utilisés et utilises encore: [Eleventy](https://www.11ty.dev/) (11ty), [Sphinx](https://www.sphinx-doc.org/en/master/) ou [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/). Mais il y a surtout Hugo, qui motorise ce site et pas mal d’autres que j’ai créés. Passons au point suivant.

## Pourquoi j’ai choisi Hugo?

[Hugo](https://gohugo.io/) est donc **un des principaux générateurs de site statiques**. Il est plutôt généraliste et je le choisis *a priori* pour mes projets (sans exclure d’autres outils pour des développements plus spécifiques). Voici ce qui m’a convaincu chez Hugo:

- L’**installation est triviale**, par la copie d’un seul fichier exécutable. Il ne demande aucun écosystème préalable (par exemple Python ou Node). Il peut être utilisé sur un ordinateur sans droits d’administration. Corollaire: le **logiciel est pérenne** car sans dépendances. Il pourrait toujours générer le site dans plusieurs années et peut être stocké dans le répertoire des sources du site.

- Il est conçu selon une **logique «classique»** que je trouve pertinente dans la très grande majorité des cas. Il existe des types implicites comme des listes (qui proposent les contenus des répertoires et sous-répertoires) et des pages simples (qui sont le contenu). Le fichier de configuration est un simple fichier de configuration. La séparation entre les *templates* et les contenus est évidente.

- La **gestion du multilinguisme** est aboutie et disponible par défaut. C’est très important quand on travaille en Suisse.

- Les **taxonomies** et les **relations entre les pages** sont très performantes. Notamment la notion de *related* que j’utilise par exemple dans mon projet d’[annuaire protestant en ligne](https://nicolasfriedli.ch/blog/annuaire-protestant/).

- La **conception monolithique** du logiciel fait que tout est inclus (*batteries included*). C’est parfois considéré comme une limitation, par rapport à un système modulaire (*plugins*), mais c’est un avantage dans la très grande majorité des cas.

- Hugo est **très rapide** à la compilation. Il y a débat pour savoir sur c’est le générateur le plus rapide, mais je m’en balance. Je sais qu’il me permet de travailler le code ou le contenu sur un écran et voir le résultat en temps réel sur mon second écran. C’est tout ce que je souhaite.

- Il permet par défaut des **optimisations raisonnables** dans la minification des fichiers texte et le travail sur les images. Sans être forcément le plus performant, son rapport entre le résultat et l’investissement (en temps de compilation ou en complexité de développement) est excellent. C’est l’efficience.

- Finalement, Hugo dispose d’une **bonne communauté**, tant du point de vue de la quantité d’informations disponibles que de la qualité des rapports entre personnes.

Le code de plusieurs projets que je développe avec Hugo est disponibles dans [mon compte GitHub](https://github.com/nfriedli/). C’est le cas des [sources de ce site](https://github.com/nfriedli/).

----

Je pense que ce billet sera complété ou revu régulièrement. Il y a des choses auxquelles je n’ai pas pensé,; d’autres que je pense assez marginales pour ne pas en parler aujourd’hui. Mais tous vos retours sont bienvenus pour essayer de l’améliorer.
