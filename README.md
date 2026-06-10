# Vincent Genov — Portfolio

Personal portfolio and blog site. Built with [Astro](https://astro.build) and deployed to Vercel.

## Stack

- **Astro** — static site generator, all pages in `.astro`
- **No React** — intentional; keeps the site frontend-light
- Fonts: Fraunces + Newsreader + JetBrains Mono

## Dev

```bash
npm install
npm run dev      # http://localhost:4321
npm run build    # static output → dist/
npm run preview  # preview the build locally
```

## Structure

```
src/
  layouts/Base.astro       # nav, footer, social links
  pages/
    index.astro            # homepage
    projects/index.astro   # project list
    projects/*.astro       # individual project pages
    blog/index.astro       # blog index
    blog/*.astro           # blog posts
  styles/global.css        # all styles; color tokens at the top
public/
  assets/                  # images / GIFs (add locally)
  resume.pdf               # add locally
```

