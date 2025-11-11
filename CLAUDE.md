# CLAUDE.md

Ce fichier fournit des instructions à Claude Code (claude.ai/code) lors du travail sur le code de ce dépôt.

## Présentation du Projet

Il s'agit d'un site web statique pour le restaurant "Le Bistrot du Centre" à Montereau-Fault-Yonne. Le site est construit avec du HTML, CSS et JavaScript vanilla - aucun outil de build ou framework requis.

## Structure des Fichiers

- `index_3.html` - Fichier HTML principal avec la structure complète du site
- `styles_3.css` - Tous les styles incluant les breakpoints responsive
- `script_3.js` - JavaScript côté client pour l'interactivité
- `img/` - Photos et images du restaurant

## Commandes de Développement

Il s'agit d'un site statique sans processus de build. Pour développer :

```bash
# Servir localement (choisir n'importe quelle méthode)
python3 -m http.server 8000
# OU
python -m SimpleHTTPServer 8000
# OU utiliser n'importe quel serveur de fichiers statiques
```

Puis ouvrir `http://localhost:8000/index_3.html` dans un navigateur.

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

4. **Formulaire de Contact** - Validation côté client uniquement (lignes 52-81)
   - Affiche actuellement une alerte lors de la soumission - non connecté au backend
   - Validation email par regex

### Architecture CSS (styles_3.css)

- **Variables CSS** (lignes 9-19) - Schéma de couleurs et tokens de thème dans `:root`
- **Patterns de Layout** :
  - `.container` - Conteneur de contenu avec largeur max 1200px
  - `.container-wide` - 1400px de largeur max pour les sections plus larges
  - CSS Grid utilisé pour les layouts responsive (cartes intro, catégories menu, galerie, formules)

- **Breakpoints Responsive** :
  - 1024px : Tablette - convertit les grilles multi-colonnes en colonne unique
  - 768px : Mobile - cache la nav desktop, affiche le bouton menu mobile
  - 500px : Petit mobile - réduit les padding et tailles de police

### Structure HTML (index_3.html)

Site mono-page avec ces sections (dans l'ordre) :
1. Header - Navigation sticky (ligne 14)
2. Hero - Image pleine largeur avec boîte de texte en superposition (ligne 44)
3. Intro - Trois cartes de fonctionnalités (ligne 58)
4. About - Grille image + texte (ligne 86)
5. Menu - Catégories de menu sur trois colonnes + cartes de formules (ligne 116)
6. Gallery - 8 photos du restaurant dans une grille responsive (ligne 250)
7. CTA - Section d'appel à l'action (ligne 295)
8. Contact - Cartes d'infos + formulaire de contact (ligne 306)
9. Footer - Liens et copyright (ligne 378)

Toutes les sections utilisent des IDs d'ancrage pour la navigation en défilement fluide.

## Gestion des Images

Les images de la galerie sont référencées depuis le répertoire `img/`. Images actuelles :
- `devanture.jpg` - Image de la devanture/hero
- `bar.jpg` - Zone du bar
- `IMG-20251009-WA00XX.jpg` - Diverses photos d'intérieur et de plats

Lors de l'ajout d'images, maintenir un ratio d'aspect 1:1 pour les cartes de galerie (appliqué via `aspect-ratio: 1` dans le CSS).

## Conventions de Style

- Couleur primaire : `#e67e22` (orange) - Utilisée pour les CTA, accents, liens
- Couleur secondaire : `#2c3e50` (bleu-gris foncé) - En-têtes et footer
- Polices :
  - Titres : 'Merriweather' serif (depuis Google Fonts)
  - Corps : 'Open Sans' sans-serif (depuis Google Fonts)

Classes spéciales pour les items du menu :
- `.menu-item.special` - "Plat du Jour" mis en évidence avec teinte orange
- `.menu-item.vegetarian` - Teinte verte pour les options végétariennes

## Formulaire de Contact

Le formulaire aux lignes 352-372 dans index_3.html actuellement :
- Effectue une validation côté client
- Affiche une alerte navigateur lors de la soumission
- N'envoie PAS de données à un serveur

Pour implémenter l'envoi backend, modifier le gestionnaire de formulaire dans script_3.js (lignes 55-80) pour envoyer les données via fetch/XMLHttpRequest vers votre endpoint backend.

## Notes sur le Statut Git

La structure du répertoire parent suggère plusieurs versions. Ceci est la V1. Les fichiers comme `index_3.html`, `script_3.js`, `styles_3.css` sont les fichiers actifs (la numérotation "3" semble indiquer une itération).
