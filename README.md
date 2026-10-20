# TAFHIM.PX

Pixel-crafted animated personal site. Plain HTML, CSS and JavaScript, no build step, no backend.

- `index.html`: the whole site (preloader, hero, ticker, about, animated code editor, vinyl music scene, socials, contact).
- `vercel.json`: security headers. `favicon.svg`, `robots.txt`, `sitemap.xml`: basics.

## Deploy
1. Delete the old Next.js files (`app/`, `package.json`, `next.config.mjs`, `tailwind.config.ts`, `postcss.config.mjs`) and the old `api/` folder.
2. Add these files, push to GitHub; Vercel redeploys.
3. Domain: Vercel > Settings > Domains.

Edit the code animation text in the `CODE` array inside `index.html`.
