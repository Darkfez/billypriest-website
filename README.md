# billypriest.com

Source of truth for the live billypriest.com website.

Static site, no build step. Vanilla JS single-page app (`app.js`) that client-side
routes between pages (`/about`, `/research`, `/blog/:slug`, etc.) and renders into
`<div id="app">` in `index.html`. Styling is `colors_and_type.css` (design tokens)
+ `site.css` (layout/components).

## Repository structure

- `index.html` — shell page
- `app.js` — routing, bilingual UI/content, blog posts, prompt library, and page rendering
- `colors_and_type.css` — design tokens and typography
- `site.css` — layout and component styles
- `netlify.toml` — Netlify publish/SPA redirect configuration
- `solar-system.html` — standalone interactive Solar System page linked from AI Projects
- `uploads/` — site images and embedded PDFs

The portrait images, LINE QR code, blog images, and Autumn Intensive Writing Course PDF are all stored in `uploads/`.

## Deploying to Netlify

The repo is ready to be connected directly to the existing Netlify project.
`netlify.toml` publishes the repository root and serves `index.html` for every SPA
route so paths such as `/about` and `/blog/:slug` work correctly.

Once Netlify continuous deployment is connected to the `main` branch, GitHub
should be treated as the canonical source: make and commit changes here, then let
Netlify build/deploy the commit automatically.

## Blog posts

Blog posts live in the `blogPosts` array near the top of `app.js`. Each post
needs a unique `slug`, a `title`/`excerpt` (bilingual, `{ en, ja }`), and a
`date` (`YYYY-MM-DD` — the newest date becomes the post featured on the home
page, and all posts are listed at `/fun/archive`).

A post's body is either:
- `contentMd: { en, ja }` — Markdown-ish text rendered into the page, or
- `pdf: 'uploads/your-file.pdf'` — renders the post as an embedded PDF viewer
  with nothing else on the page (see the `autumn-intensive-writing-course`
  post for an example).

Only set one of the two.

## Bilingual content

New site content should normally have both English and Japanese variants. Academic
reference lists, citations, and material intended to remain verbatim in English
should not be translated.
