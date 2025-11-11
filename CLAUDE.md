# CLAUDE.md

Ce fichier fournit des instructions à Claude Code (claude.ai/code) lors du travail sur le code de ce dépôt.

## Présentation du Projet

Il s'agit d'un site web statique pour le restaurant "L'imaginarium" à Montereau-Fault-Yonne. Le site est construit avec du HTML, CSS et JavaScript vanilla - aucun outil de build ou framework requis.

## Structure des Fichiers

- `index.html` - Fichier HTML principal avec la structure complète du site
- `styles_3.css` - Tous les styles incluant les breakpoints responsive
- `script_3.js` - JavaScript côté client pour l'interactivité
- `img/` - Photos et images du restaurant
- `Menu d'automne LAST.pdf` - Menu officiel du restaurant (source de référence)

## Informations du Restaurant

- **Nom** : L'imaginarium
- **Adresse** : 6 rue couverte, 77130 Montereau-Fault-Yonne, France
- **Téléphone** : 01 60 71 00 09
- **Horaires** :
  - Mardi - Samedi : 12h-14h / 19h-22h
  - Dimanche : 12h-15h
  - Lundi : Fermé

## Commandes de Développement

Il s'agit d'un site statique sans processus de build. Pour développer :

```bash
# Servir localement (choisir n'importe quelle méthode)
python3 -m http.server 8000
# OU
python -m SimpleHTTPServer 8000
# OU utiliser n'importe quel serveur de fichiers statiques
```

Puis ouvrir `http://localhost:8000/index.html` dans un navigateur.

## Architecture & Fonctionnalités Clés

### Fonctionnalités JavaScript (script_3.js)

Le site possède trois fonctionnalités interactives principales :

1. **Système de Menu Mobile** - Menu coulissant activé par le bouton hamburger (lignes 1-31)
   - Basculer avec `.mobile-menu-btn`
   - Fermer via le bouton `.close-menu`, les liens de navigation, ou en cliquant à l'extérieur

2. **Défilement Fluide** - Tous les liens d'ancrage défilent en douceur avec un décalage de 80px pour l'en-tête (lignes 33-49)

3. **Animations au Défilement** - Effet de fondu entrant utilisant IntersectionObserver (lignes 84-112)
   - Cible les éléments `.gallery-card` et `.intro-card`
   - Délais échelonnés pour un effet en cascade

4. **Contact** - Pas de formulaire, uniquement CTA d'appel téléphonique direct (ligne 51)

### Architecture CSS (styles_3.css)

- **Variables CSS** (lignes 9-19) - Schéma de couleurs et tokens de thème dans `:root`
  - Couleur primaire : `#e67e22` (orange)
  - Couleur secondaire : `#2c3e50` (bleu-gris foncé)

- **Patterns de Layout** :
  - `.container` - Conteneur de contenu avec largeur max 1200px
  - `.container-wide` - 1400px de largeur max pour les sections plus larges
  - CSS Grid utilisé pour les layouts responsive

- **Breakpoints Responsive** :
  - 1024px : Tablette - grilles multi-colonnes → colonnes simples
  - 900px : Menu catégories et boissons → colonne unique
  - 768px : Mobile - navigation desktop → menu hamburger
  - 600px : Carte boissons → colonne unique
  - 500px : Petit mobile - padding et tailles de police réduites

### Structure HTML (index.html)

Site mono-page avec ces sections (dans l'ordre) :

1. **Header** - Navigation sticky avec logo "L'imaginarium"
2. **Hero** - Image pleine largeur avec boîte de bienvenue (transparence 95%)
3. **Intro** - Trois cartes de fonctionnalités (Cuisine Maison, Ambiance, Vins)
4. **About** - Grille image + texte de présentation
5. **Menu** - Carte du restaurant :
   - 3 catégories principales : Entrées, Plats, Desserts (grille 3 colonnes)
   - Formules : Menu du Jour (13€), Menu Complet (16€), Menu Enfant (8€)
   - **Planches** : Charcuterie (16€), Fromages (12€), Mixte (18€)
   - **Spécialités** : Couscous, Fritures, Brunch du Dimanche
   - **Carte des Boissons** : Format compact 2 colonnes, 6 catégories regroupées
6. **Gallery** - 8 photos du restaurant dans une grille responsive (4 colonnes)
7. **CTA** - Section d'appel à l'action "Envie de nous rendre visite"
8. **Contact** - 2 colonnes :
   - Colonne gauche : Google Maps + CTA d'appel téléphonique
   - Colonne droite : Cartes d'infos (Adresse, Téléphone, Horaires)
9. **Footer** - Liens et copyright "manyO.dev"

Toutes les sections utilisent des IDs d'ancrage pour la navigation en défilement fluide.

## Structure du Menu

### Entrées (4,50€ - 7,50€)
- Mille-feuilles, Carottes râpées : 4,50€
- Salades composées : 7,50€
- Velouté au Comté : 6,50€

### Plats (6,50€ - 14€)
- Épinards végétariens : 6,50€
- Escalopes de dinde : 12€
- Bavette : 12€ / Entrecôte : 14€
- Accompagnements : frites maison / haricots verts à l'ail

### Desserts (3,50€ - 6€)
- Glaces (2 boules) : 3,50€ (supplément chantilly 1,50€)
- Assiette de fromages : 6€
- Fruits de saison : 5€
- Dessert du jour : 4,50€

### Spécialités
- **Planches** : Charcuterie/Fromages/Mixte
- **Fritures** : Toutes à 4,50€ (samoussas, accras, beignets, etc.)
- **Couscous** : Sur réservation 24h, 6 pers min (7 légumes 13€, Royal 22€)
- **Brunch dimanche** : 20€, formules salée/sucrée

### Carte des Boissons (Format compact)
- Eaux, Softs (avec sirops), Boissons chaudes
- Bières : Leffe, gamme Briard (Blanche, Blonde, Ambré, IPA)
- Apéritifs & Spiritueux regroupés
- Vins & Champagne : avec détails millésimes (Chinon, Saint-Amour, Chardonnay, Coteaux, Champagne Georges Clément)

## Gestion des Images

Images référencées depuis le répertoire `img/` :
- `devanture.jpg` - Image hero de la devanture
- `bar.jpg` - Zone du bar pour section About
- `IMG-20251009-WA00XX.jpg` - Photos d'intérieur et ambiance (8 images pour la galerie)

Pour la galerie : maintenir un ratio d'aspect 1:1 (appliqué via `aspect-ratio: 1` dans le CSS).

## Conventions de Style

### Couleurs
- Primaire : `#e67e22` (orange) - CTA, accents, liens, prix
- Primaire foncé : `#d35400` - Hover states
- Secondaire : `#2c3e50` (bleu-gris) - En-têtes, footer
- Texte : `#2c3e50` (foncé), `#7f8c8d` (clair)
- Fond : `#f8f9fa` (sections alternées)

### Polices
- Titres : 'Merriweather' serif (Google Fonts)
- Corps : 'Open Sans' sans-serif (Google Fonts)

### Classes spéciales
- `.menu-item.special` - Items mis en évidence avec teinte orange
- `.menu-item.vegetarian` - Items végétariens avec teinte verte
- `.formula-card.highlight` - Formule populaire avec fond dégradé orange
- `.drinks-grid-compact` - Grille 2 colonnes pour carte boissons compacte

## Contact & Intégration Google Maps

Section contact sans formulaire :
- **Google Maps** : Intégré avec adresse "6 rue couverte, 77130 Montereau-Fault-Yonne"
- **CTA d'appel** : Bouton avec dégradé orange pour appel direct vers 01 60 71 00 09
- Layout : Map + CTA à gauche, Cartes d'infos à droite

Pour mettre à jour la carte Google Maps :
1. Aller sur Google Maps
2. Chercher l'adresse
3. Cliquer "Partager" → "Intégrer une carte"
4. Remplacer l'iframe dans la section `.map-wrapper`

## Notes sur le Déploiement

- Site destiné à être hébergé sur GitHub Pages : `https://nicowithmanyo.github.io/imaginarium/`
- Domaine personnalisé prévu : `imaginarium77.com` (actuellement sur Wix, à transférer)
- Pas de backend requis - site 100% statique
- Copyright footer : "manyO.dev"

## Fichiers de Menu

Le menu est basé sur **"Menu d'automne LAST.pdf"** - fichier de référence officiel.
En cas de mise à jour du menu, toujours se référer au PDF fourni par le restaurant.
