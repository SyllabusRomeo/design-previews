# Permanent free hosting (no paid plan, no custom domain)

This project is a **static site** (HTML / CSS / fonts). You do not need a paid host, a custom domain, or a 24-hour trial URL.

**Recommended:** [GitHub Pages](#1-github-pages--recommended) — already matches this repo, free forever on the public `*.github.io` URL.

---

## Comparison

| Host | Free public URL | Custom domain required? | Good for this repo? | Caveats |
|------|-----------------|-------------------------|---------------------|---------|
| **GitHub Pages** | `https://SyllabusRomeo.github.io/design-previews/` | No | Best fit | Public repo (or GitHub Pro for private Pages) |
| **Cloudflare Pages** | `*.pages.dev` | No | Excellent | Free Cloudflare account |
| **Netlify** | `*.netlify.app` | No | Excellent | Free bandwith/build limits (fine for mocks) |
| **Vercel** | `*.vercel.app` | No | Excellent | Free hobby tier |
| **GitLab Pages** | `*.gitlab.io` | No | Good | Needs GitLab project / mirror |
| **Surge** | `*.surge.sh` | No | Good | CLI deploy; free subdomain |
| **Render Static Site** | `*.onrender.com` | No | OK | Free static CDN; keep as *static site*, not a free web service |
| **here.now** | `*.here.now` | No | Temporary only | Anonymous / TTL sites expire (e.g. 24h) — not for permanent board |

Avoid relying on **here.now** for the lasting decision board. Use it for quick throwaway links if you want; keep this repo + Pages (or similar) as the permanent home.

---

## 1. GitHub Pages — recommended

Repo: https://github.com/SyllabusRomeo/design-previews  

Expected URL after enable:

**https://SyllabusRomeo.github.io/design-previews/**

### Enable in the UI

1. Open the repo → **Settings** → **Pages**
2. Under **Build and deployment** → **Source**, choose **Deploy from a branch**
3. Branch: **`main`** · Folder: **`/ (root)`**
4. Save
5. Wait 1–2 minutes, then open the Pages URL

### Enable via CLI (if `gh` is logged in)

```bash
gh api -X POST repos/SyllabusRomeo/design-previews/pages -f build_type=legacy -f source[branch]=main -f source[path]=/
```

Or in newer repos:

```bash
gh api -X PUT repos/SyllabusRomeo/design-previews/pages -f build_type=workflow
```

For this static root site, **Deploy from a branch / `main` / root** is enough — no GitHub Actions required.

### After it is live

- Share `https://SyllabusRomeo.github.io/design-previews/` internally  
- Every `git push` to `main` updates the site  
- No domain purchase needed  

**Private repos:** GitHub Pages on private repositories requires a paid GitHub plan. Keep the repo **public** (as it is now) for free Pages, or use Cloudflare/Netlify/Vercel free tiers with a private Git connection.

---

## 2. Cloudflare Pages

1. Sign up at [Cloudflare Pages](https://pages.cloudflare.com/) (free)
2. **Create project** → connect GitHub → select `design-previews`
3. Build settings:
   - Framework preset: **None**
   - Build command: *(leave empty)*
   - Output directory: `/` or `.`
4. Deploy  
5. Use the free `*.pages.dev` URL (custom domain optional)

---

## 3. Netlify

1. Sign up at [Netlify](https://www.netlify.com/) (free)
2. **Add new site** → Import from Git → `design-previews`
3. Build command: empty · Publish directory: `.` (repo root)
4. Deploy  
5. Use free `*.netlify.app` URL  

Optional `netlify.toml` in repo root:

```toml
[build]
  publish = "."
```

---

## 4. Vercel

1. Sign up at [Vercel](https://vercel.com/) (Hobby / free)
2. Import `design-previews`
3. Framework: **Other** · Output: repo root  
4. Deploy  
5. Use free `*.vercel.app` URL  

Optional `vercel.json`:

```json
{
  "cleanUrls": true,
  "trailingSlash": false
}
```

---

## 5. Surge.sh (CLI, no Git required)

```bash
npm install -g surge
cd design-previews
surge . your-name-designlanguages.surge.sh
```

Free `*.surge.sh` subdomain. Good for a one-off publish without connecting Git.

---

## 6. Render static site

1. [Render](https://render.com/) → **New** → **Static Site**
2. Connect this GitHub repo
3. Build command: empty (or `echo ok`)
4. Publish directory: `.`
5. Use free `*.onrender.com` URL  

Do **not** deploy this as a free **Web Service** (those spin down). Use **Static Site** only.

---

## What you do *not* need

- A paid hosting plan  
- A purchased domain (all options above give a free HTTPS subdomain)  
- A server, Docker, or database  
- here.now auth / TTL for permanent access  

---

## Suggested default for this project

1. Turn on **GitHub Pages** from `main` / root  
2. Put that URL in Slack / Notion as the permanent design board  
3. Treat here.now (if used) as disposable only  

When Pages is on, update the main [README](./README.md) live link from the temporary here.now URL to:

`https://SyllabusRomeo.github.io/design-previews/`
