# 93Ciné 🎬

Site de streaming HD gratuit — Films & Séries classés par genre.

---

## ✨ Fonctionnalités

- **Hero dynamique** — Film tendance du jour affiché en plein écran au lancement
- **12 catégories** — Action, Comédie, Drame, Horreur, Sci-Fi, Romance, Thriller, Animation, Aventure, Crime, Histoire
- **Onglets Films / Séries** — Quand tu cliques sur un genre, tu bascules entre films et séries du même genre
- **4 serveurs vidéo** — VidSrc, 2Embed, MultiEmbed, VidLink (changeable si un serveur ne fonctionne pas)
- **Recherche en temps réel** — Résultats instantanés pendant la frappe
- **Modal détaillé** — Affiche poster, note, année, durée, genres et description
- **Design sombre premium** — Typographie Playfair Display + DM Sans, animations fluides

---

## 🚀 Installation

Aucune dépendance, aucun build. C'est un fichier HTML unique.

```bash
# Option 1 — Ouvrir directement
double-clic sur 93cine.html

# Option 2 — Héberger sur GitHub Pages
1. Créer un repo GitHub
2. Upload 93cine.html → renommer en index.html
3. Settings → Pages → Source: main
4. Dispo sur : https://tonpseudo.github.io/93cine

# Option 3 — Cloudflare Pages (recommandé pour le trafic)
1. cloudflare.com → Pages → Connect to Git
2. Brancher ton repo GitHub
3. URL gratuite + CDN mondial
```

---

## 🗂️ Structure du code

```
93cine.html
├── <style>        → Tout le CSS (variables, nav, hero, cards, modal, responsive)
├── <body>
│   ├── <nav>      → Barre de navigation fixe avec recherche
│   ├── <section>  → Hero plein écran
│   ├── .cats-wrapper  → Boutons de catégories
│   ├── .genre-tabs-bar → Onglets Films / Séries (visible sur un genre)
│   └── <main>     → Sections de films générées dynamiquement
└── <script>
    ├── tmdb()           → Requêtes API TMDB
    ├── loadHero()       → Charge le film tendance du jour
    ├── loadSections()   → Charge toutes les sections home
    ├── filterCat()      → Filtre par catégorie + affiche les onglets
    ├── switchGenreTab() → Bascule Films ↔ Séries
    ├── loadGenreContent() → Charge films ou séries d'un genre
    ├── openModal()      → Ouvre la fiche détaillée
    ├── watchMovie()     → Lance le lecteur
    └── handleSearch()   → Recherche TMDB en temps réel
```

---

## 🔧 Configuration

### Changer la clé API TMDB
```javascript
const KEY = 'ta_clé_ici'; // ligne 1 du <script>
```
Créer une clé gratuite sur [themoviedb.org](https://www.themoviedb.org/settings/api)

### Ajouter / retirer des sections sur l'accueil
```javascript
const SECTIONS = [
  { title: '🔥 Tendances', url: 'trending/movie/week' },
  // Ajouter une ligne ici
];
```

### Ajouter un serveur vidéo
```javascript
function getServers(id, type='movie') {
  return [
    `https://ton-serveur.com/embed/${id}`,
    // ...
  ];
}
```
Et ajouter le bouton correspondant dans le HTML `.server-tabs`.

---

## 📡 API utilisée

[TMDB (The Movie Database)](https://www.themoviedb.org/) — gratuite, 1000 requêtes/jour.  
Endpoints utilisés :
- `trending/movie/day` — Hero
- `movie/top_rated`, `movie/popular`, `movie/now_playing` — Sections home
- `discover/movie` et `discover/tv` — Filtrage par genre
- `search/movie` — Recherche
- `movie/{id}` et `tv/{id}` — Détails modal

---

## 📱 Responsive

| Écran | Comportement |
|-------|-------------|
| Desktop | Nav complète, hero 100vh, grille auto |
| Mobile (< 768px) | Nav links cachées, titre hero réduit, modal en colonne |

---

## ⚠️ Avertissement légal

Les contenus streamés via les serveurs embarqués (VidSrc, 2Embed, etc.) ne sont pas hébergés par ce site. L'utilisation de ces services peut être illégale selon votre pays. Ce projet est à but éducatif uniquement.

---

*Fait avec ❤️ par le 93*
