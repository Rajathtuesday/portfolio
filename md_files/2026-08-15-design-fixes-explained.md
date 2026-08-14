# What changed today, and why

You asked whether the portfolio (and Rasova) reads as an "AI-made" website, because someone said that about the portfolio specifically and you don't want that said again. Here's exactly what I found and what I changed. README.md is now written for a visitor landing on the repo, not for you, so this file is the one with the dev notes and the reasoning.

## The actual diagnosis, not a vibe

I pulled the real HTML and CSS before saying anything, not a guess. Four concrete things were landing close to patterns that read as generic/AI-templated:

1. **The light-mode default was almost the exact AI-default cream.** `--accent-soft: #f6efe0` is nearly identical to the specific warm-cream `#F4F1EA` that's become a recognized AI-default background. Combined with the gold accent, it read as "warm cream with a terracotta-ish accent," one of the most commonly called out patterns right now.
2. **"Inter" was literally named in the font stack.** Inter is one of two fonts explicitly known as "the safe AI choice" (the other is Space Grotesk). Even sitting as a fallback, naming it is part of the tell.
3. **The three service cards used `01 / 02 / 03` as icons**, but the three services (web apps, mobile apps, security) aren't a sequence, there's no order between them. Numbered markers on non-sequential content is a specific named pattern, decoration pretending to be information.
4. **Every card used the identical `border-radius: 12px` plus the same soft double-shadow.** One repeated rounded-card-with-shadow component, reused everywhere, is the generic SaaS-template signature.

The copy and project descriptions were never the problem, they're specific and yours (the 373MB git history bloat fix, the exact compression percentages). Only the visual system needed work.

## What actually changed

- **Committed to dark-only.** The dark palette was already your real brand, the exact gold `#c5a059` used on Rasova, on `#0a0a0a`. Rather than keep a light variant that drifted toward generic cream, the site now just commits to the one look that's already distinctive and already yours. One considered theme beats a light/dark pair where only one half is actually good.
- **Added DM Serif Display for headings**, same font Rasova uses for its own headings, kept as a real Google Fonts link, not a system-font fallback. Body text stays on the system font stack, with `"Inter"` removed from the fallback list entirely.
- **`01/02/03` became `API / APP / SEC`.** Still short, still a small tag above each service title, but now it actually tells you what the category is instead of implying an order that doesn't exist.
- **Service cards lost their shadow and background fill**, they're flat with just a border now. The profile card and project cards kept their shadow. Two distinct card treatments instead of one component copy-pasted three times.

Checked it renders clean in a real browser before calling it done, screenshots matched what's described above, no console errors.

## Local preview and deploy (moved out of README.md)

No build step, plain HTML and CSS.

```
python -m http.server 8000
```

Then visit `http://localhost:8000`.

**GitHub Pages hosting**, one time setup:

1. Push to GitHub on the `main` branch.
2. Repo Settings &rarr; Pages.
3. Under Build and deployment, Source: Deploy from a branch.
4. Branch: `main`, folder `/ (root)`, save.
5. Live within a minute or two at `https://rajathtuesday.github.io/portfolio`.

Every push to `main` republishes automatically, no workflow file, no secrets.

**Custom domain, optional:** add a `CNAME` file to the repo root with just your domain name, set the same domain under Settings &rarr; Pages &rarr; Custom domain, add the DNS records GitHub shows you. GitHub issues the HTTPS cert automatically once DNS verifies.

## One known gap, unrelated to today's fix

The Shaping Metals project card still uses a text placeholder (`thumb-fallback`) instead of a real screenshot, every other project card already has one in `images/`. Worth dropping a real screenshot in next time you're in this repo.

## On Silvora

You also asked whether Silvora's UI is generic. Short version, checked separately: the **Flutter app itself holds up fine**, it uses DM Sans plus Syne (not Inter or Space Grotesk), a real two-color brand system, flat non-glassy cards. The **marketing website** (`templates/landing/index.html` in the backend repo) is a different story, it hits several strong, textbook AI-generic marketing-site patterns: `"Inter"` as the only named font, a large blurred purple glow-orb behind the hero (one of the most recognizable current AI-slop tells), heavy glassmorphism on every card, and fade-up-on-scroll reveals on every section. That one's worth the same treatment as this portfolio got, just say the word.
