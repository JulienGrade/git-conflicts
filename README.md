## Résoudre un conflit de fusion

Un conflit de fusion intervient lorsque l'on tente de fusionner deux branches qui modifient la même partie d'un même fichier. Dans ce cas, `git` va intégrer les deux versions dans le même fichier puis laisser le développeur décider du contenu final de cette partie.

L'objectif de ce tuto est d'apprendre à résoudre un conflit de fusion. (*merge conflict*)

Pour cela, nous allons devoir commencer par en causer un !

### Procédure pour causer un conflit de fusion

Étapes à suivre, une par une:

1. Créer un nouveau dépôt sur GitHub
2. Dans le répertoire du dépôt local, créer un fichier `README.md` contenant les paroles d'une chanson de votre choix
3. Créer un commit initial sur la banche master et l'envoyer sur GitHub avec `git add`, `git commit` puis `git push`
4. Créer une branche `branche1` à partir de `master`, avec `git checkout -b`
5. Dans le `README.md` de cette branche, modifier à votre guise la première phrase des paroles, créer un commit, puis envoyer les modifications de cette branche sur GitLab
6. Revenir à la branche `master` avec `git checkout`
7. Créer une branche `branche2` à partir de `master` (comme dans l'étape 5)
8. Dans le `README.md` de cette branche, modifier également la première phrase des paroles avec un texte différent de celui saisi à l'étape 6, créer un commit, puis envoyer les modifications de cette branche sur GitLab
9. Revenir à la branche `master`
10. Fusionner `branche1` dans `master`, avec `git merge`
11. Fusionner `branche2` dans `master`

Si vous avez bien suivi cette procédure, vous devriez obtenir un conflit de fusion:

```
Auto-merging README.md
CONFLICT (content): Merge conflict in README.md
Automatic merge failed; fix conflicts and then commit the result.
```

Voici ce que devrait répondre `git status`:

```
On branch master
You have unmerged paths.
  (fix conflicts and run "git commit")
  (use "git merge --abort" to abort the merge)

Unmerged paths:
  (use "git add <file>..." to mark resolution)

        both modified:   README.md
```

### Procédure pour résoudre un conflit de fusion

Pour résoudre ce conflit, il va falloir:

1. ouvrir le fichier `README.md` dans son éditeur de code,
2. constater comment `git` représente le conflit, et la source de chaque version,
3. éditer le fichier pour ne conserver que la version finale souhaitée,
4. puis créer un commit.

> Au moment du commit:
> - si vous vous retrouvez dans l'éditeur `vi`, tapez `:wq` pour quitter en sauvegardant le fichier;
> - si vous vous retrouvez dans l'éditeur `nano`, pressez `Ctrl-X` pour quitter.

Après la résolution du conflit de fusion, `git status` devrait répondre ceci:

```
On branch master
nothing to commit, working tree clean
```

### Bonus

- supprimer les branches `branche1` et `branche2`, non seulement dans votre dépôt local, mais aussi dans le dépôt distant associé (sur GitHub).