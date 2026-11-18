# Mooscles

A free workout tracker that runs entirely in the browser.
No account, no server, no build step — one self-contained `index.html`.

**Repo:** https://github.com/aloysiusng/mooscles

Send the link (or the file) to anyone and they get their own tracker.
Each person's routines, history and measurements are stored in their
own browser's `localStorage` on their own device — nothing is uploaded
anywhere, and nobody can see anyone else's workouts.

Mooscles has its own look on purpose: a pine-green and rust palette,
warm paper background, condensed display headings, and squarer,
chunkier controls — built from scratch, not a reskin of any other app.
It follows your system light / dark setting.

## Features

- **Unlimited routines** — Push / Pull / Legs / Upper / Lower templates,
  or build your own with per-exercise sets, rep targets and rest times
- **Set-by-set logging** — previous performance shown next to every set,
  weight/reps prefilled from last time
- **Checked sets only** — finishing a workout saves only the sets you
  ticked ✓; unchecked sets are dropped
- **Rest timer** — starts automatically when you check a set, with
  selectable durations (presets or custom), +15s / −15s, sound and
  vibration alerts
- **PR detection** — trophy badge and toast when you beat your best
  weight or estimated 1RM (warmup sets excluded)
- **Exercise catalogue** — 43 built-in exercises with movement
  thumbnails, plus your own custom exercises; per-exercise stats,
  best weight, estimated 1RM and a progress chart
- **History** — every finished workout with volume, duration and PRs;
  repeat any past workout in one tap
- **Body measurements** — weight, body fat, waist and 13 more fields,
  with a weight-trend chart
- **Backup & transfer** — export/import a JSON backup (`mooscles-backup.json`),
  and export or import CSV so you can move data in or out

## Host it yourself

Mooscles is a single static file, so it hosts anywhere that can serve
HTML. Pick whichever you already use — you only need one.

### Option 1 — Host it in Muse

Muse can host Mooscles as your own personal web space, with a
shareable link. Your visitors still get separate data — each browser
keeps its own `localStorage`.

1. Get the code: fork [aloysiusng/mooscles](https://github.com/aloysiusng/mooscles)
   on GitHub, or download `index.html` from this repo.
2. Open [Muse](https://muse.ai) and start a new chat.
3. Attach / upload `index.html` (or paste the GitHub repo link) and ask:

   > Create a static web artifact called **Mooscles** from this
   > `index.html`. Keep it as a single self-contained page with no
   > server and no account — data stays in each visitor's browser.

4. Muse builds the space and gives you a link. Share that link with
   anyone you want to use it.
5. To change it later (colours, exercises, features), just ask Muse
   in the same chat to edit the space — for example *"change the accent
   colour to forest green"* — and it will rebuild and republish it.

> Note: there is no Muse app-store approval step. A Muse-hosted
> Mooscles is simply your own space with a shareable link — describe it
> as *"built with Muse"*, not as an official Muse app.

### Option 2 — Host it on Vercel (free)

**From the Vercel dashboard (no terminal needed):**

1. Fork [aloysiusng/mooscles](https://github.com/aloysiusng/mooscles)
   to your own GitHub account (or use **Use this template** if enabled).
2. Go to [vercel.com/new](https://vercel.com/new) and sign in with GitHub.
3. Import your `mooscles` repository.
4. On the configure screen:
   - **Framework Preset:** `Other`
   - **Build Command:** leave empty — there is no build step
   - **Output Directory:** leave empty / root (`.`)
   - **Environment variables:** none needed
5. Click **Deploy**. Vercel gives you a live URL like
   `https://mooscles-<your-name>.vercel.app`.
6. Every push to `main` redeploys automatically. To use your own
   domain, add it under Project → Settings → Domains.

**From the terminal (Vercel CLI):**

```sh
git clone https://github.com/aloysiusng/mooscles.git
cd mooscles
npm i -g vercel   # once, if you don't have it
vercel            # preview deployment — follow the prompts
vercel --prod     # production deployment
```

No `package.json`, build command or server is required — Vercel just
serves `index.html` as a static site.

### Option 3 — GitHub Pages

Push this repo, then in Settings → Pages choose "Deploy from a branch"
→ `main` → `/ (root)`. Mooscles will be live at
`https://<username>.github.io/mooscles/`.

### Option 4 — Just open it locally

Download `index.html` and open it in a browser, or serve the folder:

```sh
python3 -m http.server 8000
# then open http://localhost:8000
```

Works on phone and desktop. On a phone, use the browser's
"Add to Home Screen" to keep it one tap away.

## Your data

- Data lives in `localStorage` under the key `wt-shareable-v1`, plus
  `wt-shareable-draft` for a workout in progress (so a refresh
  mid-workout loses nothing).
- It never leaves the device. Clearing browser data deletes it —
  export a backup from Train → Your data first.
- Data does not sync between devices; use Export/Import backup to
  move it.
- Hosting Mooscles on Muse, Vercel, GitHub Pages or locally does not
  change this — the host only serves the file, it never receives
  anyone's workouts.

## Tech

Plain HTML, CSS and vanilla JavaScript in one file — no framework,
no dependencies, no build step, nothing to install. Fonts load from
Google Fonts; everything else, including the exercise thumbnails
(small inline SVG drawings), is in the file itself.
