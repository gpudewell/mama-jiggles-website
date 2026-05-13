# Mama Jiggles Website

The marketing site for **Mama Jiggles** — hand-crafted Jell-O shots. This is the page the QR code on the business card points to.

- **Live:** https://mamajiggles.com
- **Stack:** [Astro](https://astro.build) + Tailwind v4, deployed to Cloudflare Pages
- **Contact:** mamajigglesgelatin@gmail.com

## Local dev

```sh
npm install
npm run dev
```

Then open http://localhost:4321.

| Command           | What it does                              |
| :---------------- | :---------------------------------------- |
| `npm run dev`     | Local dev server at `localhost:4321`      |
| `npm run build`   | Build the static site into `./dist/`      |
| `npm run preview` | Preview the production build locally      |

## Required assets

Drop these files into `public/` before deploying:

| File                  | What it is                              | Used where                          |
| :-------------------- | :-------------------------------------- | :---------------------------------- |
| `logo.png`            | Main Mama Jiggles logo (square, ~1200px) | Hero section                        |
| `og-image.png`        | Social share image (1200×630)            | Open Graph / Twitter cards          |
| `apple-touch-icon.png`| iOS home-screen icon (180×180)           | "Add to Home Screen" on iPhone      |

The favicon (`public/favicon.svg`) is already in place — a stylized red Jell-O cup on the navy/cream brand.

## Editing content

Most copy lives in `src/pages/index.astro`. The flavor list, headline, tagline, and steps are all in that one file. To change the contact email or order template, update the constants at the top of that file.

Brand tokens (colors, fonts) live in `src/styles/global.css` under `@theme`.

## Deploying to Cloudflare Pages

1. Push this repo to GitHub.
2. In the Cloudflare dashboard → **Workers & Pages → Create → Pages → Connect to Git**.
3. Pick the repo. Use these build settings:
   - **Framework preset:** Astro
   - **Build command:** `npm run build`
   - **Build output directory:** `dist`
   - **Node version:** `22` (set as env var `NODE_VERSION=22`)
4. Add the custom domain `mamajiggles.com` under **Custom domains**. Cloudflare will issue an SSL cert automatically.

That's it. Future pushes to `main` redeploy automatically.

## Structure

```
src/
├── components/
│   └── AgeGate.astro       21+ modal shown on first visit
├── layouts/
│   └── Layout.astro        HTML shell with meta tags, fonts, OG cards
├── pages/
│   └── index.astro         The single landing page
└── styles/
    └── global.css          Brand tokens, base styles, reusable components
public/
└── favicon.svg             Brand favicon
```
