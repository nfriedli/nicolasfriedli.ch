---
title: Colorisation syntaxique avec Chroma dans Hugo
description: La colorisation syntaxique facilite la lecture du code. Notes sur l’utilisation de Chroma pour optimiser les CSS et l’accessibilité (A11). 
date: 2025-01-11
categories:
- a11y
- hugo
- performance
---

Je souhaite utiliser la colorisation syntaxique sur ce site. Elle existe par défaut dans Hugo, avec l’excellent Chroma.
Mais je ne vais pas le faire sans certaines précautions: la pérennité si je modifie mon thème, l’assurance de l’accessibilité (A11Y), l’existence de versions claire et sombre et l’optimisation des perfomances (webperf).

**Remarque:** pour le moment, rien n’est activé sur ce site qui présente le code en blanc sur noir (ou noir sur blanc).

Une lecture préalable  de [Syntax highlighting](https://gohugo.io/content-management/syntax-highlighting/) dans la documentation de Hugo est souhaitable.

## Contraste des couleurs

J’ai passé [tous les thèmes disponibles dans Chroma](https://xyproto.github.io/splash/docs/longer/all.html) dans les [WAVE Web Accessibility Evaluation Tools](https://wave.webaim.org/report#/https://xyproto.github.io/splash/docs/longer/all.html).
Ceux qui passent disposent d’un contraste suffisant pour être accessibles sont:

- average
- borland
- bw
- doom-one
- doom-one2
- github-dark
- github
- modus-operandi
- modus-vivendi
- pygments
- rrt
- witchhazel
- xcode

J’exclus tous ceux qui ne sont pas accessibles (A11Y) par défaut.

## Couleur de fond définie

Quand la couleur de fond de `pre` n’est pas définie, il y a un risque si je modifie ma charte de couleurs.
Par défaut, ces thèmes ne sont pas assez pérennes pour que je les retiennent:

- hr_high_contrast
- hrdark
- onesenterprise
- pygments

Par rapport à la liste des thèmes accessibles, seul pygments est concerné.
Je l’élimine.

Il me reste donc comme thèmes accessibles et pérennes:

- average
- borland
- bw
- doom-one
- doom-one2
- github-dark
- github
- modus-operandi
- modus-vivendi
- rrt
- witchhazel
- xcode

## Polices à chasse fixe

*Ce point ne concerne pas Chroma, mais mon utilisation d’Hugo et mes choix de polices.*

J’ai décidé de placer en priorité Roboto Mono comme police à chasse fixe (monospace).
Mais si cette police est bien à largeur fixe, elle diffère légèrement entre version droite et version italique.
**C’est à mon avis une erreur!**

En conséquence, je refuse tous les thèmes qui comprennent des italiques, par exemple abap ou algol.

Il me reste, de la liste précédente:

- github
- modus-operandi
- modus-vivendi
- witchhazel
- xcode

## Mode clair (light) et mode foncé (dark)

Désormais, je dois me demander si je souhaite une même version pour les thèmes light et dark de mon site.

Si je souhaite 1 même style (CSS) pour les 2 versions du site, je peux utiliser la syntaxe par CSS embarqué ou par feuilles de style externes.
Autrement dit, les 2 options suivantes sont possibles dans `hugo.toml`:

```
noClasses = false   <- il faut générer 1 feuille de style externe
noClasses = true    <- option par défaut
```

Pour générer mon CSS externe, il faut lancer une commande du type:

```
hugo gen chromastyles --style github > static/css/github.css
```

Cette feuille de style est fonctionnelle, mais ne sera pas optimisée par la suite.
J’en profite pour faire mieux ci-dessous.

Si je souhaite des thèmes différents (light et dark), je dois générer 2 feuilles de style externes différentes:

```
noClasses = false   <- il faut générer 2 feuilles de style externes
```

Puis, je génère les CSS dans `assets`:

```
hugo gen chromastyles --style modus-operandi > assets/css/modus-operandi.css
hugo gen chromastyles --style modus-vivendi > assets/css/modus-vivendi.css
```

Ensuite, un appel distinct selon que le thème est clair ou foncé:

```
{{ $modusoperandi  := resources.Get "css/modus-operandi.css" | minify | fingerprint }}
{{ $modisvivendi   := resources.Get "css/modus-vivendi.css" | minify | fingerprint }}

<link
    rel="stylesheet" 
    href="{{ $modusoperandi.RelPermalink }}"  
    media="screen and (prefers-color-scheme: dark)" >

<link 
    rel="stylesheet" 
    href="{{ $modisvivendi.RelPermalink }}"  
    media="screen and (prefers-color-scheme: light)" >
```

**Voir aussi:** mon billet [Feuilles de style minifiées et gestion du cache](https://nicolasfriedli.ch/blog/css-minification-cache/) pour comprendre les lignes ci-dessus.

## Uniformité des couleurs

Quand j’utilise du code sans préciser un langage pour la colorisation syntaxique, je souhaite avoir exactement les mêmes couleurs qu’avec la colorisation activée.

Donc, dans mon exemple, il faudrait aller chercher les codes couleurs exacts des CSS générés et les appliquer à `pre`.
Pour du code différent entre dark et light lorsque la colorisation n’est pas activée, quelque chose comme:

```
pre {
    background: #000;
    color: #FFF;

    @media (prefers-colors-scheme: dark ) {
        background: #FFF;
        color: #000;
    }
}
```

## Validité et optimisation du CSS

La feuille de style générée avec `hugo gen chromastyle` est complète et commentée.
Et c’est très bien ainsi, par exemple pour faciliter sa modification (sujet que je ne traite pas ici).

Le fichier `modus-operandi.css`:

```
/* Background */ .bg { color:#000;background-color:#fff; }
/* PreWrapper */ .chroma { color:#000;background-color:#fff; }
/* Other */ .chroma .x {  }
/* Error */ .chroma .err {  }
/* CodeLine */ .chroma .cl {  }
/* LineLink */ .chroma .lnlinks { outline:none;text-decoration:none;color:inherit }
/* LineTableTD */ .chroma .lntd { vertical-align:top;padding:0;margin:0;border:0; }
/* LineTable */ .chroma .lntable { border-spacing:0;padding:0;margin:0;border:0; }
/* LineHighlight */ .chroma .hl { background-color:#e5e5e5 }
/* LineNumbersTable */ .chroma .lnt { white-space:pre;-webkit-user-select:none;user-select:none;margin-right:0.4em;padding:0 0.4em 0 0.4em;color:#7f7f7f }
/* LineNumbers */ .chroma .ln { white-space:pre;-webkit-user-select:none;user-select:none;margin-right:0.4em;padding:0 0.4em 0 0.4em;color:#7f7f7f }
/* Line */ .chroma .line { display:flex; }
/* Keyword */ .chroma .k { color:#5317ac }
/* KeywordConstant */ .chroma .kc { color:#0000c0 }
/* KeywordDeclaration */ .chroma .kd { color:#5317ac }
/* KeywordNamespace */ .chroma .kn { color:#5317ac }
/* KeywordPseudo */ .chroma .kp { color:#5317ac }
/* KeywordReserved */ .chroma .kr { color:#5317ac }
/* KeywordType */ .chroma .kt { color:#005a5f }
/* Name */ .chroma .n {  }
/* NameAttribute */ .chroma .na {  }
/* NameBuiltin */ .chroma .nb { color:#8f0075 }
/* NameBuiltinPseudo */ .chroma .bp {  }
/* NameClass */ .chroma .nc {  }
/* NameConstant */ .chroma .no {  }
/* NameDecorator */ .chroma .nd {  }
/* NameEntity */ .chroma .ni {  }
/* NameException */ .chroma .ne {  }
/* NameFunction */ .chroma .nf { color:#721045 }
/* NameFunctionMagic */ .chroma .fm {  }
/* NameLabel */ .chroma .nl {  }
/* NameNamespace */ .chroma .nn {  }
/* NameOther */ .chroma .nx {  }
/* NameProperty */ .chroma .py {  }
/* NameTag */ .chroma .nt {  }
/* NameVariable */ .chroma .nv { color:#00538b }
/* NameVariableClass */ .chroma .vc {  }
/* NameVariableGlobal */ .chroma .vg {  }
/* NameVariableInstance */ .chroma .vi {  }
/* NameVariableMagic */ .chroma .vm {  }
/* Literal */ .chroma .l { color:#0000c0 }
/* LiteralDate */ .chroma .ld { color:#0000c0 }
/* LiteralString */ .chroma .s { color:#2544bb }
/* LiteralStringAffix */ .chroma .sa { color:#2544bb }
/* LiteralStringBacktick */ .chroma .sb { color:#2544bb }
/* LiteralStringChar */ .chroma .sc { color:#2544bb }
/* LiteralStringDelimiter */ .chroma .dl { color:#2544bb }
/* LiteralStringDoc */ .chroma .sd { color:#2544bb }
/* LiteralStringDouble */ .chroma .s2 { color:#2544bb }
/* LiteralStringEscape */ .chroma .se { color:#2544bb }
/* LiteralStringHeredoc */ .chroma .sh { color:#2544bb }
/* LiteralStringInterpol */ .chroma .si { color:#2544bb }
/* LiteralStringOther */ .chroma .sx { color:#2544bb }
/* LiteralStringRegex */ .chroma .sr { color:#2544bb }
/* LiteralStringSingle */ .chroma .s1 { color:#2544bb }
/* LiteralStringSymbol */ .chroma .ss { color:#2544bb }
/* LiteralNumber */ .chroma .m { color:#0000c0 }
/* LiteralNumberBin */ .chroma .mb { color:#0000c0 }
/* LiteralNumberFloat */ .chroma .mf { color:#0000c0 }
/* LiteralNumberHex */ .chroma .mh { color:#0000c0 }
/* LiteralNumberInteger */ .chroma .mi { color:#0000c0 }
/* LiteralNumberIntegerLong */ .chroma .il { color:#0000c0 }
/* LiteralNumberOct */ .chroma .mo { color:#0000c0 }
/* Operator */ .chroma .o { color:#00538b }
/* OperatorWord */ .chroma .ow { color:#00538b }
/* Punctuation */ .chroma .p {  }
/* Comment */ .chroma .c { color:#505050 }
/* CommentHashbang */ .chroma .ch { color:#505050 }
/* CommentMultiline */ .chroma .cm { color:#505050 }
/* CommentSingle */ .chroma .c1 { color:#505050 }
/* CommentSpecial */ .chroma .cs { color:#505050 }
/* CommentPreproc */ .chroma .cp { color:#505050 }
/* CommentPreprocFile */ .chroma .cpf { color:#505050 }
/* Generic */ .chroma .g {  }
/* GenericDeleted */ .chroma .gd {  }
/* GenericEmph */ .chroma .ge {  }
/* GenericError */ .chroma .gr {  }
/* GenericHeading */ .chroma .gh {  }
/* GenericInserted */ .chroma .gi {  }
/* GenericOutput */ .chroma .go {  }
/* GenericPrompt */ .chroma .gp {  }
/* GenericStrong */ .chroma .gs {  }
/* GenericSubheading */ .chroma .gu {  }
/* GenericTraceback */ .chroma .gt {  }
/* GenericUnderline */ .chroma .gl {  }
/* TextWhitespace */ .chroma .w {  }
```

Avec le filtre `minify`, les commentaires sont supprimés, mais pas les instructions vides.
On pourrait supprimer toutes les lignes avec des `{ }` avant le passage par la minification.
**Je regrette que `minify` ne supprime pas ces instructions vides!**

Nous aurions donc:

```
/* Background */ .bg { color:#000;background-color:#fff; }
/* PreWrapper */ .chroma { color:#000;background-color:#fff; }
/* LineLink */ .chroma .lnlinks { outline:none;text-decoration:none;color:inherit }
/* LineTableTD */ .chroma .lntd { vertical-align:top;padding:0;margin:0;border:0; }
/* LineTable */ .chroma .lntable { border-spacing:0;padding:0;margin:0;border:0; }
/* LineHighlight */ .chroma .hl { background-color:#e5e5e5 }
/* LineNumbersTable */ .chroma .lnt { white-space:pre;-webkit-user-select:none;user-select:none;margin-right:0.4em;padding:0 0.4em 0 0.4em;color:#7f7f7f }
/* LineNumbers */ .chroma .ln { white-space:pre;-webkit-user-select:none;user-select:none;margin-right:0.4em;padding:0 0.4em 0 0.4em;color:#7f7f7f }
/* Line */ .chroma .line { display:flex; }
/* Keyword */ .chroma .k { color:#5317ac }
/* KeywordConstant */ .chroma .kc { color:#0000c0 }
/* KeywordDeclaration */ .chroma .kd { color:#5317ac }
/* KeywordNamespace */ .chroma .kn { color:#5317ac }
/* KeywordPseudo */ .chroma .kp { color:#5317ac }
/* KeywordReserved */ .chroma .kr { color:#5317ac }
/* KeywordType */ .chroma .kt { color:#005a5f }
/* NameBuiltin */ .chroma .nb { color:#8f0075 }
/* NameFunction */ .chroma .nf { color:#721045 }
/* NameVariable */ .chroma .nv { color:#00538b }
/* Literal */ .chroma .l { color:#0000c0 }
/* LiteralDate */ .chroma .ld { color:#0000c0 }
/* LiteralString */ .chroma .s { color:#2544bb }
/* LiteralStringAffix */ .chroma .sa { color:#2544bb }
/* LiteralStringBacktick */ .chroma .sb { color:#2544bb }
/* LiteralStringChar */ .chroma .sc { color:#2544bb }
/* LiteralStringDelimiter */ .chroma .dl { color:#2544bb }
/* LiteralStringDoc */ .chroma .sd { color:#2544bb }
/* LiteralStringDouble */ .chroma .s2 { color:#2544bb }
/* LiteralStringEscape */ .chroma .se { color:#2544bb }
/* LiteralStringHeredoc */ .chroma .sh { color:#2544bb }
/* LiteralStringInterpol */ .chroma .si { color:#2544bb }
/* LiteralStringOther */ .chroma .sx { color:#2544bb }
/* LiteralStringRegex */ .chroma .sr { color:#2544bb }
/* LiteralStringSingle */ .chroma .s1 { color:#2544bb }
/* LiteralStringSymbol */ .chroma .ss { color:#2544bb }
/* LiteralNumber */ .chroma .m { color:#0000c0 }
/* LiteralNumberBin */ .chroma .mb { color:#0000c0 }
/* LiteralNumberFloat */ .chroma .mf { color:#0000c0 }
/* LiteralNumberHex */ .chroma .mh { color:#0000c0 }
/* LiteralNumberInteger */ .chroma .mi { color:#0000c0 }
/* LiteralNumberIntegerLong */ .chroma .il { color:#0000c0 }
/* LiteralNumberOct */ .chroma .mo { color:#0000c0 }
/* Operator */ .chroma .o { color:#00538b }
/* OperatorWord */ .chroma .ow { color:#00538b }
/* Comment */ .chroma .c { color:#505050 }
/* CommentHashbang */ .chroma .ch { color:#505050 }
/* CommentMultiline */ .chroma .cm { color:#505050 }
/* CommentSingle */ .chroma .c1 { color:#505050 }
/* CommentSpecial */ .chroma .cs { color:#505050 }
/* CommentPreproc */ .chroma .cp { color:#505050 }
/* CommentPreprocFile */ .chroma .cpf { color:#505050 }
```

Mais comme la même couleur est souvent utilisée, on peut valoir la peine de restruturer la feuille de style avec un outil comme [CSSO](https://css.github.io/csso/csso.html).

En version bien mise en page:

```
.bg,.chroma {
    color: #000;
    background-color: #fff
}

.chroma .lnlinks {
    outline: 0;
    text-decoration: none;
    color: inherit
}

.chroma .lntd {
    vertical-align: top;
    padding: 0;
    margin: 0;
    border: 0
}

.chroma .lntable {
    border-spacing: 0;
    padding: 0;
    margin: 0;
    border: 0
}

.chroma .hl {
    background-color: #e5e5e5
}

.chroma .ln,.chroma .lnt {
    white-space: pre;
    -webkit-user-select: none;
    user-select: none;
    margin-right: .4em;
    padding: 0 .4em;
    color: #7f7f7f
}

.chroma .line {
    display: flex
}

.chroma .k {
    color: #5317ac
}

.chroma .kc {
    color: #0000c0
}

.chroma .kd,.chroma .kn,.chroma .kp,.chroma .kr {
    color: #5317ac
}

.chroma .kt {
    color: #005a5f
}

.chroma .nb {
    color: #8f0075
}

.chroma .nf {
    color: #721045
}

.chroma .nv {
    color: #00538b
}

.chroma .l,.chroma .ld {
    color: #0000c0
}

.chroma .dl,.chroma .s,.chroma .s1,.chroma .s2,.chroma .sa,.chroma .sb,.chroma .sc,.chroma .sd,.chroma .se,.chroma .sh,.chroma .si,.chroma .sr,.chroma .ss,.chroma .sx {
    color: #2544bb
}

.chroma .il,.chroma .m,.chroma .mb,.chroma .mf,.chroma .mh,.chroma .mi,.chroma .mo {
    color: #0000c0
}

.chroma .o,.chroma .ow {
    color: #00538b
}

.chroma .c,.chroma .c1,.chroma .ch,.chroma .cm,.chroma .cp,.chroma .cpf,.chroma .cs {
    color: #505050
} 
```

En version minifiée:

```
.bg,.chroma{color:#000;background-color:#fff}.chroma .lnlinks{outline:0;text-decoration:none;color:inherit}.chroma .lntd{vertical-align:top;padding:0;margin:0;border:0}.chroma .lntable{border-spacing:0;padding:0;margin:0;border:0}.chroma .hl{background-color:#e5e5e5}.chroma .ln,.chroma .lnt{white-space:pre;-webkit-user-select:none;user-select:none;margin-right:.4em;padding:0 .4em;color:#7f7f7f}.chroma .line{display:flex}.chroma .k{color:#5317ac}.chroma .kc{color:#0000c0}.chroma .kd,.chroma .kn,.chroma .kp,.chroma .kr{color:#5317ac}.chroma .kt{color:#005a5f}.chroma .nb{color:#8f0075}.chroma .nf{color:#721045}.chroma .nv{color:#00538b}.chroma .l,.chroma .ld{color:#0000c0}.chroma .dl,.chroma .s,.chroma .s1,.chroma .s2,.chroma .sa,.chroma .sb,.chroma .sc,.chroma .sd,.chroma .se,.chroma .sh,.chroma .si,.chroma .sr,.chroma .ss,.chroma .sx{color:#2544bb}.chroma .il,.chroma .m,.chroma .mb,.chroma .mf,.chroma .mh,.chroma .mi,.chroma .mo{color:#0000c0}.chroma .o,.chroma .ow{color:#00538b}.chroma .c,.chroma .c1,.chroma .ch,.chroma .cm,.chroma .cp,.chroma .cpf,.chroma .cs{color:#505050}
```

Entre la version générée par `hugo gen` et la version finale, on économise 75% de poids!

----

Cet article sera remis à une une fois ces recettes appliquées à mon site.
