# recruitchat

Dummy factory skin for **recruitchat.com**. Tagline: *The room, not the funnel.*

Static SubX dress rehearsal. Recruiting / job-seeker community. **Not** a résumé mill, **not** an ATS, **not** charging for polish. Not X.com.

No Firebase. No Auth provider. No AI / Ollama. No résumé upload. No LinkedIn import. Guest browse and local-only posts (`localStorage`). HTTPS off until GitHub issues the cert.

## Pages

Drop these files on `main` at `/` (root). Custom domain `recruitchat.com` (`CNAME` already contains exactly that). Leave HTTPS off until the GitHub cert is issued. Preview banner and `robots.txt` noindex stay on.

## What this is

- Feed-first **sample** posts: interview loops, recruiter spam, offer timing. Fake handles.
- Right rail is **curated outbound only** (DOL, BLS, USAJOBS, Indeed, CareerOneStop). No ingest.
- Sign-in modal is a local stub. Google is off until HTTPS + that provider is enabled.
- Guest handle: `guestrecruit`.
- One factory shell. Nested rooms are `/{slug}` on the same host — not a second app.

## Nest rooms (schema v0)

`site.json` includes recruitchat’s nest tree (interview loops, recruiter spam, role rooms, …). **Do not** copy samochat dummy nests (`pier` / `promenade` / `montana`).

URL grammar: apex `/` is the home room. `/{slug}` is the same shell, filtered by optional post field `nestSlug`. Hash routes (`#home`, `#explore`, …) still work. v0 is one path segment; reserved names (`explore`, `news`, `factory.js`, …) are not nests.

Quiet nests stay URL-addressable. Left nav / Explore only list nests with activity or `nav: true`. Set `nav: false` to hide even then.

**Static hosting:** nest deep links need an SPA fallback (Cloudflare Pages `_redirects`: `/* /index.html 200`) or the `404.html` bounce. Keep asset hrefs relative (`factory.js`, `site.json`) so `/loops` (no trailing slash) still loads `/factory.js`.

## Firestore index (manual publish)

`firebase.indexes.json` includes the posts composite `siteId ASC, nestSlug ASC, createdAt DESC`. Publish that index by hand in **subx-skins**. v0 does not require it (client filter). Do not `firebase deploy` from an agent.

## Product locks

- Tagline stays *The room, not the funnel.*
- No AI résumé upload. No listing scrape/ingest.
- Preview banner and `robots.txt` noindex stay until Jebb lifts them. No GTM lift.
