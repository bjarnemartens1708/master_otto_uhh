# OTTO Prototype — GitHub Pages hosting

A single self-contained prototype (`index.html`). No build step, no dependencies — everything (images, icons, styles) is embedded. Read-only; opens on any phone or desktop browser.

## Deploy (fastest — web UI, no git)

1. Create a new repository on GitHub (e.g. `otto-prototype`). It can be public or private; **Pages requires a public repo on the free plan**.
2. On the repo page: **Add file → Upload files**.
3. Drag in **both** `index.html` and `.nojekyll` from this folder, then **Commit changes**.
   - `.nojekyll` matters: it stops GitHub's Jekyll from mangling the file.
4. Go to **Settings → Pages**.
5. Under **Build and deployment → Source**, choose **Deploy from a branch**.
6. Branch: **main**, folder: **/ (root)** → **Save**.
7. Wait ~1 minute. The public URL appears at the top of the Pages settings:
   `https://<your-username>.github.io/otto-prototype/`

That URL is permanent and phone-friendly — send it to interviewees.

## Deploy (git CLI alternative)

```bash
git init
git add index.html .nojekyll
git commit -m "OTTO prototype"
git branch -M main
git remote add origin https://github.com/<you>/otto-prototype.git
git push -u origin main
```

Then do steps 4–7 above.

## Updating later

Re-upload a new `index.html` (Add file → Upload files → commit). Pages redeploys in ~1 minute. Tell me when you change the prototype and I'll regenerate `index.html` for you.

## Notes

- Add to Home Screen (Safari share sheet) launches it fullscreen, like a native app.
- Works fully offline once loaded.
- To keep the repo private, use a paid GitHub plan, or use Netlify Drop (drag the folder onto app.netlify.com/drop) for a free private-ish host with no repo.
