# Admin jeux (Vercel + GitHub)

Pour que la page **admin** et l’API fonctionnent sur Vercel, configure ces variables d’environnement dans le projet Vercel.

## 1. Variables dans Vercel

Dans ton projet Vercel : **Settings → Environment Variables**, ajoute :

| Variable         | Description | Exemple |
|------------------|-------------|--------|
| `GITHUB_REPO`    | Repo où est le site (et `games.json`) | `ton-user/807shopc-main` |
| `GITHUB_BRANCH`  | Branche (optionnel, défaut: `main`) | `main` |
| `GITHUB_TOKEN`   | Token GitHub avec droit d’écriture sur ce repo | `ghp_xxxx...` |
| `ADMIN_PASSWORD` | Mot de passe pour accéder à la page admin | un mot de passe fort |

## 2. Créer un token GitHub

1. GitHub → **Settings** (ton profil) → **Developer settings** → **Personal access tokens**.
2. **Generate new token (classic)**.
3. Coche au minimum : **repo** (accès complet aux repos).
4. Génère et copie le token. Colle-le dans `GITHUB_TOKEN` sur Vercel (sans le partager).

## 3. Repo et fichier `games.json`

- Le site doit être déployé depuis un repo GitHub (ex. `807shopc-main`).
- Le fichier **`games.json`** doit être à la racine de ce repo (il est déjà dans le projet).
- `GITHUB_REPO` = exactement `utilisateur/nom-du-repo` (ex. `johndoe/807shopc-main`).

## 4. Utilisation

- **Page admin :** `https://ton-site.vercel.app/admin.html`
- Connecte-toi avec le mot de passe défini dans `ADMIN_PASSWORD`.
- Ajoute un jeu : après envoi, il est écrit dans `games.json` sur GitHub. Tous les visiteurs voient le nouveau jeu au prochain chargement.

Pas de base de données, tout est stocké dans le repo (gratuit, utilisation très large).
