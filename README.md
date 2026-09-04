# Fixline — Static Web Pages

Standalone, dependency-free static site for Fixline's public marketing and legal
pages. **Pure HTML + CSS, no JavaScript** — every page works with JS disabled,
so it can be hosted anywhere static, including **GitHub Pages**.

This project is intentionally separate from the `fixline` Expo app: the app
renders these screens natively for iOS/Android/web, while this repo is the
plain-HTML version for simple static hosting and SEO/crawler friendliness.

## Pages

| File | URL (once deployed) | Purpose |
| --- | --- | --- |
| `index.html` | `/` | Marketing landing page |
| `terms.html` | `/terms.html` | Terms of Service |
| `privacy.html` | `/privacy.html` | Privacy Policy |
| `cancellation-and-refund.html` | `/cancellation-and-refund.html` | Cancellation & Refund Policy |

Each page links to the others in its footer. Styling is a per-page `<style>`
block (no shared stylesheet, so each file is fully self-contained). The three
legal pages share a light document theme; `index.html` uses the app's dark
brand theme.

## Assets

`images/` holds the landing-page artwork (`.webp`) copied from the app. The
legal pages use no images. If the images are missing the landing page still
renders (the `<img>` tags simply show nothing).

## Preview locally

No build step. Open `index.html` directly in a browser, or serve the folder:

```bash
# any static server works, e.g.
python3 -m http.server 8080
# then open http://localhost:8080
```

## Deploy to GitHub Pages

1. Create a new GitHub repo (e.g. `fixline-web`) and push this folder:
   ```bash
   git init
   git add .
   git commit -m "Add Fixline static pages"
   git branch -M main
   git remote add origin git@github.com:<org-or-user>/fixline-web.git
   git push -u origin main
   ```
2. In the repo: **Settings → Pages**.
3. Under **Build and deployment → Source**, choose **Deploy from a branch**.
4. Select branch **`main`** and folder **`/ (root)`**, then **Save**.
5. Wait ~1 minute; the site publishes at
   `https://<org-or-user>.github.io/fixline-web/`.

The `.nojekyll` file ensures GitHub Pages serves the files verbatim (no Jekyll
processing).

### Custom domain (optional)

To serve on a custom domain, add a `CNAME` file containing the domain (e.g.
`fixline.example.com`) at the repo root, then configure the DNS record and the
domain under Settings → Pages.
