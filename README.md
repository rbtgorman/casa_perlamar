# Casa Perlamar

A holiday apartment rental website for **Casa Perlamar**, a sea-view apartment in **Calpe, Spain** (Costa Blanca). Built with [Eleventy (11ty)](https://www.11ty.dev/) and edited through [Decap CMS](https://decapcms.org/).

## What's here

- **Pages:** Home, The Apartment, Gallery, Local Area, Recommendations, Reviews, Contact/Booking, Blog.
- **Owner-editable content (via the CMS at `/admin/`):**
  - **Local Area** — a guide to Calpe (getting here, beaches, climate, transport).
  - **Recommendations** — places to eat, drink, swim and visit (one entry per place).
  - **Blog** — optional travel tips.

## Project structure

```
src/
├── _data/          site.json, apartment.json, reviews.json, buildYear.js
├── _includes/      head.njk, header.njk, footer.njk
├── _layouts/       base.njk, page.njk, post.njk
├── admin/          Decap CMS (config.yml + index.html)
├── assets/         fonts, svgs, favicons, js (dark mode + mobile nav)
├── css/            theme styles + pages.css
├── images/         apartment photos (+ uploads/ for CMS media)
├── recommendations/  one .md per recommended place
├── local-area/     index.md (the Local Area page)
├── blog/           blog posts
└── *.njk           page templates
```

Eleventy reads from `src/` and outputs the finished site to `_site/` (which is git-ignored and rebuilt on deploy).

## Develop locally

```bash
npm install
npm start          # serves at http://localhost:8080
# In a second terminal, to use the CMS locally:
npx decap-server
```

## Build

```bash
npm run build      # writes the site to _site/
```

## Deployment

The site is hosted on **Netlify**. `netlify.toml` runs `npm run build` and publishes `_site/`. A push to `main` triggers a fresh build and deploy (the GitHub Actions workflow in `.github/workflows/` also builds and deploys).

To enable CMS editing on the live site, turn on **Netlify Identity** and **Git Gateway** in the Netlify dashboard.

## To do after first deploy

- Replace the placeholder photos in `src/images/` (hero.jpg, living-room.jpg, bedroom.jpg, kitchen.jpg, terrace.jpg, sea-view.jpg, pool.jpg) with real apartment photos.
- Fill in the real `url` and `email` in `src/_data/site.json` (currently `[SITE_URL]` / `[BOOKING_EMAIL]`).
- Correct the apartment details in `src/_data/apartment.json`.
