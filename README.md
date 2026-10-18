# SnackSaaS Pro — site vitrine

Landing page commerciale de SnackSaaS Pro (Click & Collect + PWA propriétaire pour snacks et restaurants), éditée par Code Crafters.
Site statique **Vite + HTML + CSS + JS vanilla**, hébergé sur **Firebase Hosting**, projet `snack-saas-pro`.

- Production : https://snack-saas-pro.web.app
- Application démo mise en avant : https://snacking-template.web.app (dépôt [snacking_template](https://github.com/Sulayman74/snacking_template))

## Démarrer

```bash
npm install
npm run dev        # http://localhost:5174
npm run build      # dist/
npm run preview    # sert dist/ sur http://localhost:4173
```

## Déployer

```bash
npm run deploy     # build + firebase deploy --only hosting --project snack-saas-pro
```

`firebase.json` verrouille le site (`"site": "snack-saas-pro"`) et le script passe `--project` : un déploiement vers un autre projet échoue au lieu d'écraser un site. Ne jamais lancer un `firebase deploy` nu depuis un autre dossier.

## Design system « Braise & Crème »

- Deux thèmes (`data-theme="dark" | "light"`, mémorisé en `localStorage`), tous les jetons dans `src/styles.css` (`:root`, `[data-theme="dark"]`, `[data-theme="light"]`).
- Zéro couleur en dur et zéro `style=""` dans `index.html` et `src/main.js` : on passe par des classes et `var(--…)`.
- Polices auto-hébergées dans `public/fonts/` (sous-ensemble latin, licence OFL) : Plus Jakarta Sans (texte) et Bricolage Grotesque 800 (`h1` du Hero et wordmark du footer).
- Mascotte « sac kraft » en SVG inline (sans yeux), décor du Hero en `radial-gradient` + grain `feTurbulence` statique, footer à vagues, bandeau défilant et wordmark rogné. Tout est coupé sous `prefers-reduced-motion`.
- Le `h1` est l'élément LCP : sa révélation ne doit jamais partir d'`opacity: 0` (voir le commentaire dans `src/styles.css`).

## Qualité

Dernière mesure Lighthouse (build de production, Chrome headless) : mobile 99 / 100 / 100 / 100, desktop 100 / 100 / 100 / 100, CLS 0.
Vérifications manuelles attendues avant déploiement : les deux thèmes aux largeurs 375, 640, 992 et 1240 px, aucun débordement horizontal, contraste AA sur les textes.
