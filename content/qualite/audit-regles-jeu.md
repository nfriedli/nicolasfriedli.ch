---
title: Les règles du jeu d’un audit sont connues à l’avance
description: La notion d’audit n’est pas toujours très claire Il vaut la peine de s’entendre sur les règles du jeu avant de commencer la partie.
date: 2023-12-19
draft: true
---

La notion d’audit n’est pas toujours très claire, dans le domaine du web comme ailleurs. Il vaut la peine de clarifier les choses pour s’entendre sur les règles du jeu avant de commencer la partie.

## Audits & problèmes

Quand un service dysfonctionne, quand il y a un souci quelque part, il n’est pas besoin d’attendre longtemps pour entendre la phrase fatidique: il faudrait un audit.

Un audit devrait permettre de trouver des solutions là où les organisations n’y arrivent pas. Cette affirmation a quelque chose de magique, pour ne pas dire qu’elle tombe du ciel. Elle est surtout éloignée de la réalité. J’en prends pour exemple un extrait de la page [Wikipédia sur l’audit](https://fr.wikipedia.org/wiki/Audit):

> Il s’agit donc d’opérations d’évaluations, d’investigations, de vérifications ou de contrôles, regroupées sous le terme d’*audit* en raison d’exigences réglementaires ou normatives.

L’enjeu, ce sont bien ces «exigences règlementaires ou normatives». Pour auditer, il faut connaître les exigences au préalable, pour y confronter la réalité de la situation. Il ne s’agit pas de *règler un problème*, mais de *se conformer à un référentiel connu*.

Dans bien des cas, les exigences sont peu claires, mal formulées, pas transmises, voire inexistantes. À rien ne sert d’auditer sans référentiel. C’est ce que j’appelle les *règles du jeu* dans mon titre.

## Objectivité

Dans un audit web, c’est l’objectivité qui compte, à deux titres:

- l’objectivité des critères et des normes à atteindre
- l’objectivité de l’auditeur ou de l’auditrice qui les vérifie

Pas de magie derrière l’ensemble de la démarche. Il faut de la clarté dans les formulations des objectifs et il faut que l’évaluation soit possible sans équivoque. Dans l’absolu, n’importe qui peut effectuer un audit. Il n’y a pas de *statut particulier* pour le mener. Toutefois, il faut comprendre parfaitement les règles et travailler avec méthode.

Dans ma démarche de qualité web, j’essaie d’atteindre un maximum d’objectivité. Si vous me demandez un audit de votre site, je vous dirai selon quels référentiels je vais l’évaluer. Je ne suis pas là pour *donner mon avis* sur votre site, mais pour l’auditer rigoureusement.

## Qualité du code

La qualité du code est évaluée selon des critères connus. C’est parce que ces critères existent et son respectés que votre navigateur est capable d’interpréter du code HTML.

Le standard HTML est long et complexe, mais je peux en dire rapidement:

- que le code doit être bien formé (que sa syntaxe doit être respectée)
- que le code doit être valide (que l’utilisation des balises se fait de manière correcte)
- que le code doit être sémantiquement valable (que la bonne balise est utilisée au bon endroit)

Pour les 2 premiers points, le [Markup Validation Service](https://validator.w3.org/) du W3C donne très rapidement des résultats.

Il en va de même pour les feuilles de style CSS (validées par le [CSS Validation Service](https://jigsaw.w3.org/css-validator/)) ou les flux RSS (validées par le [Feed Validation Service](https://validator.w3.org/feed/)) fonctionnent de la même manière. Des normes précises, des règles claires, des résultats sans équivoque.

## Performances

Dans un premier temps, je mesure toujours les performances d’un site dans [PageSpeed Insights](https://pagespeed.web.dev/?hl=fr).  

Là aussi, les règles sont claires et connues dès le départ. Même s’il ne s’agit pas d’une norme comme pour le code, il s’agit de mesures (ou métriques) bien définies. Et, surtout, le barème est connu *a priori*. La documentation [Évaluation des performances Lighthouse](https://developer.chrome.com/docs/lighthouse/performance/performance-scoring?hl=fr) précise en détail tout ce qu’il faudrait atteindre.

Le critères sont fixés par Google plutôt que par un organisme de normalisation, certes. Mais tous ces objectifs ont un sens, sont discutés, critiqués, modifiés pour devenir une «norme pragmatique». Il existera toujours des Mme Michu et des M. Machinchose qui essaieront de me convaincre que leur site médiocre n’atteint pas ces scores pour mille et une raisons; c’est une fuite, rien d’autre.

## Écoconception

L’écoconception a aussi ses métriques. Le [Website Carbon Calculator](https://www.websitecarbon.com/) donne un résultat unique qui paraît parfois être une sanction. Pourtant, toute la méthodologie est décrite en détail dans [How does it work?
](https://www.websitecarbon.com/how-does-it-work/) et [Estimating Digital Emissions](https://sustainablewebdesign.org/calculating-digital-emissions/). Quiconque peut lire tous les critères, chercher à les comprendre, à les appliquer et améliorer son site.

Si j’estime qu’il y a un problème d’écoconception assez généralisé (dans [Écologie et cohérence](/qualite/ecologie-coherence/)), c’est parce que j’ai testé des centaines de sites et des milliers de pages. Je m’exprime avec neutralité selon des critères objectifs qui ne sont pas choisis par moi.

Le *Website Carbon Calculator* ne vous plaît pas? Essayez [Ecograder](https://ecograder.com/), qui est tout aussi transparent sur sa page [How it Works](https://ecograder.com/how-it-works).

## Accessibilité

L’accessibilité (A11Y) est définie dans la [Web Accessibility Initiative (WAI)](https://www.w3.org/WAI/). Il existe aussi des normes nationales comme le Référentiel général d’amélioration de l’accessibilité (RGAA). Elle se teste bien, en première approche, avec les [Web Accessibility Evaluation Tools (WAVE)](https://wave.webaim.org/)

Lorsque j’affirme qu’un site est illisible, c’est par exemple parce qu’il présente des contrastes insuffisants. Le contraste se mesure, il ne s’évalue pas *au doigt mouillé*, ni selon les goûts des graphistes, ni en fonction des humeurs de la direction. Là aussi, nous connaissons les règles du jeu en amont.

## Règles Opquast

Je ne vais pas m’étendre sur les règles Opquast dont je parle souvent ici. En guise de conclusion de ce billet, cette courte citation de [La fin des «bonnes pratiques» Opquast?](https://www.opquast.com/la-fin-des-bonnes-pratiques-opquast/):

> En tant que prestataire Web, ces 240 règles sont celles que **vous pouvez expliquer ou opposer à vos clients**. En tant que client, ces 240 règles sont celles que **vous pouvez montrer voire exiger de vos prestataires**. Si vous êtes étudiant et faites du Web, ce sont les 240 règles que **vous devez connaître pour prétendre «faire du Web»**.

Vous n’avez pas forcément toutes les cartes entre vos mains pour lancer une partie, parce que vous n’avez pas encore lu toutes les règles. Mais vous savez désormais tout ce qui est en jeu quand vous parlez d’audit.