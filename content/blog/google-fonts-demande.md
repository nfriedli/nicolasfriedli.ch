---
title: Activer les polices Google Fonts à la demande
description: Google Fonts est un service qui fonctionne très bien. Mais je refuse d’envoyer des polices distantes sur votre périphérique sans votre autorisation.
date: 2025-02-05
categories:
- polices
- performance
---

Google Fonts est un service qui fonctionne très bien.
Mais je refuse d’envoyer des polices distantes sur votre périphérique sans votre autorisation.
De plus, c’est souvent inutile si vous avez des polices correctes installées.

Ce billet fait suite aux difficultés de proposer une [police locale variable]({{< relref "inter-variable-opsz" >}}) correctement.

## La solution (facile et rapide) Google Fonts

Je propose une solution toute simple pour celles et ceux souhaitent une police précise (qui ont des problèmes d’affichage).

J’active les Google Fonts si la variable `googlefonts` a la valeur `yes` sans le stockage web local (localStorage).
**Cette solution n’est active que sur cette page**, mais elle s’active sur tout le site en utilisant ce code sur chaque page.

```
if (localStorage.getItem("googlefonts") === "yes") {
    let link = document.createElement("link");
    link.rel = "stylesheet";
    link.href = "https://fonts.googleapis.com/css2?family=JetBrains+Mono:ital,wght@0,100..800;1,100..800&family=Roboto:ital,wght@0,100..900;1,100..900&display=swap";
    document.head.appendChild(link);
}
```

On pourrait d’arrêter là et dire aux internautes qui souhaitent des Google Fonts d’entrer la valeur `yes` au bon endroit.
Ce serait un peu rude (plus que leur conseiller d’installer [JetBrains Mono](https://fonts.google.com/specimen/JetBrains+Mono) et [Roboto](https://fonts.google.com/specimen/Roboto)).

Donc, on ajoute un bouton qui stocke la valeur et ajoute la feuille de style sans délai:

```
<button id="googlefonts">Activer les Google Fonts</button>

<script>
document.getElementById("googlefonts").addEventListener("click", function() {
    localStorage.setItem("googlefonts", "yes");
    let link = document.createElement("link");
    link.rel = "stylesheet";
    link.href = "https://fonts.googleapis.com/css2?family=JetBrains+Mono:ital,wght@0,100..800;1,100..800&family=Roboto:ital,wght@0,100..900;1,100..900&display=swap";
    document.head.appendChild(link);
});
</script>
```

Il y a du code dupliqué (ce n’est pas très propre), mais comme je ne l’utilise que sur cette page, je m’en fiche un peu.
On pourrait aussi ajouter seulement la valeur dans le localStorage et attendre le rechargement de la page pour agir.

```
<button id="googlefonts">Activer les Google Fonts</button>

<script>
document.getElementById("googlefonts").addEventListener("click", function() {
    localStorage.setItem("googlefonts", "yes");
});
</script>
```

Le résultat, c’est ceci:

{{< googlefonts >}}

Désormais, c’est mémorisé: ce périphérique chargera les Google Fonts.
Pour toujours (à moins de modifier manuellement la valeur du localStorage ou de créer un bouton qui se charge de le faire).
Si vous revenez sur cette page, ce sera toujours le cas sans cliquer à nouveau sur le bouton.

## La solution locale

J’avais testé une solution complètement locale avec Inter:

1. Conversion des polices variables en `woff2` et limitation aux caractères latins (subsetting).
2. Ajout des `@font-face` qui vont bien dans la feuille de style.
3. Quand les webfonts sont acceptés dans le localStorage (par un bouton), ajout d’une class sur `html class="webfonts"`.
4. Déclaration de `font-family` spécifique à `html.webfonts`.
5. Cacher le bouton d’activation s’il a le localStorage comprend déjà l’acceptation.

Tout est disponible dans le commit [6f1fb29](https://github.com/nfriedli/nicolasfriedli.ch/commit/6f1fb29130cbbcd2907e01c2e7cb5da7f043631b) sur GitHub.

## Les chantiers inutiles

Ce titre est un hommage aux [grands travaux inutiles](https://fr.wikipedia.org/wiki/Grands_travaux_inutiles).

Au fond, ces 2 propositions me paraissent inutiles, parce que mes choix de polices système suffisent.
Mais j’avais envie de tester 2 choses.

D’une part, laisser le choix aux internautes concernant les polices Google Fonts.
Cela peut se mettre en place en 5 minutes.
Et il n’est pas besoin de faire clignoter des bannières de consentement et autres trucs.
Un bouton; c’est tout!

D’autre part, tester le chargement conditionnel d’une police locale, pour imaginer une solution sans service tiers.
C’est un peu plus pénible à maintenir, notamment pour réactualiser les polices quand nécessaire.
C’est un peu plus compliqué à mettre en œuvre, notamment selon les jeux de caractères utilisés sur le site.
Mais c’est possible.

À la suite de cet exercice avec des *web fonts*, je suis encore plus convaincu des polices locales.
Je proposerai désormais toujours de travailler avec *font stacks* système.
Puis permettre d’activer d’autres fontes par un bouton.

Je suis presque certain que personne ne cliquera.

----

Ce page transfère environ 5ko de données pour le contenu (HTML et CSS).
À l’activation des polices Google Fonts, ce sont un peu plus de 120ko qui sont téléchargés.
C’est 24 fois plus.
Rien à ajouter!
