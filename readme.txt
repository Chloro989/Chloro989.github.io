# This repository is for my website.

## Commands

## Local preview
python -m http.server 8000 -d docs
# then open http://localhost:8000

## Known gaps (carried over from the old Django site)
- /play/ (great number game) and /leaderboard.html are dead (POST to /result has no backend).
  Decided not to rebuild these. Still on disk but no longer linked from the homepage.
- Gallery (photo upload/browse) isn't in this repo at all yet. The old Django app stored photos
  in a DB; a static-friendly version needs image hosting + a JSON manifest, or a small
  serverless upload endpoint.

## Fixed
- /studies/jkmath had no file extension, so servers sent it as application/octet-stream and
  browsers downloaded it instead of rendering it. Renamed to jkmath.html.

## Landing page redesign
index.html is now a single full-bleed mountain photo hero (docs/static/images/snowpeak-*.jpg,
Unsplash) with just four links: Math Problems (/studies/jkmath.html), YouTube, Instagram,
GitHub. Dropped the old header/nav, the "run your own race" text, and the game/gallery/timer/
studies/image-generation links that used to fill out the page. Those pages (/play/, /timer/,
/studies/) still exist, just aren't linked from the homepage anymore.
