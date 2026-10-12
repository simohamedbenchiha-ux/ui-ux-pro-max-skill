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

## Autres sections dark luxe (même installation)

Dépose chaque fichier dans `sections/`, puis ajoute-le depuis *Personnaliser*.
Toutes partagent la palette dark luxe (réglable par section).

| Fichier | Rôle |
|---|---|
| `collection-luxe.liquid` | Grille produits depuis une **vraie collection** (choisie dans les réglages) : image, titre, prix, promo, bouton panier, « voir tout ». |
| `story-luxe.liquid` | Histoire + blocs **engagements** répétables (icône/titre/texte). |
| `testimonials-luxe.liquid` | **Avis** en blocs répétables (note ★, citation, nom, photo). |
| `newsletter-luxe.liquid` | Inscription branchée sur le **formulaire client Shopify** (`{% form 'customer' %}`). |

### Collections de ton store (à sélectionner dans `collection-luxe`)

| Collection | Handle |
|---|---|
| Atelier Rosa | `belleza` |
| Pura Luce | `cura-del-viso` |
| Elisir Dorato | `styling-capelli` |
| Essenza di Seta | `cura-dei-capelli` |
| Perfezione Nude | `benessere` |
| BELLEZA | `test` |

### Ordre conseillé de la page d'accueil
1. Hero cinématique
2. Collection dark luxe (ex. *Perfezione Nude* ou *Elisir Dorato*)
3. Histoire dark luxe
4. Avis dark luxe
5. Newsletter dark luxe

> Astuce : pour animer les sections au scroll, GSAP + ScrollTrigger doivent
> être chargés (le hero charge déjà GSAP ; ajoute ScrollTrigger dans
> `theme.liquid` si tu utilises les sections sans le hero) :
> ```html
> <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.5/ScrollTrigger.min.js" defer></script>
> ```
> Sans GSAP, les sections s'affichent simplement sans animation (contenu visible).

## Aperçu HTML

Rendus statiques autonomes (ouvre dans un navigateur) :
- `giulia-beauty-design/hero-cinematic.html` — le hero seul
- `giulia-beauty-design/home-dark-luxe.html` — la homepage complète
