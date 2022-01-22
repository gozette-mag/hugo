# Gozette

## Faire un nouveau article

Aller sur Github pour créer un nouveau fichier dans `/content/posts` : [https://github.com/gozette-mag/hugo/tree/main/content/posts](https://github.com/gozette-mag/hugo/tree/main/content/posts). 

1. Cliquer sur "Add File" puis sur create new file.
2. Appeler le nouveau fichier comme vous voulez, je recommande `YYYYMMDD-mon-titre.md`. Ce qui est important : pas de caractères de merde (pas d'accents, pas d'espaces, etc.) et extension `.md`. Par exemple `20220101-la-gozette-sur-le-web-c-est-cool.md`.
3. Le nouveau fichier doit contenir un "en-tête" avec les infos pertinentes. Voici un exemple : 

```markdown
---
title: My First Post
date: 2022-01-22
author: Author Name
feature_image: /img/cover.jpg
tags:
  - tag1
  - tag2
numeros: 
  - 1
draft: false
---
```
Quelques explications : 
- `title` : Le titre de l'article tel que vous voulez le voir apparaitre sur la page
- `date` : La date de publication
- `author` : Le nom de l'auteur
- `feature_image` : l'image que vous voulez faire apparaitre en haut et dans les vignettes (voir ci-dessous pour ajouter de nouvelles images)
- `tags` : Des mots clés liés à votre article
- `numeros` : Les numéros de la gozette dans lesquels l'article apparait
- `draft` : si votre article est un brouillon et ne doit pas encore être publié

4. en dessous de cet en-tête vous pouvez écrire votre article avec la syntaxe Markdown : [https://www.markdownguide.org/basic-syntax/](https://www.markdownguide.org/basic-syntax/)
5. Cliquez sur "Commit new file" pour sauvegarder l'article, il sera en ligne (si `draft` à true) d'ici quelques minutes.

## Ajouter une image
Pour ajouter une image il faut le faire en deux étapes. D'abord il faut l'uploader puis vous pourrez l'utiliser dans votre article.

### Uploader l'image

1. Allez dans `static/img` : [https://github.com/gozette-mag/hugo/tree/main/static/img](https://github.com/gozette-mag/hugo/tree/main/static/img)
2. Cliquez sur "Add File" puis sur upload file
3. Choisissez la/les images à uploader
4. Cliquez sur commit changes pour faire l'upload

### utilisez l'image dans un article
Pour l'ajouter comme `feature_image`, il suffit de mettre son chemin : `/img/mon-image.jpg`.

Pour l'utiliser dans un article il suffit d'utiliser cette syntaxe : 

```markdown
![Texte pour les malvoyants et quand l'image ne se charge pas](/img/mon-image.jpg)
``` 
