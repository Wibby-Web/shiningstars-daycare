# ShiningStars Early Learning Center

A bilingual (English / French) website for a daycare and preschool, built with the [Eleventy](https://www.11ty.dev/) static site generator.

The site presents the daycare's programs, philosophy, educators, photo gallery, and contact information in both languages. It is fully static, fast, and can be deployed to GitHub Pages or Netlify.

## Pages

| English | French | Content |
| --- | --- | --- |
| `/` | `/fr/` | Home: hero, philosophy, programs, testimonials, call to action |
| `/programs/` | `/fr/programs/` | Infant, toddler, and pre-K programs, plus enrichment activities |
| `/about/` | `/fr/about/` | Story, values, and educator profiles |
| `/gallery/` | `/fr/gallery/` | Photo gallery |
| `/contact/` | `/fr/contact/` | Contact details, opening hours, and a Netlify-ready form |

## Features

- **Bilingual content and navigation** — English and French pages, with a language switcher in the header.
- **Responsive layout** — mobile, tablet, and desktop styling with CSS Grid and Flexbox.
- **No JavaScript framework** — plain HTML, CSS, and a small script for the mobile menu and icons.
- **Fast by default** — CSS and JavaScript are inlined and minified at build time.
- **Editable in Markdown** — page copy lives in Markdown files with HTML sections where needed.
- **Automatic navigation** — powered by [Eleventy Navigation](https://www.11ty.dev/docs/plugins/navigation/).
- **Contact form** — uses Netlify Forms when deployed to Netlify.

## Tech stack

- [Eleventy 3](https://www.11ty.dev/) with Nunjucks and Liquid templates
- [Eleventy Navigation](https://www.11ty.dev/docs/plugins/navigation/) and [Eleventy I18n](https://www.11ty.dev/docs/plugins/i18n/)
- Vanilla CSS and JavaScript
- [Lucide](https://lucide.dev/) icons and Google Fonts (Poppins)
- Node.js 22 (see `.nvmrc`)

## Project structure

```text
.
├── _data/
│   └── metadata.json          # Site title, URL, description, author
├── _includes/
│   ├── assets/
│   │   ├── css/inline.css     # All site styles (inlined at build)
│   │   └── js/inline.js       # Mobile menu behavior
│   ├── components/            # head, nav, footer, ...
│   └── layouts/               # base, home, page, contact, post
├── en/                        # English pages + en.json
├── fr/                        # French pages + fr.json
├── static/img/                # Images and illustrations
├── posts/                     # Sample blog posts from the original boilerplate
├── .eleventy.js               # Eleventy configuration
├── netlify.toml               # Netlify build settings
└── package.json
```

## Getting started

### Requirements

- [Node.js](https://nodejs.org/) 22 (or 18+)
- npm

### Install and run

```bash
git clone https://github.com/xuefei519/shiningstars-daycare.git
cd shiningstars-daycare
npm install
npm run serve
```

The local site runs at <http://localhost:8080> and reloads when you save a file.

To create a production build in `_site/`:

```bash
npm run build
```

## Editing the site

### Site-wide information

Update `_data/metadata.json` to change the site name, URL, description, and contact email:

```json
{
  "title": "ShiningStars",
  "url": "https://shiningstars-example.com/",
  "language": "en",
  "description": "A loving and happy place for early childhood development, structured learning, and play.",
  "author": {
    "name": "ShiningStars Early Learning Center",
    "email": "hello@shiningstars-example.com",
    "url": "https://shiningstars-example.com/about/"
  }
}
```

### Page content

Each page is a Markdown file in `en/` or `fr/`:

- `en/home.md` and `fr/home.md`
- `en/programs.md` and `fr/programs.md`
- `en/about.md` and `fr/about.md`
- `en/gallery.md` and `fr/gallery.md`
- `en/contact.md` and `fr/contact.md`

The front matter controls the page:

```yaml
---
title: Our Programs
metaDescription: Discover the play-based learning programs we offer at ShiningStars.
date: 2024-01-01T00:00:00.000Z
permalink: /programs/index.html
eleventyNavigation:
  key: Programs
  order: 1
---
```

- `permalink` is the output URL.
- `eleventyNavigation.order` controls the position in the header navigation (0–4).
- Keep the English and French versions of a page at matching paths: `/about/` and `/fr/about/`.

Layouts, navigation, and the footer are in `_includes/`. Global styles are in `_includes/assets/css/inline.css`.

### Images

Page images are served from `static/img/opt/` in 800px and 1600px versions. Use both with `srcset`/`sizes` so the browser downloads the smallest suitable file, and add `loading="lazy"`, `decoding="async"`, and explicit `width`/`height`:

```html
<img src="/static/img/opt/teacher-reading-1600.jpg"
     srcset="/static/img/opt/teacher-reading-800.jpg 800w, /static/img/opt/teacher-reading-1600.jpg 1600w"
     sizes="(min-width: 768px) 50vw, 100vw"
     width="1600" height="1067"
     alt="Teacher reading to children" loading="lazy" decoding="async">
```

The full-resolution originals stay in `static/img/`; the `static/img/opt/` files are what the pages load. Hero backgrounds use a single 1600px file, with an 800px override for mobile in `inline.css`. When adding a new image, generate the same 800/1600 variants before referencing it.

The logo and favicon use the same star mark: `static/img/logo.svg` (header and footer), `favicon.svg` and `favicon.ico` (browser tabs), and `apple-touch-icon.png` (mobile home screens). Replace all of them together if you change the logo.

### Contact form

The contact form uses `data-netlify="true"`. When the site is deployed to Netlify, submissions appear in the Netlify dashboard under **Forms**. The form does not submit on GitHub Pages because GitHub Pages is static-only; connect a form service if you deploy there.

## Bilingual setup

- `en/en.json` and `fr/fr.json` set the default layout, language, and collection tag for each folder.
- The header navigation is generated per language from `collections.en` and `collections.fr`.
- The language switcher uses Eleventy's `locale_links` filter and falls back to the other language's home page when a translation is missing.
- To add a page, create the same file in both `en/` and `fr/` with matching `permalink` paths and navigation order.

## Deployment

### GitHub Pages

A workflow is included at `.github/workflows/deploy-pages.yml`.

1. In the repository, go to **Settings → Pages** and set **Source** to **GitHub Actions**.
2. Push to the `develop` branch, or run the workflow manually from the **Actions** tab.
3. The site is published under `https://<username>.github.io/<repository>/`.

The workflow sets `SITE_BASE_PATH` to the repository name so internal links and assets work when the site is served from a subdirectory. To deploy from another branch, change the `branches` list in the workflow. If you attach a custom domain to the site, remove `SITE_BASE_PATH` from the workflow so URLs stay at the domain root.

### Netlify

1. Push the project to GitHub, GitLab, or Bitbucket.
2. In [Netlify](https://app.netlify.com/), choose **Add new site → Import an existing project**.
3. Select the repository. Netlify reads `netlify.toml`:
   - **Build command:** `npm run build`
   - **Publish directory:** `_site`
4. Deploy. Every push to the production branch triggers a new build.

## Available scripts

| Command | Description |
| --- | --- |
| `npm run build` | Build the site into `_site/` |
| `npm run serve` | Start a local server with live reload |
| `npm run watch` | Rebuild on file changes without a server |
| `npm run debug` | Build with Eleventy debug output |

## Before you launch

The site ships with placeholder content. Update:

- Rename the GitHub repository to `shiningstars-daycare` (or update the clone command above) so the repository link matches
- The address, phone number, and email in `en/contact.md`, `fr/contact.md`, and `_includes/components/footer.njk`
- The site URL and email in `_data/metadata.json`
- The testimonials, educator names, and photos in the Home and About pages
- The opening hours on the Contact pages
- The gallery captions and images, if needed

## Credits and license

Released under the [MIT License](LICENSE).

Based on the [Eleventy Netlify Boilerplate](https://github.com/danurbanowicz/eleventy-netlify-boilerplate) by Dan Urbanowicz. Sample images are placeholders and should be replaced with your own.
