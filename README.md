# Jeu-de-Devinette-Charade-Enigme

Votre divertissement notre priorité

\# Jeu de Devinette Charade Nigme



\## Mes contributions au projet



\---



\## Branche : `feature/api-ia`



Cette branche gère la validation intelligente des réponses du joueur

grâce à l'intelligence artificielle (Claude API d'Anthropic).



\### Fichiers créés



\#### `validator.js`

Fichier principal de validation des réponses.

\- Envoie la réponse du joueur à Claude API pour vérification

\- Claude accepte les synonymes, fautes d'orthographe mineures,

&#x20; réponses partielles et pluriels/singuliers

\- Si l'API est inaccessible, un système de secours local prend le relais

\- Le fallback local utilise l'algorithme de Levenshtein pour détecter

&#x20; les réponses proches

\- Fonction principale : `validateWithAI(userAnswer, expectedAnswer)`

&#x20; retourne `true` si la réponse est correcte, `false` sinon



\#### `config.js` ⚠️ (non envoyé sur GitHub)

Fichier de configuration locale qui contient la clé API secrète.

\- Contient la clé Claude API personnelle

\- Ignoré par Git grâce au `.gitignore` pour protéger la clé

\- Chaque membre de l'équipe doit créer son propre `config.js`

&#x20; en se basant sur `config.exemple.js`



\#### `config.exemple.js`

Modèle de configuration à partager avec l'équipe.

\- Montre la structure du fichier `config.js`

\- Contient `METS\_TA\_CLE\_ICI` à la place de la vraie clé

\- Ce fichier est envoyé sur GitHub sans danger



\#### `.gitignore`

Fichier qui dit à Git quels fichiers ne pas envoyer sur GitHub.

\- Ignore `config.js` pour protéger la clé API

\- Empêche toute exposition accidentelle de données sensibles



\---



\## Branche : `feature/leaderboard`



Cette branche gère l'affichage du classement des joueurs dans le jeu.



\### Fichiers créés



\#### `leaderboard.css`

Fichier de style pour la page du classement.

\- Définit l'apparence visuelle du tableau des scores

\- Mise en forme des rangs, noms et points des joueurs



\---





