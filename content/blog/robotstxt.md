---
title: Remarques sur le fichier robots.txt en 2026
description: Les directives de robots.txt ne sont pas respectées par certaines entreprises. Ce n’est pas une raison pour ne plus le proposer à celles qui jouent honnêtement le jeu.
lastMod: 2026-07-10
---

Le fichier `robots.txt` reste intéressant envers et contre tout.
Il fonctionne depuis plus de 30 ans, plutôt bien.
Ce n’est pas parce que les grandes entreprises d’intelligence artificielle (IA) ne le respectent pas que je vais l’abandonner; elles ne respectent rien.

## Collaboration entre honnêtes gens

Le principe du `/robots.txt` ou [protocole d’exclusion des robots](https://fr.wikipedia.org/wiki/Protocole_d%27exclusion_des_robots) est de donner des directives pour l’exploration de son site.

C’est un fichier visible publiquement.
Celui de ce site est donc disponible à l’URL <https://nicolasfriedli.ch/robots.txt>.

Quand un robot (aussi appelé *crawler* ou *spider*) arrive sur mon site, il dit qui il est avec l’instruction `user-agent`.
Dans mon fichier, je donne des instructions spécifiques par nom de robot.
Un exemple tout simple, en langage naturel:

> Si tu es le robot d’indexation de Google, tu peux parcourir tout mon site à l’exception du répertoire `/photos/`.

En langage `/robots.txt`:

```
User-agent: Googlebot
Disallow: /photos/
```

Le truc génial du deal, c’est que:

- ce répertoire ne sera pas indexé dans Google (ce que **je** souhaite)
- car Google ne va pas le parcourir et l’analyser (ce qui **lui** fait économiser des ressources)

Les 2 parties sont gagnantes.
L’instruction tient en quelques lignes.
Et tout va bien.

Ne serait-ce que parce que des entreprises respectent cette manière de faire, je pense qu’il vaut la peine de rédiger quelques lignes d’instruction.

## Déclarer ses intentions

En affichant des directives dans un fichier public, je dis clairement ce que je souhaite (ou ne souhaite pas).

Si j’exclus ChatGPT pour tout mon site, je signifie que je ne souhaite pas voir mes contenus utilisés pour fourrager la bête.
Cela complète bien la [licence des contenus](/license/).

Ainsi, je dis, en langage naturel:

> Je ne souhaite pas que toi, ChatGPT, utilise mon contenu pour construire ta base de connaissance.
> Et si tu les utilisais, tu devrais respecter la licence.

Je ne me fais aucune illusion sur le manque de respect de toute règle éthique par entreprises derrière les grands modèles de langages (LLM) et IA génératives.
Mais je permet à quiconque de voir comment je me positionne par rapport à ces outils.

## Économiser la bande passante

Comme certains outils continuent à respecter les directives de `robots.txt`, c’est possible de limiter les transferts de données inutiles.
Il n’y a aucune raison que des moteurs de recherche russe ou chinois indexent mon site.
Les outils de référencement (SEO) n’ont pas besoin de parcourir mes contenus.

Je vais être clair, ces règles dans `robots.txt` ne sont pas un outil pour «lutter contre des bots».
Si votre serveur croule sous la charge, ce n’est pas une réponse pertinente.
C’est une fois encore une bonne pratique entre gens fréquentables.
Mais l’idée que ce soit respecté me motive à jouer le jeu envers et contre tout.

## Règles de mon `robots.txt`

Les règles exactes du jour sont disponibles en tout temps dans le fichier en production ou sur GitHub.
Mais le principe est visible ici.
J’exclus 3 types de robots.

Les moteurs de recherche qui n’ont aucun intérêt à lire mon site:

```
User-agent: 360Spider
User-agent: Baidu
User-agent: Baiduspider
User-agent: PetalBot
User-agent: SeznamBot
User-agent: Shenma
User-agent: Sogou web spider
User-agent: Yandex
Disallow: /
```

Les outils SEO:

```
User-agent: AhrefsBot         
User-agent: AhrefsSiteAudit
User-agent: DotBot
User-agent: MJ12bot
User-agent: SemrushBot
User-agent: SemrushBot-SA
Disallow: /
```

Les IA:

```
User-agent: Amazonbot
User-agent: anthropic-ai
User-agent: Applebot-Extended
User-agent: Bytespider
User-agent: CCBot
User-agent: ChatGPT-User
User-agent: Claude-SearchBot
User-agent: Claude-Web
User-agent: ClaudeBot
User-agent: cohere-ai
User-agent: Diffbot
User-agent: FacebookBot
User-agent: FriendlyCrawler
User-agent: Google-Extended
User-agent: GPTBot
User-agent: meta-externalads
User-agent: meta-externalagent
User-agent: meta-externalfetcher
User-agent: OAI-AdsBot
User-agent: OAI-SearchBot
User-agent: Omgili
User-agent: Perplexity-User
User-agent: PerplexityBot
User-agent: YouBot
Disallow: /
```

## Références utiles

Je vous conseille le billet [Bloquer les AI bots](https://www.didiermary.fr/bloquer-ai-bots-chatgpt-openai/) de Didier J. Mary, tenu à jour et beaucoup plus développé que cette page.

Il existe des [listes d’exclusion](https://github.com/ai-robots-txt/ai.robots.txt) prêtes à l’emploi pour qui souhaite exclure les intelligences artificielles (IA) de son site.

CloudFlare propose un [Bots Directory](https://radar.cloudflare.com/bots/directory) avec les robots les plus actifs par catégories.

Je me suis inspiré de 3 ressources ci-dessus pour créer ma liste.

## Exclusion technique des tricheurs

Quand les robots ne respectent pas les règles, il faut trouver d’autres solutions, par exemple:

- la solution [StupidAntibot](https://sebsauvage.net/wiki/doku.php?id=stupidantibot) de sebsauvage
- l’ajout d’un «obstacle» comme [Botcheck](https://github.com/splitbrain/botcheck) d’Andi Gohr ou [Anubis](https://anubis.techaro.lol/)
- le pourrissement volontaire des contenus qui ne devraient pas être lus (si les robots respectaient les règles), c’est la proposition [Poisoning well](https://heydonworks.com/article/poisoning-well/) d’Heydon Pickering
- les [bombes de décompression](https://fr.wikipedia.org/wiki/Bombe_de_d%C3%A9compression) ou *zip bombs* (un tout petit fichier qui devient immense et sature les ordinateurs qui analysent les données, mais qui peut être considéré comme une attaque)

Ces solutions visent toutes à ralentir ou arrêter les crawlers des grandes entreprises qui saturent la bande passante ou ne jouent pas le jeu.
Elles sont discutables parce qu’elles dérangent les internautes.
Certaines sont très consommatrices d’énergie; c’est le but, hélas.

Je suis très réticent à l’utilisation d’une solution trop centralisée comme CloudFlare.
C’est une entreprise si tentaculaire qu’elle fait tomber la moitié du web à chaque problème, elle ne refuse pas la censure, etc.
