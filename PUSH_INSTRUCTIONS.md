# Push & Deploy Instructions — leoromero.dev

This file walks through the three things you need to do from your personal
machine to get `leoromero.dev` live: create the GitHub repo, push the initial
commit, and deploy to Vercel with the custom domain.

The local repo is at `/home/leo/projects/leoromero-dev/` with the initial
commit already made on the `main` branch.

---

## Step 1 — Local preview (optional but recommended)

Before pushing, sanity-check the site renders the way you want:

```bash
cd /home/leo/projects/leoromero-dev
python3 -m http.server 8080
# then open http://localhost:8080 in your browser
```

Check: hero copy, project cards (Prob-Edge live link, Smart-Beta repo link, PaPs Mercados repo link), Writing section, Contact section.

---

## Step 2 — Create the GitHub repo

Open <https://github.com/new> and create the repo:

- **Owner:** `leoromero-quant`
- **Repository name:** `leoromero-dev`
- **Description:** `Personal landing site for Leonardo Suárez Romero, PhD. Static HTML, Vercel-deployed.`
- **Visibility:** Public
- **Initialize:** leave ALL three checkboxes UNCHECKED.

Click **Create repository**.

---

## Step 3 — Push the local repo

```bash
cd /home/leo/projects/leoromero-dev

# Verify the initial commit is there
git log --oneline -1
# Should show: 3b935ce Initial commit: leoromero.dev personal landing

# Add the GitHub remote
git remote add origin git@github.com:leoromero-quant/leoromero-dev.git
# or HTTPS: git remote add origin https://github.com/leoromero-quant/leoromero-dev.git

# Push
git push -u origin main
```

---

## Step 4 — Deploy to Vercel

Two paths, pick whichever you have set up.

### Path A — Vercel UI (recommended first time)

1. Go to <https://vercel.com/new>.
2. **Import Git Repository** → pick `leoromero-quant/leoromero-dev`.
3. Framework Preset: **Other** (it is plain static HTML, no framework).
4. Root Directory: leave as default.
5. Build Command: leave empty.
6. Output Directory: leave empty (Vercel serves the repo root).
7. Click **Deploy**.

You should see your first preview URL within 30 seconds, something like
`leoromero-dev-xxxx.vercel.app`.

### Path B — Vercel CLI

```bash
npm i -g vercel
cd /home/leo/projects/leoromero-dev
vercel --prod
```

Follow the prompts. The `vercel.json` in this repo configures clean URLs and
security headers automatically.

---

## Step 5 — Wire the custom domain `leoromero.dev`

In the Vercel project dashboard:

1. **Settings** → **Domains** → **Add Domain**.
2. Enter `leoromero.dev`. Vercel will show the DNS records you need.
3. If your domain registrar is Namecheap, Cloudflare, GoDaddy, etc., copy the
   `A` record (for the apex) and the `CNAME` (for `www`) into the registrar's
   DNS panel.
4. Wait 5 to 30 minutes for DNS propagation. Vercel auto-issues the SSL cert
   via Let's Encrypt once DNS resolves.

Optional: also add `www.leoromero.dev` and redirect it to the apex.

---

## Step 6 — Verify and announce

Once live, do this sanity check:

- Open <https://leoromero.dev> and confirm it loads with HTTPS.
- Verify every external link works: `prob-edge.com`, the Prob-Edge repo, the Smart-Beta repo (depends on the smart-beta push being done first), the PaPs Mercados repo, the LinkedIn URL, the GitHub URL, the email link.
- Run Lighthouse from Chrome DevTools and target Performance ≥ 95, Accessibility ≥ 95, SEO ≥ 95. The current template should hit all three.

Then update your LinkedIn header URL and your CV V3 PDF footer to point at
`leoromero.dev` instead of the email address alone.

---

## Step 7 — Delete this file from the repo

Once everything is live, remove this file:

```bash
git rm PUSH_INSTRUCTIONS.md
git commit -m "Remove internal push instructions"
git push
```

---

## What to iterate next (post-launch)

- Add a real Markdown post for the LinkedIn Prob-Edge article on 2026-05-19 in a `/writing/` folder, and link it from the Writing section.
- When new cover letters mention additional projects, add cards to the Projects section.
- After the first callback from the 13 May 16 applications materializes into an offer, add a brief "currently considering" note to the Contact section.
- Consider migrating to Next.js if you want MDX-based writing later. The current static HTML can be migrated to one Next.js page in a couple of hours.
