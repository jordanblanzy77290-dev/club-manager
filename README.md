# Club Manager

Application de gestion des clubs de badminton : challenge interne, SmashRoulette, tournoi, Choc des volants, joueurs.

**Site :** https://jordanblanzy77290-dev.github.io/club-manager/

## Comment c'est construit

- **Le code est public, les données ne le sont pas.** Ce dépôt ne contient que l'appli (`index.html`). Aucun joueur, aucun score, aucun mot de passe n'y figure.
- **Les données sont dans Firebase** (projet `club-manager-6301b`, base Firestore à Paris). Chaque club a ses données à part : `clubs/<club>/…`.
- **Pour se connecter, il faut un e-mail et un mot de passe** (10 caractères au moins), avec une adresse vérifiée.
- **On n'entre dans un club que sur invitation.** L'administrateur général donne les droits rubrique par rubrique : rien, voir ou modifier. Pour le Choc des volants, il existe aussi le rôle « capitaine », qui ne saisit que les rencontres de son club et celles qu'il reçoit.
- **Le serveur contrôle chaque lecture et chaque écriture** avec les règles de [`firestore.rules`](firestore.rules). L'appli ne fait qu'afficher ce que la personne a le droit de voir.
- **L'administrateur général** est déclaré à la main dans la console Firebase (collection `admins`). Personne ne peut se l'attribuer depuis l'appli.

## Fichiers

| Fichier | Rôle |
|---|---|
| `index.html` | L'appli complète (une seule page), générée depuis la source de Club Manager. |
| `firestore.rules` | Les règles de sécurité de la base, à coller dans Firestore › Règles. |

Ne modifie pas `index.html` à la main : il est régénéré à chaque version.
