# Rally — put it on GitHub Pages

Everything here goes at the **top level** of the repo. About three minutes.

## 1. Make the repo

Go to **github.com/new**

- Repository name: `rally`
- **Public** — free GitHub Pages only works on public repos
- Leave "Add a README" unchecked

Click **Create repository**.

> Public means the *app code* is visible. Your match data isn't in here — it
> lives only on your phone and never gets uploaded.

## 2. Upload the files

On the empty repo page, click **uploading an existing file**.

Unzip this bundle — you'll get a folder called `rally-files`. Open it, select
**the files inside** — not the folder itself — and drag them into the upload
box:

```
index.html
sw.js
manifest.webmanifest
icon-192.png
icon-512.png
apple-touch-icon.png
.nojekyll        (optional, and Finder may hide it — fine either way)
```

If you drag the folder by mistake the app still works, you just get a longer
URL. Click **Commit changes**.

## 3. Turn on Pages

In the repo: **Settings** → **Pages** (left sidebar)

- Source: **Deploy from a branch**
- Branch: **main**, folder: **/ (root)**
- **Save**

Give it about a minute. Refresh the Pages settings screen and your address
appears at the top:

```
https://YOUR-USERNAME.github.io/rally/
```

The trailing slash matters. Open it in a browser to confirm you get the setup
screen with the orange R icon.

## 4. Install it on your phone

**iPhone / iPad — has to be Safari**

1. Open the URL in Safari
2. Share (square with the arrow)
3. Scroll down → **Add to Home Screen**
4. Name it, Add

**Android — Chrome**

1. Open the URL in Chrome
2. Menu (⋮) → **Install app**
3. Install

## 5. The gym test — do this before match day

Open it once from the home-screen icon while you have signal, so the offline
cache fills. Then turn on airplane mode and open it again. It should start
normally with the court showing. If it does, a dead gym wifi can't touch you.

## Sending an update

If you get a new `index.html`:

1. In the repo, click `index.html` → pencil icon → paste the new contents, or
   use **Add file → Upload files** and drop the new one over the top
2. Open `sw.js`, change `var CACHE = "rally-v1"` to `"rally-v2"`
3. Commit

Phones pick up the change next time they open the app with a signal. Bumping
the cache name is what forces it — skip that and they'll keep the old copy.

## If you'd rather use git

```bash
cd rally-files
git init -b main
git add .
git commit -m "Rally volleyball tracker"
git remote add origin https://github.com/YOUR-USERNAME/rally.git
git push -u origin main
```

Then do step 3 above to switch Pages on.

## Troubleshooting

**404 at the URL** — Pages takes a minute on first publish. Also check the
files are at the repo root, not inside a folder, and that Pages is set to
`main` / `/ (root)`.

**Loads but no Add to Home Screen option on iPhone** — you're in Chrome or
another browser. iOS only offers it in Safari.

**Works online but not in airplane mode** — you skipped step 5 while you had
signal, so the cache never filled. Open it once connected, then retest.

**Changed a file but the phone shows the old version** — bump the `CACHE`
name in `sw.js`. That's the whole point of that line.
