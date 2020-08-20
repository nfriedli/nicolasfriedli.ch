---
title: Fil d'Ariane récursif avec Hugo
date: 2020-08-20
description: 
---

Question fréquente sur les forums. On attaque avec la solution toute cuite:

```go-html-template
{{ with .Parent }} {{ if .URL }}{{ if .URL }}{{ if .URL }} {{ if .URL }}
    {{ if .URL }}
    {{ end }}
{{ end }}
```