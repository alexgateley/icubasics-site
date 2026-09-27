# icubasics.com

Static site: `index.html`, `privacy.html`, `support.html`, `styles.css`, `assets/`. No build step.

Question counts in `index.html` are filled from the app's banks by `scripts/site-counts.sh`
(run it after adding questions, then commit).

## Publishing (pick one)

### A. GitHub Pages (free, recommended)
1. `gh auth login`, then from this folder: `gh repo create icubasics-site --public --source=. --push`
   (or push the `website/` folder to a repo of your choosing).
2. Repo → Settings → Pages → Source: "Deploy from a branch", branch `main`, folder `/ (root)`.
3. Settings → Pages → Custom domain: `icubasics.com` (the `CNAME` file here already says so). Tick "Enforce HTTPS" once the certificate is issued (up to an hour).
4. GoDaddy → My Products → DNS for icubasics.com. Delete GoDaddy's parking/forwarding records, then add:
   - `A` records for `@` → `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - `CNAME` for `www` → `alexgateley.github.io`
   DNS takes minutes to a few hours to propagate.

### B. Netlify Drop (no command line)
1. Go to https://app.netlify.com/drop and drag this folder onto the page.
2. Site settings → Domain management → Add custom domain `icubasics.com`.
3. GoDaddy DNS: `A` for `@` → `75.2.60.5`, `CNAME` for `www` → the `*.netlify.app` name Netlify shows.

### C. GoDaddy web hosting
Only if you bought a hosting plan (not Website Builder): upload these files to `public_html` with the File Manager.
Website Builder cannot host custom HTML; use A or B instead.

## After it's live
- Set `PRIVACY_POLICY_URL` in the app's `src/config.ts` to `https://icubasics.com/privacy.html`.
- In App Store Connect → App Information, set Privacy Policy URL and Support URL to the same domain.
