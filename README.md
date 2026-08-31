# ericcedwards.com — static site

A static rebuild of the content from ericcedwards.com (previously a Wix site) as plain HTML/CSS, ready to host for free on GitHub Pages.

## Contents

- `index.html` — home / bio / contact
- `publications.html` — journal articles and book chapters, by year
- `working-papers.html` — working papers and papers under review
- `outreach.html` — outreach publications
- `consulting.html` — consulting page
- `style.css` — shared stylesheet
- The **Vitae** nav link points directly at the CV PDF (matches the original site's behavior).

Content was transcribed from the live site on 2026-08-31. Check it against the current site before publishing, since it may have changed since.

## Known limitation: hotlinked images/PDF

This sandbox's network access does not reach `ericcedwards.com` or `static.wixstatic.com`, so the headshot photo and the CV PDF are currently **linked directly to the original Wix-hosted URLs** rather than copied into this repo. That means:

- The site works today, but if the Wix site is ever taken down, those two assets will break.
- To self-host them instead, download the two files and swap the URLs:

```bash
curl -o assets/headshot.png "https://static.wixstatic.com/media/1110dc_e670e7ae389045cb87a3cca3a7f8e212~mv2.png/v1/crop/x_56,y_0,w_1663,h_2495/fill/w_316,h_474,al_c,q_85,usm_0.66_1.00_0.01,enc_avif,quality_auto/headshot_2023_edited.png"
curl -o assets/cv.pdf "https://www.ericcedwards.com/_files/ugd/1110dc_272754c1f0764ae5ba2ef3a335615f69.pdf"
```

Then update the `src="..."` in the `<img>` tag (all five HTML files) to `assets/headshot.png`, and the Vitae `<a href="...">` (all five HTML files) to `assets/cv.pdf`.

## Publish to GitHub

```bash
# from inside this folder
git remote add origin https://github.com/<your-username>/<repo-name>.git
git branch -M main
git push -u origin main
```

## Turn on GitHub Pages

1. On GitHub, go to the repo's **Settings → Pages**.
2. Under "Build and deployment", set **Source** to "Deploy from a branch".
3. Set **Branch** to `main` and folder to `/ (root)`, then **Save**.
4. The site will be live within a minute or two at `https://<your-username>.github.io/<repo-name>/`.

To use the custom domain `ericcedwards.com`:
1. Add a file named `CNAME` at the repo root containing just `ericcedwards.com`.
2. In **Settings → Pages**, enter the custom domain and save.
3. At your DNS provider, point the domain at GitHub Pages (an `A`/`ALIAS` record to GitHub's IPs, or a `CNAME` record to `<your-username>.github.io` for a subdomain) — see GitHub's docs on "Managing a custom domain for your GitHub Pages site".
