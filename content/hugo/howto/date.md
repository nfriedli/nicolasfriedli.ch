---
title: Comment afficher les dates en français?
date: 2021-04-28
description: 
images:
    - https://cdn.pixabay.com/photo/2017/06/21/21/00/calendar-2428560_960_720.jpg
---

Hugo beaucoup de qualités, notamment dans sa gestion du multilinguisme.
Malheureusement, la gestion des dates dans d'autres langues que l'anglais n'est pas fournie par défaut.

C'est une question récurrente sur le forum, anglophone.
On trouve des trace de la solution que je propose dans ici: [Dates: only in english?](https://discourse.gohugo.io/t/dates-only-in-english/1317) ou là: [Have the date displayed in french](https://discourse.gohugo.io/t/have-the-date-displayed-in-french/28106).
Je me dis que c'est une bonne idée d'en parler... en français.

## Version avec *partial*

Un bout de code à copier simplement dans un fichier, par exemple `layout/partials/date.html`:

```go-html-template
{{ $month_names := slice "janvier" "février" "mars" "avril" "mai" "juin" "juillet" "août" "septembre" "octobre" "novembre" "décembre" }}
{{ $month := sub .Date.Month 1 }}

<time datetime="{{ .Date.Format "2006-01-02"}}">
  {{ .Date.Day }}{{ if eq .Date.Day 1 }}er{{end}}&nbsp;{{ index $month_names $month }} {{ .Date.Year }}
</time>
```

Pas besoin de beaucoup d'explication:

- une *slice* comprend tous les mois en français
- on soustrait 1 (parce que la numérotation de la *slice* commence à 0)
- on affiche la date dans un code `html` correct (balise `time` et attribut `datetime` avec un format adéquat)
- on affiche le nom du mois en toutes lettres
- on ajoute *er* s'il s'agit du premier jour du mois (vous pouvez le mettre en exposant si souhaité)

Logiquement, on appelle la date dans les *templates* par:

```go-html-template
{{ partial "date" . }}
```

## Version avec *data*

Le site d'Hugo propose de gérer les dates en d'autres langues en utilisant un fichier *data*. 
C'est techniquement plus élégant. 

C'est probablement plus pertinent dans le cas où il faudrait gérer plusieurs langues.
Pour plus d'infos, en anglais: [Customize Dates](https://gohugo.io/content-management/multilingual/#customize-dates).

Sur ce site qui n'est qu'en français, je conserve ma première méthode.

## À propos des formats de date

Les bonnes pratiques Opquast sont claires: [les dates sont présentées dans des formats explicites](https://checklists.opquast.com/fr/qualiteweb/les-dates-sont-presentees-dans-des-formats-explicites).

Je préfère nettement le mois en toutes lettres au mois en abrégé.
Je n'ai aucune hésitation à afficher les années en 4 chiffres (et jamais 2).
Reste à choisir sur le nombre du jour est précédé d'un 0 quand il n'a qu'un chiffre (s'il comporte toujours 2 chiffres, j'éviterais le *er* pour le premier jour du mois).