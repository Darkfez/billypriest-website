# billypriest.com

Static site, no build step. Vanilla JS single-page app (`app.js`) that client-side
routes between pages (`/about`, `/research`, `/blog/:slug`, etc.) and renders into
`<div id="app">` in `index.html`. Styling is `colors_and_type.css` (design tokens)
+ `site.css` (layout/components).

## Deploying to Netlify

Connect this repo to Netlify as-is — `netlify.toml` is already set up to serve
`index.html` for every path (required because routes like `/about` aren't real
files; the JS router handles them client-side).

## Missing images

`app.js` references these files under `uploads/`, which are not in this repo yet
because they weren't provided:

- `uploads/Mirrorball profil.jpeg` (home page portrait)
- `uploads/Profile.jpeg` (About page portrait)
- `uploads/LINE QR Code.jpg` (About page contact QR code)

Add them to `uploads/` (same filenames, or update the `src` attributes in
`app.js`) and they'll appear automatically. Until then those three `<img>` tags
will show as broken images.

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
