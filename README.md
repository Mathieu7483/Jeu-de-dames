<p align="center"\>
<img src="https://github.com/Mathieu7483/Jeu-de-dames/blob/main/Capture%20d'%C3%A9cran%202026-06-04%20165746.png"\>
</p>
# Jeu de Dames Professionnel — v4.0

Une implémentation web moderne et autonome du jeu de dames, développée en **HTML5**, **CSS3** (Variables & Grid) et **JavaScript Vanilla** (ES6+). Ce projet est conçu sans dépendances externes, respectant les principes de la programmation orientée objet implicite et de la manipulation directe du DOM.

## 🚀 Fonctionnalités

* **Règles officielles de capture** : Gestion des déplacements simples et priorité absolue aux captures (obligation de prendre).
* **Rafles en chaîne (Chain Capturing)** : Prise en charge des captures consécutives obligatoires avec blocage du joueur tant que la rafle n'est pas terminée.
* **Promotion en Dame** : Transformation automatique d'un pion en Dame (`King`) lorsqu'il atteint la dernière ligne adverse, débloquant les déplacements de longue portée.
* **Interface Responsive & Moderne** : Design sombre (*Dark Mode*) avec un plateau sous forme de grille CSS, effets visuels de sélection, et indications distinctes pour les mouvements simples et les captures possibles.
* **Tableau des scores** : Suivi en temps réel du nombre de pièces restantes pour chaque joueur.
* **Détection de fin de partie** : Fin de partie automatique si un joueur n'a plus de pièces ou se retrouve bloqué sans aucun coup légal disponible.

---

## 🛠️ Structure Technique & Architecture

L'application est entièrement contenue dans un seul fichier (`Jeu de dames.html`), ce qui facilite sa portabilité.

### 1. Modélisation du Plateau (State Management)

Le plateau est représenté par une matrice JavaScript (tableau de tableaux $8 \times 8$).

```javascript
let boardState = [
    [null, 'B', null, 'B', null, 'B', null, 'B'],
    // ...
    ['W', null, 'W', null, 'W', null, 'W', null]
];

```

* `null` : Case vide.
* `'W'` / `'B'` : Pions normaux (Blancs / Noirs).
* `'KW'` / `'KB'` : Dames (Kings Blancs / Kings Noirs).

### 2. Algorithme de Recherche de Coups

* **`getPlayerCaptures()`** : Scanne le plateau pour déterminer si le joueur actif possède des captures obligatoires.
* **`getPieceMoves(r, c)`** : Calcule les vecteurs de déplacement diagonaux selon le type de pièce (portée de $1$ case pour les pions, portée infinie via boucle `while` pour les Dames).

---

## 💻 Installation et Utilisation

Aucun serveur, build ou package manager (`npm`/`yarn`) n'est requis.

1. Télécharge ou copie le fichier `Jeu de dames.html`.
2. Ouvre le fichier directement dans ton navigateur web (Chrome, Firefox, Edge, Safari) :
```bash
# Exemple via le terminal (macOS/Linux)
open "Jeu de dames.html"

```


3. **Jouer** : Les Blancs commencent. Clique sur un pion pour afficher ses mouvements légaux (points verts pour un coup simple, points rouges pour une capture), puis clique sur la case de destination.

---

## 🎨 Personnalisation (Thématisation)

Les couleurs de l'interface sont centralisées dans la pseudo-classe `:root` CSS. Tu peux facilement modifier l'aspect visuel du jeu en changeant les variables suivantes :

```css
:root {
    --bg-color: #0a0f1d;          /* Fond de la page */
    --board-light: #f0d9b5;       /* Cases claires */
    --board-dark: #b58863;        /* Cases foncées */
    --pawn-white: #f5f5f5;        /* Pions blancs */
    --pawn-black: #1a1a1a;        /* Pions noirs */
    --highlight: rgba(0, 255, 128, 0.4); /* Target coup simple */
}

```

---

## 📈 Améliorations Futures Envisageables

* **Refactoring OOP** : Encapsuler l'état et la logique du jeu dans une classe JavaScript `CheckersGame` pour séparer strictement la logique métier de l'affichage (Pattern MVC).
* **Intelligence Artificielle** : Intégration d'un algorithme Minimax avec élagage Alpha-Bêta pour un mode solo contre l'ordinateur.
* **Historique des coups** : Ajout d'un système de notation des coups et d'une fonctionnalité "Annuler le coup" (*Undo*).

---

Si tu souhaites modifier la logique pour basculer sur un plateau international standard de 100 cases ($10 \times 10$) ou injecter une IA en arrière-plan, fais-le moi savoir, Mathieu. Quel est l'objectif principal de ton étape actuelle sur ce code ?
