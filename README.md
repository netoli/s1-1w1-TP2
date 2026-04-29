# Motiv-True — TP2 Mise en page Web

> Site statique HTML / CSS — premier travail pratique du programme **TIM** (Technique d'intégration multimédia, Collège de Maisonneuve, automne 2023).

**Démo live :** https://netoli.github.io/s1-1w1-TP2/

---

## Le projet

Site fictif sur le thème de la motivation au travail (« Motiv-True »), structuré autour de cinq sections : Accueil, Inscription, Horaire (table semaine), Articles, Galerie médias. Premier exercice du cursus, ce TP servait à pratiquer la mise en page HTML5 / CSS3 sans framework, sans JavaScript.

## Refonte portfolio (avril 2026)

La version livrée en classe a été remise à niveau pour devenir une pièce de portfolio :

### Sémantique & accessibilité
- `<html lang="fr">` (était `en`), `<title>` contextualisé.
- Wrappers `<div id="...">` éliminés au profit de balises HTML5 (`<header>`, `<main>`, `<footer>`, `<section>`, `<article>`, `<figure>`).
- Skip link « Aller au contenu », `<main id="main">`, `aria-labelledby` sur chaque section.
- Tous les `<input>` du formulaire d'inscription : labels `for`/`id` corrigés (les radios `prog__1/2/3` étaient cassées), `name` ajoutés, `autocomplete` sur nom/prénom/email/mot-de-passe.
- `<th scope="col">` / `scope="row"` sur la table d'horaire.
- Burger menu : `aria-label`, `role="button"`, `tabindex="0"`, `alt=""` sur SVG décoratifs.
- Lorem ipsum éliminé, contenu réel à la place (3 cartes de valeur dans le footer).
- Liens sociaux désormais cliquables (`<a aria-label>`) au lieu de `<figure>` mortes.
- Hiérarchie de titres rétablie (plus de `<h5>` orphelin).
- `prefers-reduced-motion` supporté.

### SEO
- `<meta name="description">`, Open Graph (type, title, description, url), Twitter card, `<link rel="canonical">`, `<meta name="theme-color">`, `<meta name="author">`.

### Performance
- 3 requêtes Google Fonts → 1 seule combinée (`Nova+Square&family=Pacifico&family=Permanent+Marker`).
- `<link rel="preconnect">` vers `fonts.googleapis.com` + `fonts.gstatic.com`.
- Ordre CSS corrigé : `normalize.css` désormais **en premier** (était dernier — il écrasait tous les styles).
- `loading="lazy"` + dimensions explicites (width/height, `aspect-ratio`) sur les images sous le pli.
- `preload="metadata"` sur les vidéos (au lieu du chargement complet).

### Refonte visuelle (`style.css` v2)
- **Design system** complet via custom properties : palette **indigo `#1e1b4b` + ambre `#f59e0b`**, échelle d'espacement modulaire, ombres calibrées, transitions discrètes.
- **Typographie** : `Permanent Marker` pour le wordmark, `Nova Square` pour les titres de section (avec underline ambre), `system-ui` pour le corps de texte.
- **Header sticky** avec backdrop blur, soulignement animé sur les liens de nav, recherche intégrée.
- **Cards** modernes (border + ombre douce + hover lift) sur toutes les sections.
- **Galerie** : effet zoom au hover, overlay dégradé sur les `<figcaption>`, badge catégorie ambre.
- **Table horaire** : cours codés couleur (cinq teintes pastel par cours), responsive mobile en cartes.
- **Burger menu CSS-only** (checkbox hack, sans JS) avec animation de hauteur.
- **Footer dark** avec 3 cards de valeur, formulaire de contact, navigation organisée, médias sociaux interactifs.

### Responsive (mobile-first)
- 4 breakpoints : `< 640px` (mobile), `< 900px` (tablette + burger), `≥ 768px` (layout 2 colonnes), `≥ 1024px` (desktop).
- Table horaire transformée en cartes empilées sous 640 px.
- Formulaire d'inscription en grille 2 colonnes sur tablette+.
- Galerie auto-fit (`minmax(250px, 1fr)`).

---

## Stack

- **HTML5** sémantique (validateur W3C)
- **CSS3** : custom properties, Grid, Flexbox, `clamp()`, `aspect-ratio`, container queries-ready
- **Aucun JavaScript** — tout en CSS-only

## Structure

```
s1-1w1-TP2/
├── index.htm
├── README.md
├── css/
│   ├── normalize.css       # reset standard (chargé en 1er)
│   ├── style.css           # design system v2 — tout consolidé ici
│   ├── navigation.css      # vidé (legacy)
│   ├── accueil.css         # vidé (legacy)
│   ├── horaire.css         # vidé (legacy)
│   ├── articles.css        # vidé (legacy)
│   ├── galerie.css         # vidé (legacy)
│   └── inscription.css     # vidé (legacy)
├── Images/
│   ├── Logo/
│   ├── Galerie/
│   ├── Réseaux sociaux/
│   ├── stat.png
│   └── etoile.png
└── Vidéos/
    ├── 5.mp4
    └── 6.mp4
```

## Apprentissages

- **Sémantique avant style** : la version originale empilait `<div id="..."><header>...</header></div>` — j'ai redécouvert en refondant que les balises HTML5 *sont* le système de mise en page, pas une couche au-dessus.
- **Accessibilité par accident vs. par design** : les `<label for="...">` du TP étaient *visuellement* corrects mais *fonctionnellement* cassés (5/6 radios sans cible valide). Tester réellement avec un lecteur d'écran change la perspective.
- **Custom properties = design system** : centraliser la palette/échelle dans `:root` rend toute itération de marque triviale.
- **CSS-only burger menu** : le checkbox hack reste élégant pour un site sans JS — limites a11y connues, contournées via `aria-label` + `tabindex` sur le `<label>`.

## Auteur

**Olivier Vernet** — étudiant TIM, Collège de Maisonneuve · [GitHub @netoli](https://github.com/netoli)
