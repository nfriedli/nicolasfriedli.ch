---
title: Nicolas Friedli
---

Consultant web indépendant dans la région de Neuchâtel (Suisse), j’aide des institutions, des entreprises et des particuliers à être présents sur le web. J’élabore des stratégies de contenu et les applique. J’aime les sites désespérément simples, lisibles et rapides.

```html
<a href="test">texte</a>
```

```go 
// ... code
```

```go-html-template
{{ define "breadcrumb" }}
    {{ with .Parent }}
        {{ template "breadcrumb" . }}
        <a href="{{ .Permalink }}">{{ .Title }}</a> >
    {{ end }}
{{ end }}

{{ template "breadcrumb" . }} {{.Title}}
``` 

```css
html {
    margin: 0 auto;
    max-width: 66ch;
    padding: 1rem;
}