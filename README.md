# icubasics.com

Static site: `index.html`, `privacy.html`, `support.html`, `styles.css`, `assets/`. No build step.

Question counts in `index.html` are filled from the app's banks by `scripts/site-counts.sh`
(run it after adding questions, then commit).

## Publishing

Live at https://icubasics.com via GitHub Pages from the public repo `alexgateley/icubasics-site`
(branch `main`, root). This folder is the source of truth; the repo is a copy.

To publish a change: edit here, then run `scripts/site-publish.sh` (rsyncs into the sibling
`icubasics-site` checkout, commits, pushes). Pages rebuilds in about a minute.

DNS (GoDaddy): `A` records for `@` → `185.199.108.153`, `185.199.109.153`, `185.199.110.153`,
`185.199.111.153`; `CNAME www` → `alexgateley.github.io`. GoDaddy's NS and SOA records stay.

## Related settings
- `PRIVACY_POLICY_URL` in the app's `src/config.ts` → `https://icubasics.com/privacy.html`.
- App Store Connect → App Information: Privacy Policy URL and Support URL → the same domain.
