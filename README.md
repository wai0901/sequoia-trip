# Sequoia Road Trip site

A single-page, static, bilingual (中文 / EN) website for the Aug 6–9, 2026 Tesla trip to
Sequoia & Kings Canyon. Everything is in **`index.html`** — no build step, no dependencies.
Images come from Wikimedia Commons (fast 1280px thumbnails with automatic fallback to the
full image) and the mini-maps are free Google Maps embeds (no API key).

Default language is **Traditional Chinese**; the 中文 / EN toggle is top-right. All place
names stay in English; the descriptions, drive times, costs and notes switch language.

---

## Deploy to Vercel via GitHub — terminal steps

Run everything from inside this folder.

```bash
cd "sequoia-trip-site"
```

### A. Push to GitHub

First-time git setup only (skip if already done):
```bash
git config --global user.name  "Your Name"
git config --global user.email "snail0830@gmail.com"
```

Create the repo and first commit:
```bash
git init
git add .
git commit -m "Sequoia trip site"
git branch -M main
```

Then create the GitHub repo and push — **pick ONE:**

**Option 1 — GitHub CLI (easiest):**
```bash
gh auth login
gh repo create sequoia-trip --public --source=. --remote=origin --push
```

**Option 2 — create the repo on github.com manually:**
1. Go to https://github.com/new, name it `sequoia-trip`, leave it empty, click **Create repository**.
2. Then (replace `YOUR-USERNAME`):
```bash
git remote add origin https://github.com/YOUR-USERNAME/sequoia-trip.git
git push -u origin main
```

### B. Connect to Vercel
1. Go to https://vercel.com, sign in **with GitHub**.
2. **Add New… → Project**, import the `sequoia-trip` repo.
3. Framework Preset: **Other**. Leave Build Command and Output Directory **empty**.
4. **Deploy** → you get a live URL like `https://sequoia-trip.vercel.app`.

Every later `git push` auto-redeploys:
```bash
git add .
git commit -m "update"
git push
```

If `git push` asks for a password, use a GitHub **personal access token** (Settings →
Developer settings → Personal access tokens), not your account password.

---

## Editing content
- All trip data is in the `D` array near the bottom of `index.html` — edit text, distances,
  costs, images (`IMG` object) or coordinates there, then push again.
- Each stop has English + `_zh` (Traditional Chinese) fields; update both when you change text.
- If a photo ever fails, the card automatically falls back to a labeled colored tile.
- Distances/times are driving estimates; confirm live in Google Maps/Waze on the day, and
  re-check park prices and the Crystal Cave / shuttle status on nps.gov/seki before you go.
