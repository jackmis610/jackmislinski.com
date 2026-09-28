# jackmislinski.com

Static personal site. Pure HTML/CSS — no build step, no framework, no JS dependencies.

## Structure

```
jackmislinski.com/
├── index.html         # The site — bio, building, research, writing CTA
├── work.html          # Redirect stub → / (old page, kept so bookmarks don't 404)
├── funspan.html       # The Funspan framework (off-nav, linked from bio)
├── styles.css         # All styles
├── CNAME              # GitHub Pages custom domain
├── images/profile.jpg
├── papers/            # Research PDFs
├── biomarkers/        # Longevity Biomarker Heat Map (standalone HTML, synced from its repo)
└── wearables/         # Wearable Validity Atlas (standalone HTML, synced from its repo)
```

Nav: **Writing** only (goes straight to Substack). Footer: LinkedIn · X · Substack.

## Hosting

Deployed via GitHub Pages from `main`. DNS: A records at Wix → GitHub Pages IPs (Wix won't allow nameserver changes). Push to `main` and it's live in ~1 min.

## Syncing the hosted tools

`biomarkers/index.html` and `wearables/index.html` are copies of the standalone builds in their source repos. To update:

```bash
curl -sL https://raw.githubusercontent.com/jackmis610/longevity-biomarker-heatmap/main/heatmap/heatmap-standalone.html -o biomarkers/index.html
curl -sL https://raw.githubusercontent.com/jackmis610/wearable-validity-atlas/main/docs/index.html -o wearables/index.html
```

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
