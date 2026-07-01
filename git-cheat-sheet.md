# Aide-mémoire Git

Référence rapide des commandes du quotidien. En cas de doute : `git status`.

## Configuration (une fois)
| Commande | Rôle |
|---|---|
| `git config --global user.name "Nom"` | Définit le nom sur vos commits |
| `git config --global user.email "vous@x.com"` | Définit l'e-mail sur vos commits |
| `git config --global --list` | Affiche votre configuration actuelle |

## Démarrer
| Commande | Rôle |
|---|---|
| `git clone <url>` | Copie un dépôt distant sur votre machine |
| `git status` | Montre ce qui a changé et quoi faire ensuite |

## Le cycle quotidien
| Commande | Rôle |
|---|---|
| `git pull` | Récupère les derniers commits du dépôt distant (à faire en premier) |
| `git add <fichier>` | Indexe un fichier pour le prochain commit |
| `git add .` | Indexe toutes vos modifications |
| `git commit -m "message"` | Enregistre les modifications indexées dans un commit |
| `git push` | Envoie vos commits vers le dépôt distant |

## Branches
| Commande | Rôle |
|---|---|
| `git branch` | Liste les branches (la branche actuelle est marquée) |
| `git checkout -b <nom>` | Crée une branche et bascule dessus |
| `git checkout <nom>` | Bascule sur une branche existante |
| `git push -u origin <nom>` | Pousse une nouvelle branche et la suit |
| `git merge <nom>` | Fusionne une autre branche dans la branche actuelle |

## Conflits de fusion
| Étape | Action |
|---|---|
| 1 | Ouvrez le fichier indiqué dans le message de conflit |
| 2 | Repérez les marqueurs `<<<<<<<`, `=======`, `>>>>>>>` |
| 3 | Modifiez le texte comme il doit être — gardez une version ou combinez les deux |
| 4 | Supprimez les trois lignes de marqueurs |
| 5 | `git add <fichier>`, puis `git commit` pour terminer |

## Voir ce qui s'est passé
| Commande | Rôle |
|---|---|
| `git log --oneline` | Liste compacte des commits récents |
| `git diff` | Montre les modifications non indexées |
| `git diff --staged` | Montre ce qui va être validé |

## Corriger une erreur
| Commande | Rôle |
|---|---|
| `git restore <fichier>` | Annule les modifications non indexées d'un fichier |
| `git restore --staged <fichier>` | Retire un fichier de l'index (garde les modifications) |
| `git commit --amend` | Modifie le dernier commit (avant de pousser) |
| `git reset --hard origin/main` | Force la branche à correspondre au distant — détruit les modifications locales |

---
Règle d'or : tirez avant de pousser, validez souvent et par petits bouts, et lisez ce que `git status` vous indique.
