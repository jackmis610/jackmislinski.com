# jackmislinski.com

Static personal site. Pure HTML/CSS — no build step, no framework, no JS dependencies.

## Structure

```
jackmislinski.com/
├── index.html         # Homepage — bio + featured work + writing CTA
├── work.html          # Research, building, code
├── funspan.html       # The Funspan framework / brand pitch
├── styles.css         # All styles
└── images/
    └── profile.jpg    # Profile photo
```

Nav: **Work · Funspan · Writing**. Writing goes straight to Substack.

## Content placeholders

Search the HTML for `[REPLACE: ...]` markers — these are spots where I left guess-text or asked for a sentence. Currently:

- `index.html` / `work.html` — Aevox one-liner (best version) and the CPET validation paper description.
- `funspan.html` — one or two sentences for each of the four pillars (Biology, Passion, Relationships, Psychology).

## Local preview

```bash
cd ~/jackmislinski.com
python3 -m http.server 8000
# open http://localhost:8000
```

## Deploy options

Pick one. All three are free and support the custom domain `jackmislinski.com`.

### Cloudflare Pages (recommended)
1. Push this directory to a new GitHub repo.
2. cloudflare.com/pages → "Connect to Git" → pick the repo.
3. Build command: *(empty)*. Output: `/`.
4. Custom domains → add `jackmislinski.com` and `www.jackmislinski.com`. Cloudflare gives you the DNS records.
5. Point your registrar at Cloudflare (or just add the records they show).

### GitHub Pages
1. Push to a repo named `jackmislinski.github.io` (or any repo with Pages enabled on `main`).
2. Repo Settings → Pages → Source: `main` / `/ (root)`.
3. Add a `CNAME` file containing `jackmislinski.com` (already optional, can add when ready).
4. At your DNS provider, add an `A` record for `@` → GitHub's IPs, and `CNAME` for `www` → `<user>.github.io`.

### Netlify
1. netlify.com → "Add new site" → "Deploy manually" → drag the folder.
2. Site settings → Domain management → add `jackmislinski.com`.
3. Follow Netlify's DNS instructions.

## Editing

Each page duplicates the header + footer. When you change nav links or social icons, update all five HTML files (or ask me to do it). If pages multiply, consider a tiny build step or switch to a static site generator.

## DNS cutover from Wix

1. Deploy to your host of choice; verify at the host-provided URL.
2. In your domain registrar, update DNS to point at the new host.
3. Disconnect the domain from Wix last, only after the new site is live.
