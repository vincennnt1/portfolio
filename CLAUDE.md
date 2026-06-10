# CLAUDE.md — Portfolio Project Context

This file gives Claude Code the context and decisions behind this project so future
sessions can continue without re-explaining. Read this first.

## What this is

The personal portfolio + blog for **Vincent Genov**, a Data Science student at the
University of Waterloo. Goal: a clean, recruiter-facing site that showcases two to three
projects and hosts a blog for documenting findings (mainly from the arms tracker).

Built with **Astro** (static site). Deploys to Vercel/Netlify. Every page is a plain
`.astro` file — basically HTML with a small frontmatter block. **No React was used or
needed**, and that's intentional (see preferences below).

## Owner preferences (important — these drove the design)

- **Avoid hand-writing React frontend.** Vincent has shipped React before (the arms-tracker
  viz uses React 18 + D3), so it's a preference, not a skill gap. Keep pages in Markdown-like
  `.astro`. If the live arms-tracker visualization ever gets embedded, do it as an isolated
  Astro island so the rest of the site stays frontend-light.
- **Visual direction: clean & minimal**, modeled on a friend's site (vnguyen.org) — light
  background, simple link-forward nav (Projects / Blog / Resume), one-line intro, a "Recently"
  bullet list. Chosen over a darker "data-journalism" look. Keep it understated.
- **Tagline:** "I like using data to tell stories — lately, 85 years of the global arms trade."
  The simple first half is the hook; the specific tail is what stops a recruiter's skim. Keep
  both halves.
- **Priority is impressing recruiters for data roles.** The codebase itself is part of the
  impression, so keep it tidy.

## Project hierarchy (deliberate arc: serious → fun)

1. **Global Arms Trade Network** — THE centerpiece. Lead with it everywhere. SIPRI arms-transfer
   data 1940–2025, 258 countries, 3,150 supplier→recipient flows, 497 anomaly spikes. Python ETL
   (pandas/Jupyter), directed graph + Louvain community detection (networkx), rolling HHI +
   Z-score anomaly detection, async Gemini API for geopolitical context, cross-referenced against
   UCDP conflict data. Rendered as an interactive world map in React + D3. Repo: WatchTower.
2. **Bad Link** — the "personality" project. Two-player co-op puzzle game, C++ + SFML, NO game
   engine (all logic from scratch), built in 48h for Mini Jam 111 (theme: Colors). Downloadable
   on Itch.io (vincennnt1.itch.io/bad-link). Should sit clearly as the second/"for fun" project,
   not competing with the data work.

## Blog

Documents findings from the arms tracker. The differentiator: lots of students show projects,
few document their thinking. First post stub exists at `src/pages/blog/reading-the-arms-trade.astro`
with italic prompts marking what to write. The strong move is to pick ONE of the 497 anomaly
spikes (ideally where the Gemini context lined up with UCDP conflict data) and tell it as a small
story: year, country, what the data said, whether it matched a real event, what surprised you.
One good post beats five thin ones.

## File structure

- `src/pages/index.astro` — homepage (tagline + "Recently" list)
- `src/pages/projects/index.astro` — projects list (array at top of file)
- `src/pages/projects/*.astro` — one file per project page
- `src/pages/blog/index.astro` — blog index (posts array at top)
- `src/pages/blog/*.astro` — blog posts
- `src/layouts/Base.astro` — nav, footer, social links
- `src/styles/global.css` — ALL styling; colors + fonts are at the very top

## Styling notes

Confirmed color palette:
- `--bg`:      #1a1815  (dark warm brown-black)
- `--surface`: #222018  (slightly lighter, cards/hover)
- `--border`:  #302c26  (separator lines)
- `--muted`:   #7a746e  (nav links, secondary text)
- `--text`:    #e8e3db  (warm off-white body text)
- `--accent`:  #c0623e  (terracotta — links, emphasis)

Fonts: Fraunces (display/headings, weight 300) + Newsreader (body, weight 300) + JetBrains Mono
(labels/meta, uppercase 0.75rem). Re-theme by changing `--accent` in one line. Keep the restraint
— minimal designs live or die on spacing and typography, so resist adding clutter.

## Project page shape (use for any new project)

problem → what I built → the hard part (the interesting technical bit) → what I'd do next.
The "hard part" section is what makes a junior portfolio read as credible. Don't just paste READMEs.

## Outstanding to-do (owner's part)

1. Add images to `public/assets/`: arms map screenshot/GIF (`arms-map.png`), an anomaly chart
   (`arms-spike.png`), a Bad Link gameplay GIF (`bad-link.gif`). Placeholders in the pages mark
   exactly where each goes. For the game, a GIF does ~90% of the persuading.
2. Drop resume at `public/resume.pdf` (nav already links to it).
3. Finish the first blog post (prompts are in the file).
4. Fix the Bad Link GitHub repo README — it currently says "try out habitHacker" in the download
   section (copy-paste leftover). Also add descriptions to the pinned repos; recruiters click through.
5. Add a live demo link to the arms project page if the visualization gets deployed.

## Commands

```bash
npm install
npm run dev      # http://localhost:4321
npm run build    # static output to dist/
```

## Identity / links

- Name: Vincent Genov
- Email: vgenov@uwaterloo.ca
- GitHub: github.com/vincennnt1
- LinkedIn: linkedin.com/in/vincent-genov/
- School: University of Waterloo, Honours BMath in Data Science (Sept 2024 – Aug 2029)
