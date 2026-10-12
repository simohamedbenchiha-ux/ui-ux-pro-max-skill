# Giulia Beauty — Hero cinématique (section Shopify)

Section de bannière immersive « dark luxe ambré », entièrement éditable depuis
l'éditeur de thème. Fond **vidéo** si tu en fournis une, sinon **scène animée**
(pétales + gouttes d'or) en repli automatique.

## Installation (3 minutes)

1. Admin Shopify → **Boutique en ligne → Thèmes → … → Modifier le code**.
2. Dossier **`sections/`** → *Ajouter un fichier* → nomme-le `hero-cinematic` →
   colle le contenu de `sections/hero-cinematic.liquid`. Enregistre.
3. Ajoute les **polices** : ouvre `layout/theme.liquid` et colle ceci juste avant
   `</head>` :
   ```html
   <link rel="preconnect" href="https://fonts.googleapis.com">
   <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
   <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,400;0,500;0,600;1,400&family=Jost:wght@300;400;500;600&display=swap" rel="stylesheet">
   ```
4. Retourne sur **Personnaliser** → *Ajouter une section* → **Hero cinématique**.
   Place-la en haut de la page d'accueil.

## Réglages disponibles (éditeur de thème)

- **Contenu** : sur-titre, titre (avec `<em>…</em>` pour la couleur or, `<br>`
  pour les retours), texte.
- **Boutons** : 2 boutons (texte + lien).
- **Étiquette produit** (bas droite) : mention, nom, prix.
- **Fond — Vidéo** :
  - `Vidéo (hébergée Shopify)` : importe ton `.mp4` dans *Contenus → Fichiers*
    puis sélectionne-le, **ou**
  - `URL d'une vidéo .mp4` : colle une URL directe, **ou**
  - laisse vide → la **scène animée** s'affiche.
  - `Image poster` : affichée pendant le chargement de la vidéo.
- **Animation** : parallaxe souris (on/off), hauteur (60–100 vh).
- **Couleurs** : fond, ambre, or, texte clair, texte secondaire, bouton sombre.

## Notes techniques

- GSAP est chargé depuis le CDN par la section (une seule fois). Pour un contrôle
  total des performances, tu peux l'héberger dans `assets/` et remplacer la balise
  `<script src=...>` par `{{ 'gsap.min.js' | asset_url | script_tag }}`.
- Respecte `prefers-reduced-motion` : animations coupées pour les personnes
  sensibles au mouvement.
- Compatible éditeur de thème : la scène se réinitialise sur
  `shopify:section:load`.
- Pour la perf, une **vidéo** de fond doit être courte (6–12 s), en boucle,
  compressée (H.264, ~1080p, < 4–5 Mo), muette.

## Aperçu HTML

Le rendu statique autonome est dans
`giulia-beauty-design/hero-cinematic.html` (ouvre-le dans un navigateur).
