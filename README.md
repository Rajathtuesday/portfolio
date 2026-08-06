# Rajath, Portfolio

Personal portfolio site. Plain HTML and CSS, no build step, no framework.

## Local preview

Open `index.html` directly in a browser, or run a tiny local server so relative paths behave the same as production:

```
python -m http.server 8000
```

Then visit `http://localhost:8000`.

## Before this goes live

1. **Contact form.** The form points at `https://formspree.io/f/your-form-id`, a placeholder. Sign up at formspree.io, create a form, and swap in your real endpoint in `index.html`, in the `<form action="...">` line.
2. **Project screenshots.** Each project card has a text placeholder instead of a real image. Drop real screenshots into an `images/` folder and swap the `.project-thumb` text for an `<img>` tag once you have them.

## GitHub Pages hosting, one time setup

No build step here, so this is genuinely a two minute setup, no workflow file needed at all.

1. Push this repo to GitHub, on the `main` branch.
2. In the repo, go to **Settings, Pages**.
3. Under **Build and deployment**, set **Source** to **Deploy from a branch**.
4. Set **Branch** to `main`, folder `/ (root)`, then save.
5. GitHub gives you a URL, something like `https://rajathtuesday.github.io/portfolio`. That is live within a minute or two of saving.

**Custom domain, optional.** If you want your own domain instead of the github.io one, add a `CNAME` file to the repo root containing just your domain name, then set that same domain in **Settings, Pages, Custom domain**, and add the DNS records GitHub shows you at your domain registrar. GitHub issues the HTTPS certificate for you automatically once DNS is verified, nothing to set up by hand.

From then on, every push to `main` republishes the site automatically. No secrets, no separate deploy step.
