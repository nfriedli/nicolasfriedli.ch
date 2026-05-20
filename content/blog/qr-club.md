+++
title = "Réalisation technique d'un QR Club"
description = "test"
date = 2026-05-04
draft = true
+++

Tout mettre dans la section: <https://theologique.ch/qr/>

Empêcher le référencement de ces entrées dans robots.txt

Ne pas lister les contenus dans le sitemap, le RSS, etc.:

```
[cascade]
[cascade.build]
  list = "never"
```

ou 

```
cascade:
  build:
    list: never
```

Sur la page d"accueil de la section, pas de liste des contenus, mais une explication

En bas de chaque page, générer un QR code de lien direct
Inviter celles et ceux qui le souhaitent à imprimer et partager ce lien.


{{< qr
    text="https://theologique.ch/qr/"
    level="low"
    scale=4
    targetDir="/images/"
    alt="Lien vers le QR Club ecclésial"
    loading="lazy"
/>}}

```
{{</* qr 
    text="https://theologique.ch/qr/"
    level="low"
    scale=4
    targetDir="/images/"
    alt="Lien vers le QR Club ecclésial"
    loading="lazy"
/*/>}}
```