# SnackSaaS Pro — site vitrine : règles de développement

Site statique Vite + HTML + CSS + JS vanilla, déployé sur Firebase Hosting (projet `snack-saas-pro`, site `snack-saas-pro`).

## Style & thèmes
- Jamais de couleur en dur ni de `style=""` dans `index.html` / `src/main.js` : classes CSS + jetons `var(--…)` définis dans `src/styles.css` (`:root` pour l'indépendant du thème, `[data-theme="dark"]` et `[data-theme="light"]` pour le reste).
- Les surfaces « écran » (mockup téléphone, cadre d'aperçu) utilisent les jetons `--screen-*` et restent sombres dans les deux thèmes ; l'illustration de la mascotte utilise `--illu-*`.
- Toute animation décorative doit être neutralisée dans le bloc `@media (prefers-reduced-motion: reduce)`.
- Le `h1` du Hero est l'élément LCP : pas de révélation depuis `opacity: 0`, pas de dépendance à `main.js` pour l'afficher.

## Polices
- Auto-hébergées dans `public/fonts/` (`@font-face` en tête de `src/styles.css`). Pas de `<link>` Google Fonts.

## Déploiement
- Uniquement `npm run deploy` (build + `firebase deploy --only hosting --project snack-saas-pro`). Jamais de `firebase deploy` sans `--project`.
- Valider avant : `npm run build`, les deux thèmes à 375 / 640 / 992 / 1240 px, aucun débordement horizontal, contraste AA.
