# This repository is for my website.

## Commands

## Local preview
python -m http.server 8000 -d docs
# then open http://localhost:8000

## Known gaps (carried over from the old Django site)
- /play/ (great number game) and /leaderboard.html are dead (POST to /result has no backend).
  Decided not to rebuild these.
- Gallery (photo upload/browse) isn't in this repo at all yet. The old Django app stored photos
  in a DB; a static-friendly version needs image hosting + a JSON manifest, or a small
  serverless upload endpoint. Next up, after the math problem set.

## Fixed
- /studies/jkmath had no file extension, so servers sent it as application/octet-stream and
  browsers downloaded it instead of rendering it. Renamed to jkmath.html.
