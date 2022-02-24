---
title: La nouvelle Gozette et ses fonctionalités
date: 2022-02-24
lastmod: 2022-02-24
author: Nicotupe
# avatar: /img/author.jpg
# authorlink: https://author.site
feature_image: /img/cover.jpg
# images:
#   - /img/cover.jpg
categories:
  - news
tags:
  - gozette
numeros: 
  - 3
mathjax: true
# nolastmod: true
draft: false
---

Ce mois-ci, pour son troisième numéro, la Gozette s'est faite une nouvelle beauté, elle s'est exilée en ligne sur ce blog et avec un nom de domaine tous neuf : gozette.fr

Au dela d'être en ligne, la nouvelle gozette intègre plein de nouvelles fonctionalités présentées ici.

<!--more-->

## Markdown

D'abord pour écrire des articles dans la nouvelle Gozette on utilse le [Markdown](https://www.markdownguide.org/basic-syntax/). C'est une syntaxe qui permet de très rapidement écrire un texte avec un minimum de mise en page. Par exemple, pour faire un titre comme le "Markdown" écrit ci-dessus, il vout suffit d'écrire : 

```markdown
## Markdown
```

Et vous avez bien sûr plusieurs niveaux de titres  : 

```markdown
# Titre de niveau 1
## Titre de niveau 2
### Titre de niveau 3
```

Il est aussi très facile d'intégrer des images a partir de leur lien : 

```markdown
![](https://chemin/de/votre/image.jpg)
```

Allez voir [ce guide](https://www.markdownguide.org/basic-syntax/) si ça vous intéresse!

## Go

On est un blog de Go donc on est intéressés partager des parties. Et justement ce blog permet de faire ça très facilement. Par exemple si vous avez joué sur OGS, vous pouvez a partir du lien : [https://online-go.com/game/41397912](https://online-go.com/game/41397912) l'afficher dans le blog avec cette commande : 

```markdownㅤㅤㅤ
{ {< ogs 41397912 5 >} }
```

(le `5` est le move que vous voulez afficher).

Et ça donne ça : 

{{< ogs 41397912 5 >}}



