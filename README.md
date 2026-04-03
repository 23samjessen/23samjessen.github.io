# CV_project

A multilingual static CV website for **Sam Jessen**.

## Included

- English, Danish, and Swedish CV pages
- English, Danish, and Swedish motivation-letter pages
- language switcher
- one shared downloadable CV for all language pages
- LinkedIn icon in the top bar
- public certificate section
- private recommendation-letter workflow
- dark mode toggle
- Cloudflare Web Analytics snippet
- print-friendly layout
- Docker support
- GitHub Pages support

---

## Project Info

- GitHub username: `23samjessen`
- Repository: `23samjessen.github.io`
- Repository URL: `https://github.com/23samjessen/23samjessen.github.io`
- Live site: `https://23samjessen.github.io/`
- English CV page: `https://23samjessen.github.io/`
- Danish CV page: `https://23samjessen.github.io/da/`
- Swedish CV page: `https://23samjessen.github.io/sv/`
- English motivation letter page: `https://23samjessen.github.io/motivation-letter.html`
- Danish motivation letter page: `https://23samjessen.github.io/da/motivation-letter.html`
- Swedish motivation letter page: `https://23samjessen.github.io/sv/motivation-letter.html`
- LinkedIn: `https://www.linkedin.com/in/samjessen-a-938572b4/`

---

## Run Locally

### Python

```bash
python3 -m http.server 8000
```

If `python3` does not work:

```bash
python -m http.server 8000
```

Open:

```text
http://localhost:8000
http://localhost:8000/da/
http://localhost:8000/sv/
```

### Docker

```bash
docker compose up --build
```

Open:

```text
http://localhost:8080
http://localhost:8080/da/
http://localhost:8080/sv/
```

Stop Docker:

```bash
docker compose down
```

---

## Where To Edit Things

### Main website text

```text
src/js/data/site-data.js
```

This controls:
- hero text
- contact section
- experience
- education
- skills
- languages
- motivation letter text
- documents section

### Remove or change the thesis sentence / badge

Edit:

```text
src/js/data/site-data.js
```

Fields:
- `en.hero.badge`
- `da.hero.badge`
- `sv.hero.badge`

The badge is rendered conditionally in:

```text
src/js/renderers/cv-renderer.js
```

### Change how CV sections are rendered

```text
src/js/renderers/cv-renderer.js
```

### Change how motivation-letter pages are rendered

```text
src/js/renderers/motivation-renderer.js
```

### Change layout, colors, spacing, buttons, LinkedIn icon styling

```text
src/css/main.css
```

### Change wrapper pages, nav, LinkedIn link, Cloudflare snippet, download buttons

```text
index.html
motivation-letter.html
da/index.html
da/motivation-letter.html
sv/index.html
sv/motivation-letter.html
```

### Shared downloadable CV used by all pages

```text
assets/sam-jessen-cv.pdf
```

### Public certificate PDFs

```text
assets/documents/certificates/
```

### Private recommendation letter reference

```text
private/recommendation/google-drive-link.private.txt
```

---

## GitHub Setup

From your local project folder:

```bash
cd /Users/sam/Desktop/My_online_CV_2/New_repo/CV_project
```

### First clean upload

```bash
rm -rf .git
git init
git branch -M main
git remote add origin https://github.com/23samjessen/23samjessen.github.io.git
git remote -v
grep -RIn '<<<<<<<\|=======\|>>>>>>>' .
git add -A
git commit -m "Upload final clean CV project"
git push -u origin main
git commit --allow-empty -m "Trigger GitHub Pages rebuild"
git push
```

### Normal update workflow later

```bash
git status
git add .
git commit -m "Describe your update"
git push
```

### Pull latest changes

```bash
git pull origin main
```

### Check current remote

```bash
git remote -v
```

### If the remote already exists

```bash
git remote set-url origin https://github.com/23samjessen/23samjessen.github.io.git
git remote -v
```

### Force push if you want to replace the remote completely

```bash
git push -u origin main --force
```

---

## GitHub Pages Setup

Repository:

```text
https://github.com/23samjessen/23samjessen.github.io
```

Then:
1. Open **Settings**
2. Open **Pages**
3. Set:
   - **Source** = `Deploy from a branch`
   - **Branch** = `main`
   - **Folder** = `/ (root)`
4. Save

Live site:

```text
https://23samjessen.github.io/
```

---

## Cloudflare Web Analytics

The Cloudflare snippet is included in all page wrappers.

Token used:

```text
83ba0d1129184ee4b13054f40157b5ac
```

If you need to remove or replace it, edit these files:

```text
index.html
motivation-letter.html
da/index.html
da/motivation-letter.html
sv/index.html
sv/motivation-letter.html
```

Look for:

```html
<script defer src="https://static.cloudflareinsights.com/beacon.min.js" data-cf-beacon='{"token": "83ba0d1129184ee4b13054f40157b5ac"}'></script>
```

---

## SSH Setup (Optional)

```bash
ls -al ~/.ssh
ssh-keygen -t ed25519 -C "23samjessen@gmail.com"
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
cat ~/.ssh/id_ed25519.pub
ssh -T git@github.com
git remote set-url origin git@github.com:23samjessen/23samjessen.github.io.git
git remote -v
```

---

## Notes

- The live site stays online even when VS Code is closed
- GitHub Pages updates after each push
- The recommendation letter should stay out of the public repo
- Certificates are fine to keep public on the site
- The private Google Drive link should stay only in the private folder
- Use only one working project folder to avoid Git conflicts
- All **Download CV** buttons use the same shared file:

```text
assets/sam-jessen-cv.pdf
```
