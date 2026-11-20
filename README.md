# Danny Pye: personal website

A one-page site built with HTML and Tailwind CSS. It has no JavaScript.
GitHub builds and publishes it automatically, so nothing needs to be installed on your PC.

## What's in this folder

| Path | What it is | Edit it? |
|---|---|---|
| `index.html` | The page: text, links, layout | Yes, for content changes |
| `src/input.css` | Tailwind settings: colours and fonts (`@theme` block) | Yes, for colour or font changes |
| `assets/portrait.jpg`, `assets/portrait.webp` | Headshot, 640 × 800 px | Replace both to change the photo |
| `assets/cv.pdf` | Your CV, linked from the Download CV button | Replace to update |
| `assets/favicon.svg` | Browser-tab icon | Optional |
| `assets/site.css` | Compiled CSS. GitHub rebuilds it on every commit | No |
| `.github/workflows/deploy.yml` | Instructions for GitHub to build and publish the site | No |

---

## Put it online (first time, about 10 minutes, all in the browser)

**1. Create the repository**
- Sign in at github.com (a free account is fine).
- Click **+** (top right) → **New repository**.
- **Repository name:** `YOUR-USERNAME.github.io`, using your exact GitHub username. Your site will then be at `https://YOUR-USERNAME.github.io`.
- Set it to **Public**. Free accounts only get Pages on public repositories.
- Leave "Add a README" unticked → **Create repository**.

**2. Upload the files**
- On the new, empty repository page, click the **uploading an existing file** link.
- In File Explorer, open the unzipped folder. Select `index.html`, `README.md`, and the `assets` and `src` folders, then drag them into the browser window.
- Click **Commit changes**.
- The `.github` folder is added in step 4. Browser uploads don't reliably include folders whose names start with a dot.

**3. Turn on GitHub Pages**
- In the repository, go to **Settings** → **Pages** (left menu).
- Under **Build and deployment** → **Source**, choose **GitHub Actions**.

**4. Add the build workflow**
- Go to the **Code** tab → **Add file** → **Create new file**.
- In the name box, type exactly: `.github/workflows/deploy.yml`. Each `/` creates a folder.
- Open `deploy.yml` from the unzipped folder in Notepad, then press `Ctrl+A`, `Ctrl+C`. Paste it into the GitHub editor with `Ctrl+V`.
- Click **Commit changes**. This starts the first build.

**5. Check it worked**
- Open the **Actions** tab. Wait for a green tick next to "Build and deploy site", which takes about a minute.
- Visit `https://YOUR-USERNAME.github.io`.

---

## Making changes

Every commit to `main` rebuilds and republishes the site within about a minute.

- **Small edits:** open a file on GitHub → pencil icon (✎) → edit → **Commit changes**.
- **Full editor in the browser:** on the repository's main page, press the **.** (full stop) key. VS Code opens in your browser. Edit, then open the **Source Control** icon in the left bar, type a short message, and click **Commit & Push**.
- **Preview on your PC:** double-click `index.html` in File Explorer. A Tailwind class you've just added only takes effect after GitHub rebuilds the site, so check new styling on the live site.

## Common tasks

| Task | How |
|---|---|
| **Update your CV** | Open the `assets` folder on GitHub → **Add file** → **Upload files** → upload the new version named exactly `cv.pdf`. It replaces the old one. Visitors download it as `Danny-Pye-CV.pdf`. |
| **Change the summary** | Edit the paragraph under `<h1>` in `index.html`. |
| **Add a profile link** | In `index.html`, copy one `<a href=...>...</a>` line in the Contact section and change the address and label. |
| **Change colours or fonts** | Edit the `@theme` block in `src/input.css`. For a new font, also change the Google Fonts `<link>` in `index.html`. |
| **Replace the photo** | Upload new `portrait.jpg` and `portrait.webp` files, both 640 × 800 px, with the same names. They overwrite the old ones. |

## How Tailwind works here

- Styling is written as small classes directly in the HTML. For example, `text-lg` is a larger font, `mt-6` adds space above, and `rounded-2xl` gives rounded corners.
- On each commit, GitHub runs Tailwind. It scans `index.html` and writes only the CSS you use into `assets/site.css`.
- Class reference: https://tailwindcss.com/docs. Use the search box, for example "margin" or "font size".

## If something goes wrong

| Symptom | Fix |
|---|---|
| Red ✗ on the Actions tab | Click the run → the failed step → read the error. The usual cause is that step 3 wasn't done. Set Source to **GitHub Actions**, then go to **Actions** → **Build and deploy site** → **Run workflow**. |
| 404 at your address | Wait 2–3 minutes after the first green tick. Check that the repository name exactly matches `YOUR-USERNAME.github.io`. |
| Page shows but looks unstyled | Check that `assets/site.css` exists in the repository, and that the latest Actions run has a green tick. |
