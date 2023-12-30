---
title: Audit de ce site
description: Résultats des tests de qualité, de performance, d’accessibilité, de sécurité et d’écoconception pour ce site.
date: 2023-11-27
lastMod: 2023-12-20
draft: true
---

Comme je fais la promotion de règles de qualité web, de performance et d’accessibilité sur theologique.ch, il est logique que je m’y plie. Autant prêcher par l’exemple.

## Règles Opquast

Les [règles Opquast](https://checklists.opquast.com/fr/assurance-qualite-web/) sont disponibles en ligne. Certaines règles ne sont pas appliquées sur theologique.ch. Certaines demandent encore du travail, d’autres ne sont pas respectées par choix.

### Contenus

Je préfère expliquer des termes dans des billets que construire une référence. Donc cette règle n’est pas respectée:

- Un lexique ou un glossaire adapté au public visé explique le vocabulaire sectoriel ou technique.

### Liens

Les 2 règles suivantes ne sont pas respectées (c’est un choix que j’assume):

- Le site n’applique pas le même style aux liens visités et non visités.
- Les liens internes et externes sont différenciés.

### Navigation

À ajouter au fil du développement du site:

- Chaque page affiche une information permettant de connaître son emplacement dans l’arborescence du site.
- Le site propose un moteur de recherche interne.
- Un plan du site est disponible depuis chaque page.

### Sécurité

Je ne souhaite pas utiliser de directive Content Security Policy sur un site statique que je gère entièrement. En conséquence, cette règle n’est pas respectée:

- Le site propose un mécanisme de sécurité permettant de restreindre l’origine des contenus.

## PageSpeed Insights

Le site obtient des «pastilles vertes» (90+ sur 100) chez [PageSpeed Insights](https://pagespeed.web.dev/) tant pour le mobile que pour l’ordinateur de bureau. Le test de la page d’accueil porte sur:

- la performance
- l’accessibilité
- les bonnes pratiques
- le SEO

## Validations W3C

Les résultats des [validations par le World Wide Web Consortium (W3C)](https://validator.w3.org/) sont valides pour:

- le code HTML
- le code CSS (sauf quand j'utilise dès nouvelles règles comme css non connues du validateur...)
- le flux RSS

## Écoconception

Les scores sont les meilleurs possibles chez:

- [Website Carbon Calculator](https://www.websitecarbon.com/)
- [Ecograder](https://ecograder.com/)

## Accessibilité (A11Y)

Aucune erreur et aucune alerte dans [WAVE](https://wave.webaim.org/report#/https://theologique.ch/) (web accessibility evaluation tool). En plus de la pastille verte chez PageSpeed Insights, déjà citée.

## Sécurité

Le site obtient de bons scores sur les sites [Security Headers](https://securityheaders.com/?q=https://theologique.ch) et [Mozilla Observatory](https://observatory.mozilla.org/analyze/theologique.ch). Mais comme je n’utilise pas de directive Content Security Policy, je ne peux pas viser mieux.
