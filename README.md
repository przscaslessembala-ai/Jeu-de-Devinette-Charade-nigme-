# 🏆 Leaderboard — Devinettes & Énigmes

Classement en ligne en temps réel pour le jeu **Devinettes & Énigmes**.  
Connecté à **Firebase Firestore** avec un fallback automatique sur `localStorage`.

-----

## 📁 Structure des fichiers

```
├── leaderboard.html        # Page du classement
├── js/
│   └── leaderboard.js      # Logique complète (chargement, envoi, filtres, rendu)
└── css/
    └── leaderboard.css     # Styles dédiés au classement
```

-----

## ✨ Fonctionnalités

- 🥇 **Podium animé** pour le top 3
- 📋 **Tableau des 50 meilleurs scores**
- 🔍 **Filtres** par période, niveau et catégorie
- 📤 **Soumission automatique** du score après une partie
- 💾 **Fallback localStorage** si Firebase est inaccessible
- 🎨 **Fond animé** avec particules canvas (emojis flottants)

-----

## ⚙️ Prérequis

- Un projet **Firebase** avec **Firestore** activé
- Remplacer la `firebaseConfig` dans `js/leaderboard.js` par vos propres clés :

```js
const firebaseConfig = {
  apiKey:            'VOTRE_API_KEY',
  authDomain:        'votre-projet.firebaseapp.com',
  projectId:         'votre-projet',
  storageBucket:     'votre-projet.firebasestorage.app',
  messagingSenderId: 'XXXXXXXX',
  appId:             'XXXXXXXX'
};
```

-----

## 🎮 Intégration avec le jeu

Pour soumettre automatiquement un score depuis une partie, stocker ces valeurs dans `sessionStorage` **avant** de rediriger vers `leaderboard.html` :

```js
sessionStorage.setItem('pseudo',       'NomDuJoueur');
sessionStorage.setItem('lastScore',    '42');
sessionStorage.setItem('lastLevel',    'facile');     // facile | moyen | difficile
sessionStorage.setItem('lastCategory', 'devinette'); // devinette | charade | enigme
```

Le script détecte ces valeurs au chargement et envoie le score automatiquement.  
Si le joueur a déjà un score pour ce niveau/catégorie, **seul le meilleur score est conservé**.

-----

## 🔍 Filtres disponibles

|Filtre   |Options                                    |
|---------|-------------------------------------------|
|Période  |Tous / Aujourd’hui / Semaine / Mois        |
|Niveau   |Tous / 🟢 Facile / 🟡 Moyen / 🔴 Difficile    |
|Catégorie|Toutes / 💡 Devinette / 🔤 Charade / 🔮 Énigme|

-----

## 🔒 Sécurité

> ⚠️ La clé API Firebase visible dans le code est normale pour le SDK web côté client.  
> Cependant, il est **indispensable** de configurer les **règles Firestore** pour limiter les écritures non autorisées.

Exemple de règles Firestore recommandées :

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /scores/{document} {
      allow read: if true;
      allow write: if request.resource.data.score is number
                   && request.resource.data.pseudo is string
                   && request.resource.data.pseudo.size() <= 20;
    }
  }
}

