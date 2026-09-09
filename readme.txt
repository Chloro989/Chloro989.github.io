# This repository is for my website.

## Commands

## Local preview
python -m http.server 8000 -d docs
# then open http://localhost:8000

## Known gaps (carried over from the old Django site, not yet rebuilt)
- /play/ (great number game) posts to /result, which doesn't exist on static hosting. Needs a
  small serverless function (or client-side rewrite) to check guesses and track attempts.
- /leaderboard.html has no data source. Needs the same serverless backend as the game, or a
  swap to client-side-only high scores.
- Gallery (photo upload/browse) isn't in this repo at all yet. The old Django app stored photos
  in a DB; a static-friendly version needs image hosting + a JSON manifest, or a small
  serverless upload endpoint.
