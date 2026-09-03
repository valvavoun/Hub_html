<div align="center">

<img src="./favicon.png" width="72" alt="Logo Valvavoun" />

# ⚡ Valvavoun HUB

**Un hub centralisé pour héberger et découvrir mes mini-outils web**

[![GitHub Pages](https://img.shields.io/badge/deploy-GitHub%20Pages-5eead4?style=flat-square&logo=github)](https://valvavoun.github.io/Hub_html/)
[![Status](https://img.shields.io/badge/status-live-ffb020?style=flat-square)](https://valvavoun.github.io/Hub_html/)
[![License](https://img.shields.io/badge/license-MIT-7e93ab?style=flat-square)](#-licence)

[🔗 Voir le hub en ligne](https://valvavoun.github.io/Hub_html/)

</div>

---

## ✨ À propos

**Valvavoun HUB** est une page d'accueil unique qui référence automatiquement tous les petits outils/projets web contenus dans ce dépôt. Pas besoin de mettre à jour manuellement une liste de liens : le hub interroge l'API GitHub au chargement, détecte chaque dossier de projet à la racine, lit son `meta.json` et génère une carte cliquable — le tout avec un style "blueprint" néon fait maison.

> Ajoute un dossier avec un `index.html` (ou l'entrée définie dans `meta.json`) → recharge la page → le projet apparaît. C'est tout.

---

## 🧩 Projets disponibles

| Projet | Description | Statut |
|---|---|---|
| ⏱️ **Minutage** | Calcule le temps total de visionnage d'une série | 🟢 En ligne |
| 📺 **Multitwitch** | Regarde plusieurs streams Twitch en simultané | 🟢 En ligne |
| ☀️ **Calculateur solaire** | Détermine la meilleure orientation pour minimiser l'exposition au soleil | 🟢 En ligne |
| 🏍️ **MXGP Livetiming** *(externe)* | Classements en temps réel MXGP | 🟢 En ligne |

---

## 🛠️ Comment ça marche

Le hub (`index.html`) exécute cette logique à chaque visite :

```
1. Appel API GitHub  →  liste les dossiers présents à la racine du dépôt
2. Pour chaque dossier  →  lecture de son meta.json (via raw.githubusercontent.com)
3. Vérification  →  le fichier d'entrée (entry) répond bien en HEAD
4. Rendu  →  génération d'une carte projet avec nom, description, tags et statut
```

Un cache local de 5 minutes (`localStorage`) évite de sur-solliciter l'API GitHub lors des rechargements successifs.

---

## ➕ Ajouter un nouveau projet

1. Crée un dossier à la racine du dépôt (ex. `mon-outil/`)
2. Place ton fichier principal dedans (ex. `mon-outil/index.html`)
3. Ajoute un fichier `meta.json` à la racine de ce dossier :

```json
{
  "name": "Nom affiché",
  "desc": "Description courte du projet",
  "tags": ["Tag1", "Tag2"],
  "status": "live",
  "entry": "index.html"
}
```

| Champ | Requis | Description |
|---|:---:|---|
| `name` | non | Nom affiché sur la carte (sinon déduit du nom du dossier) |
| `desc` | non | Description courte |
| `tags` | non | Liste de mots-clés affichés en badges |
| `status` | non | `"live"` ou `"dev"` — change le point de couleur |
| `entry` | non | Fichier HTML à ouvrir (par défaut `index.html`) |

4. Push sur la branche `main` → le projet apparaît automatiquement sur le hub (après expiration du cache de 5 min).

> 💡 Les dossiers `.github`, `.git`, `assets`, `img` et `images` sont ignorés par le scanner.

---

## 📁 Structure du dépôt

```
Hub_html/
├── index.html          # Page d'accueil (le hub)
├── favicon.png
├── _nojekyll            # Désactive le traitement Jekyll de GitHub Pages
│
├── minutage/
│   ├── minutage.html
│   └── meta.json
│
├── multistream/
│   ├── multistream.html
│   └── meta.json
│
└── ombre-route/
    ├── ombre-route.html
    └── meta.json
```

---

## 🎨 Stack technique

- **HTML / CSS / JS vanilla** — aucun framework, aucune dépendance de build
- **GitHub API + raw.githubusercontent.com** pour la découverte dynamique des projets
- **GitHub Pages** pour l'hébergement
- Police **Space Grotesk** / **JetBrains Mono** / **Inter** via Google Fonts

---

## 🚀 Déploiement

Le dépôt est servi directement via **GitHub Pages** depuis la branche `main`.
Le fichier `_nojekyll` empêche GitHub de traiter le site avec Jekyll (utile car certains dossiers commencent par `_` ou contiennent des fichiers non standards).

```
Réglages du dépôt → Pages → Source: branche "main" → dossier "/ (root)"
```

---

## 📄 Licence

Distribué sous licence MIT — libre à toi de réutiliser, modifier et redistribuer.

---

<div align="center">
<sub>Fait avec 🧡 par <a href="https://github.com/valvavoun">valvavoun</a></sub>
</div>
