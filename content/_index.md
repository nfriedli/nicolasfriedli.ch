---
title: Nicolas Friedli
date: 2019-11-10
---

Texte

Lorsqu'on réalise des maquettes ou des modèles de mise en page, on a souvent besoin de générer [automatiquement](#) du faux texte pour avoir une idée plus précise de l'aspect final qu'auront les documents et présentations. Voici comment faire sous Word 2007, PowerPoint 2007 et Excel 2007.

et code

```go-html-template
<section id="main">
  <div>
    <h1 id="title">{{ .Title }}</h1>
    {{ range .Pages }}
      {{ .Render "summary"}}
    {{ end }}
  </div>
</section>
```

```css
html {
    color: #444;
    background: white;
    font-size: 20px;
    line-height: 1.5;
    font-variant-ligatures: common-ligatures;
    text-rendering: optimizeLegibility;
    font-variant-numeric: oldstyle-nums proportional-nums;
}
```

```sass
html {
    color: #444;
    background: white;
    font-size: 20px;
    line-height: 1.5;
    font-variant-ligatures: common-ligatures;
    text-rendering: optimizeLegibility;
    font-variant-numeric: oldstyle-nums proportional-nums;
}
```