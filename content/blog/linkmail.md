---
title: Utiliser des liens mail préremplis sur son site web
description: Comment structurer et optimiser les liens mailto? Avantages des emails préremplis, limites des formulaires de contact et implémentation automatisée dans Hugo via un shortcode.
date: 2025-02-08
categories:
- hugo
---


Les liens `mailto` sont un moyen simple et efficace d’encourager les utilisateurs au contact direct par mail.
Ils peuvent être enrichis pour inclure un sujet, un message prérempli et d’autres informations.

Nous verrons comment tirer parti des liens mailto préremplis, en comparant leurs avantages et leurs limites face aux formulaires de contact.
Je vous propose une solution efficace pour les automatiser dans Hugo grâce à un shortcode.

## Structure des liens

La syntaxe des liens HTML la plus simple pour un mail, c’est:

```
<a href="mailto:hello+linkmail@nicolasfriedli.ch">hello+linkmail@nicolasfriedli.ch</a>
```

En Markdown, il est possible de le saisir avec:

```
[hello+linkmail@nicolasfriedli.ch](mailto:hello+linkmail@nicolasfriedli.ch)
```

Et, parfois, les outils de rédaction ou les périphériques de lecture transforment du simple texte en lien cliquable:

```
hello+linkmail@nicolasfriedli.ch
```

Mais ce qui est intéressant, c’est d’ajouter directement du contenu au lien lui-même.
C’est facile avec [mailtolink.me](https://mailtolink.me/).

Le résultat, c’est [une réponse à ce billet](mailto:hello+mailto@nicolasfriedli.ch?subject=Ton%20article%20sur%20LinkMail&body=Je%20viens%20de%20lire%20ton%20billet%20sur%20les%20liens%20mail%20et%20j’ai%20une%20question%20%2F%20une%20remarque%20%2F%20un%20compl%C3%A9ment%20%C3%A0%20apporter.).
Le sujet du message est déjà renseigné, tout comme mon adresse (logique) et quelques lignes de texte.
Et si cela ne fonctionne pas bien, la suite vous explique pourquoi.

## Avantages des liens mail préremplis

Les liens `mailto` enrichis offrent certains avantages:

- l’adresse d’envoi est fatalement valide
- la personne qui envoie le mail possède toujours une copie dans sa boîte
- les messages peuvent être complétés librement
- il est possible d’ajouter des pièces jointes

La difficulté c’est qu’il faut utiliser l’[encodage-pourcent](encodage-pourcent).
C’est facile avec l’outil mailtolink.me, mais plus difficile (ou franchement pénible) à la main.

## Pourquoi les formulaires de contact posent problème

Je n’aime pas beaucoup les formulaires de contact.
Ils créent potentiellement beaucoup de problèmes:

- si l’adresse d’envoi est fausse, il n’y a aucune vérification
- ils permettent rarement l’envoie de pièces jointes (ou limitent leur nombre)
- il demandent un nombre important de [contrôles de qualité](https://checklists.opquast.com/fr/assurance-qualite-web/?theme=formulaires)
- ils ne sont pas plus effiaces contre le spam que de filtres de messagerie

Le seul avantage est qu’ils permettent de bien structurer une demande, avec des champs distincts (qui peuvent recevoir des contraintes et validations).
Je conseille [Découvrez «le bon HTML» et économisez du JS et du CSS](https://www.paris-web.fr/2022/conference/decouvrez-le-bon-html-et-economisez-du-js-et-du-css) pour en savoir plus.

## Les inconvénients et limites des liens `mailto`

J’ai vanté les mérites des liens `mailto, mais ils ne sont pas exempts de défauts.
Mais je ne vous cache pas qu’ils posent aussi certains problèmes.

Amy Hupe et Adam Silver les ont documentés dans [The trouble with mailto email links and what to do instead](https://adamsilver.io/blog/the-trouble-with-mailto-email-links-and-what-to-do-instead/).

En résumé, ces liens posent problème quand:

- une messagerie n’est pas configurée sur le périphérique
- je souhaite avoir le choix de la messagerie au clic
- je souhaite copier une adresse

Je m’inspire de leur approche dans le passage *offering choice* et propose:

- un lien textuel avec le contenu du mail prérempli
- l’affichage de l’adresse en pur texte à côté

Ainsi, toutes les options restent possibles en fonction des préférence de l’internaute.

## Shortcode dans Hugo

C’est très facile à faire avec mailtolink.me, mais je souhaite automatiser la procédure dans Hugo.

Ainsi, je souhaite créer un lien prérempli quand je rédige en Markdown:

```
{{</* linkmail to="hello+linkmail@nicolasfriedli.ch" subject="Test de Link Mail"  text="Envoyer une proposition" */>}}
Exemple de texte qui préremplit le message.
Avec un saut de ligne.
{{</* /linkmail */>}}
```

Pour effectuer la transformation, je crée `layouts/shortcodes/linkmail.html`:

```
<a href="mailto:{{- .Get "to" -}}?subject={{- .Get "subject" -}}&body={{- strings.TrimSpace .Inner -}}">
    {{- .Get "text" -}}
</a>
({{ .Get "to" }})
```

Et j’obtiens le résultat escompté:

{{< linkmail to="hello+linkmail@nicolasfriedli.ch" subject="Test de Link Mail"  text="Envoyer une proposition" >}}
Exemple de texte qui prérempli le message.
Avec un saut de ligne.
{{< /linkmail >}}

Attention, c’est une solution [Quick-and-dirty](https://fr.wikipedia.org/wiki/Quick-and-dirty).
Je ne fais aucune vérification dans le shortcode.
Mais la transformation par Hugo se charge de l’encodage-pourcent et `strings.TrimSpace` supprime des espaces inutiles.
C’est l’essentiel.

Cette solution rapide fonctionne bien dans Hugo, mais elle pourrait être améliorée avec des vérifications supplémentaires.
Il faudrait l’adapter aux cas spécifiques, affiner la mise en forme du lien et optimiser la syntaxe d’appel.
Toutefois, c’est une approche intéressante pour systématiser l’usage des liens `mailto` enrichis sans outil tiers.
