# Exercice Git en équipe

Un atelier pratique : cloner, valider, pousser, tirer, résoudre un conflit, puis passer aux branches et aux pull requests. Nous partons tous du même dépôt — suivez les phases dans l'ordre.

## Avant de commencer (la veille)

- Installez Git — vérifiez avec `git --version`
- Configurez votre identité :
  ```bash
  git config --global user.name "Votre Nom"
  git config --global user.email "vous@exemple.com"
  ```
- Vérifiez votre accès au dépôt (clé SSH ou jeton) en le clonant avant la séance.

## Phase 1 — Cloner, valider, pousser

```bash
git clone <URL-DU-DÉPÔT>
cd <dossier-du-dépôt>
```

Créez un fichier à votre nom (ex. `alice.txt`), puis :

```bash
git add alice.txt
git commit -m "Ajouter Alice"
git push
```

La première personne qui pousse réussit ; les autres sont *refusés* car le dépôt distant a de l'avance. C'est normal — tirez, puis poussez :

```bash
git pull
git push
```

Chacun ayant créé un fichier différent, Git fusionne tout seul. **Toujours tirer avant de pousser.**

## Phase 2 — Résoudre un conflit de fusion

Cette fois, tout le monde modifie la *même ligne*, exprès. Ouvrez `team-roster.md`, changez la ligne de la devise (marquée TODO), puis :

```bash
git add team-roster.md
git commit -m "Ajouter notre devise"
git push
```

Le premier push passe ; le suivant déclenche un *conflit* au moment de tirer. Git le marque ainsi :

```
<<<<<<< HEAD
votre version
=======
la version distante
>>>>>>> origin/main
```

Pour le résoudre : choisissez le texte final, supprimez les trois lignes de marqueurs (`<<<<<<<`, `=======`, `>>>>>>>`), puis :

```bash
git add team-roster.md
git commit
git push
```

C'est la compétence clé de l'exercice.

## Phase 3 — Branches et pull requests

Modifier `main` directement, c'est justement *pourquoi* la Phase 2 a fait mal. On isole plutôt son travail sur une branche :

```bash
git checkout -b feature/votrenom
git push -u origin feature/votrenom
```

Ouvrez ensuite une Pull Request (ou Merge Request) dans l'interface web, faites relire par un collègue, puis fusionnez. C'est le flux du quotidien.

## Bloqué ?

`git status` vous dit presque toujours quoi faire ensuite. Voir aussi l'aide-mémoire.
