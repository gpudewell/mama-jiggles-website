# Mama Jiggles Website — Working With Claude

This project is the marketing landing page for **Mama Jiggles** (hand-crafted Jell-O shots). The QR code on her business cards points here.

Two kinds of people use Claude on this repo:
- **Greg** — technical owner, can change anything.
- **Mama Jiggles herself (non-technical content editor on her phone)** — should only change text, flavors, and contact info, and always via a Pull Request.

The rules below default to the content-editor workflow. If you're working with Greg, the safety rails are advisory — but the file map and stack notes still apply.

---

## Hard rules for content edits

1. **Never push to `main` directly.** Always create a new branch and open a Pull Request. Greg reviews and merges.
2. **Branch naming:** `content/<short-description>` — e.g. `content/add-watermelon-flavor`, `content/update-tagline`.
3. **One change per PR** when possible — easier to review on a phone.
4. **Don't change visual design, deploy config, or component logic** unless explicitly asked. The "Locked files" list below is the source of truth.
5. **Always include a one-line PR description** explaining what was changed in plain English.

---

## Stack & deploy

- **Framework:** [Astro](https://astro.build) v6 (static-site generator)
- **Styling:** Tailwind v4 with brand tokens in `src/styles/global.css`
- **Hosting:** Cloudflare Workers Static Assets (deployed via `wrangler deploy`)
- **Custom domain:** mamajiggles.com (or workers.dev URL until registered)
- **Auto-deploy:** Every push to `main` triggers a Cloudflare build in ~30 seconds.

That means: **the moment Greg merges a PR, the change is live on mamajiggles.com.**

---

## Where common content lives

All editable content is in **`src/pages/index.astro`**. Use this map to find what to change:

| What you want to change | Where it is in `src/pages/index.astro` |
| :----------------------- | :-------------------------------------- |
| The **order email address** | Top of file, `const orderEmail = "..."` |
| The **pre-filled order template** sent in the email | Top of file, `const orderBody = "..."` |
| The **flavor list** (names + notes) | Top of file, the `flavors = [...]` array |
| The **hero tagline** ("Hand-crafted Jell-O shots...") | Inside `<p class="hero__tagline">` |
| The **"Who's Mama?" about copy** | Inside the `section--cream-dark` block |
| The **"How to Order" 3 steps** | Inside the `section--cream` block, in the `<ol class="steps">` |
| The **footer legal text** | Inside `<p class="footer__legal">` |
| The **age-gate copy** ("Hold up, sugar.") | `src/components/AgeGate.astro` |
| The **page title and OG description** (shows in search results and social shares) | `src/layouts/Layout.astro`, the `title` and `description` defaults |

---

## Locked files — do NOT edit on content PRs

These control how the site looks and deploys. Changes here belong in a separate, technical PR from Greg:

- `src/styles/global.css` — brand colors, fonts, button styles
- `src/layouts/Layout.astro` — HTML scaffolding, meta tags (UNLESS the request is specifically about meta tags / SEO)
- `astro.config.mjs`, `wrangler.jsonc`, `package.json`, `tsconfig.json` — build and deploy config
- `public/logo.png`, `public/og-image.png`, `public/favicon.svg`, `public/apple-touch-icon.png` — brand assets

If you think one of these *needs* to change, **stop and ask the user to confirm with Greg** before editing.

---

## Workflow for a content edit (the happy path)

When Mama (or anyone) asks for a content change:

1. **Confirm in plain English** what you'll change before editing. Example: "Got it — I'll add a new flavor called 'Watermelon Wonder' (tequila, watermelon) to the menu and open a PR for Greg to review. Sound good?"
2. **Create a new branch** named `content/<short-description>`.
3. **Make the change** to the relevant file(s) per the map above.
4. **Commit** with a clear message describing the change. No need for technical jargon — write like you're texting a friend.
5. **Open a PR** to `main` with a title and 1–2 line description of what changed and why.
6. **Tell the user** the PR is open and Greg will get a notification — once he merges, the live site updates in ~30 seconds.

---

## Tone & content guidelines

The brand voice is **vintage, playful, slightly cheeky** — think 1940s pin-up Americana. Words like "sugar," "kick," "wobble," "Mama" are on-brand. Avoid corporate-speak. Keep it short and punchy. When in doubt, match the tone of the existing copy on the page.

The site is alcohol-adjacent (Jell-O shots), so it must remain 21+ — never remove or weaken the age-gate disclaimer in the footer or the AgeGate component.

---

## Quick reference — what's already there

- **Domain (target):** mamajiggles.com
- **Live URL (current):** https://mama-jiggles-website.gpudewell.workers.dev (until custom domain wired up)
- **Order email:** mamajigglesgelatin@gmail.com
- **Current flavors:** Classic Cherry Bomb, Lime in the Coconut, Peach Please, Blue Bombshell, Strawberry Sweetheart, Ask Mama (placeholder — likely to be replaced with the real menu)
