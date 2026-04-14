# 🎮 Interface de Jeu — `feature/jeu`

> Module responsable de l'affichage et de la logique du jeu interactif.  
> Branche : `feature/jeu` | Auteur : BISSEMOU CHARMANT

---

## 📁 Fichiers de cette branche

```
game.html   → Structure des écrans du jeu
game.css    → Styles et animations de l'interface
game.js     → Logique complète du jeu
```

---

## 🧩 Rôle de ce module

Ce module gère **tout ce que le joueur voit et vit pendant la partie** :

- L'écran de bienvenue avec les règles
- L'affichage des questions une par une
- Le timer animé par question
- La saisie et validation des réponses
- Le système de score et de vies
- Les effets sonores
- L'écran de fin avec les statistiques

Ce module **dépend** de deux autres branches :
| Dépendance | Branche | Fichier |
|---|---|---|
| Questions du jeu | `feature-questiont/réponse` | `data.js` |
| Validation IA | `feature/api-ia` | `validator.js` |
or.js
---

## 📄 Détail des fichiers

### `game.html`
Structure HTML des 3 écrans du jeu :
- **Écran Welcome** : pseudo, catégorie, niveau, règles
- **Écran de jeu** : timer, score, vies, question, input, boutons
- **Écran de fin** : résultats, stats, boutons rejouer/accueil/classement

### `game.css`
Styles complets de l'interface :
- Overlay et cartes animées (popIn, fadeIn, slideIn)
- Timer SVG avec anneau de progression coloré
- Barre de progression des questions
- Input avec effets correct (vert) / wrong (rouge + shake)
- Animations de victoire (pétales 🌸) et défaite (confetti 💀)
- Score pop animé (+pts)
- Responsive mobile

### `game.js`
Logique complète du jeu :
- Lecture du pseudo/catégorie/niveau depuis `sessionStorage`
- Configuration par niveau (questions, timer, vies, points)
- Mélange aléatoire des questions (`shuffle`)
- Gestion du timer avec alerte visuelle et sonore
- Validation des réponses via `validateWithAI()` (P4)
- Calcul du score avec bonus de rapidité
- Effets sonores via Web Audio API
- Animation canvas en arrière-plan

---

## ⚙️ Configuration des niveaux

| Niveau | Questions | Timer | Vies | Pts/réponse | Pts charade |
|---|---|---|---|---|---|
| Facile | 10 | 45s | 1 | 10 pts | 15 pts |
| Moyen | 15 | 35s | 3 | 15 pts | 20 pts |
| Difficile | 20 | 25s | 5 | 20 pts | 25 pts |

> Le **bonus de rapidité** est calculé ainsi :  
> `bonus = floor((timer - tempsUtilisé) / timer * 10)`  
> Il est annulé si le joueur a utilisé un indice.

---

## 🚀 Tester ce module localement

```bash
# 1. Cloner le repo et aller sur la bonne branche
git clone https://github.com/przscaslessembala-ai/Jeu-de-Devinette-Charade-nigme-.git
cd Jeu-de-Devinette-Charade-nigme-
git checkout feature/jeu

# 2. Récupérer les branches des autres membres
git fetch --all
git merge origin/feature/data
git merge origin/feature/validator

# 3. Ouvrir game.html avec Live Server (VS Code)
```

> ⚠️ Sans `feature-questiont/réponse/data.js` et `feature/api-ia/validator.js`, le jeu ne peut pas fonctionner.

---

## 📝 Commits de cette branche

```
feat(jeu): ajouter la structure HTML des écrans welcome, jeu et fin
style(jeu): ajouter les styles de l'interface de jeu et animations
feat(jeu): ajouter la logique du jeu (timer, score, vies, sons, feedback)
docs(jeu): ajouter le README de la branche feature/jeu
```

---

## ✍️ Auteur

**BISSEMOU CHARMANT** — Responsable de l'interface et logique de jeu  
Branche : `feature/jeu`
