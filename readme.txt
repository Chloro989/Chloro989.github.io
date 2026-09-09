# This repository is for my website.

## Commands

## Local preview
python -m http.server 8000 -d docs
# then open http://localhost:8000

## Known gaps (carried over from the old Django site)
- /play/ (great number game) is dead — its submit posts to /result, which has no backend.
  Decided not to rebuild. Still on disk but no longer linked from the homepage. Removed its
  Leaderboard button since that page doesn't exist anymore either.
- Gallery (photo upload/browse) isn't in this repo at all yet. The old Django app stored photos
  in a DB; a static-friendly version needs image hosting + a JSON manifest, or a small
  serverless upload endpoint.
- OGP/Twitter-card meta tags across several pages point at chloro966.net, but there's no CNAME
  file in docs/ — the site is only actually reachable at https://chloro989.github.io/ right
  now. Left alone since touching the custom domain wasn't asked for.

## Fixed
- 2026-09-10: the repo was named `chloro.github.io`, which does NOT match the owner
  `Chloro989` — GitHub Pages only serves at the bare `<owner>.github.io` root when the repo
  name matches exactly, so the site was actually deployed one path segment deeper
  (`.../chloro.github.io/`) than every absolute path in this site assumed. Every page was
  broken on the real deployment (no CSS, no images, every internal link 404ing) while testing
  fine locally. Renamed the repo to `Chloro989.github.io` to fix it — site is now correctly
  at https://chloro989.github.io/. If this ever gets renamed again, re-check this.
- /studies/jkmath had no file extension, so servers sent it as application/octet-stream and
  browsers downloaded it instead of rendering it. Renamed to jkmath.html.
- 2026-09-10: most of the site still had unrendered Django template tags (`{% ... %}`) left
  over from the static export — visitors would see literal `{% url 'top' %}` etc. Deleted the
  five orphaned root-level duplicates that already had a working folder version
  (apex_data.html, play.html, timer.html, juken_sugaku.html, study_top.html) and
  leaderboard.html (unbuildable without the DB-backed game we're not rebuilding). Fixed
  403.html, 404.html (the one GitHub Pages actually serves for bad URLs — was broken on the
  live site), and license.html in place, since those have no working duplicate elsewhere.
  Also fixed apex_data/index.html's `<title>` tag, which had the favicon `<link>` nested
  inside it as text (garbled the browser tab title and silently dropped the favicon).

## Landing page redesign
index.html is now a single full-bleed mountain photo hero (docs/static/images/snowpeak-*.jpg,
Unsplash) with just four links: Math Problems (/studies/jkmath.html), YouTube, Instagram,
GitHub. Dropped the old header/nav, the "run your own race" text, and the game/gallery/timer/
studies/image-generation links that used to fill out the page. Those pages (/play/, /timer/,
/studies/) still exist, just aren't linked from the homepage anymore.
