# Listing_Page

YachtWay listing page template. Module order, fact block and contact placement set from Amplitude data (project 748126, 9 Jun to 7 Sep 2026), four converting session replays and graded buyer research. Spec: Notion, Listing pages row, child page Listing Page · Information Hierarchy.

Two stages, same markup:

- `/` clean page, positions hidden. Add `?notes=1` to show them.
- `/notes/` positions shown, every module numbered with its rule and evidence.

`notes/index.html` is generated from `index.html` by switching the body class; edit `index.html` and re-copy.

## Design system

Styling follows [`@yachtway/ui`](https://github.com/yachtway/yachtway-ui) 0.1.4 at commit `fb4240d`. The prototype is a static file, so the React components cannot be used; their CSS is mirrored instead:

- Tokens: the `n-*` base palette, the `s-*` semantic text, fg, bg and border sets, the shadcn roles (`--background`, `--card`, `--muted`, `--border`) and the `.shadcn-root` radius scale (`--radius` 0.9rem), copied from `styles/colors.css`, `roles.css`, `base.css`. Light palette only, as the package ships.
- Type: Poppins for headlines, Figtree for text, per `styles/typography.css`. Body 16/24.
- Buttons: `primary` is the brand radial face with `--shadow-btn-brand`; `secondary` is the white gradient face with `--shadow-btn-white`. Small size, 40 px, `squareRadius(40)` = 13 px, pill for icon buttons. From `src/components/ui/button.tsx` and `styles/controls.css`.
- Badge: 20 px pill, 12 px medium, from `badge.tsx`. Status labels use the semantic success and warning tokens.
- Tabs and the unit toggle: muted list with a raised active trigger, from `tabs.tsx`.
- Inputs: 40 px, 13 px radius, `--border-s-input-default`, hover `--border-s-input-hover`, from the form-controls skill.

When the page is built for real, replace these mirrors with the package components inside `ShadcnRoot`.
