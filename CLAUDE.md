# Intervole Timer — notes for coding agents

## What this is
A behavioral scoring tool for vole partner preference tests. A scientist scores the
focal vole's location (5 zones in a three-chamber arena) while watching video of the
test. Version 1.6 (`v1_perl/`) is the original Perl command-line script; Version 2.0
(`v2_web/`) is the web app, published with GitHub Pages at
https://beerylab.github.io/intervole_timer/.

This repository is public. Don't commit hostnames, internal paths, credentials or
task-tracking files.

## Layout
- `v1_perl/`: the original script, its instructions and a sample output file. This
  is the reference for behavior and output format; don't change it.
- `v2_web/index.html`: the whole web app (HTML + CSS + JS, no framework, no build step).
- `v2_web/server.js`: a minimal Node static server for local use only (port 3001).
  The live site is static: `.github/workflows/pages.yml` deploys `v2_web/` on
  pushes to `main` that touch it, so the app must keep working as plain static files.

## Behavioral logic
States 0–4:
- 0: Left Huddling
- 1: Left Not Huddling
- 2: Center Chamber (solo)
- 3: Right Not Huddling
- 4: Right Huddling

Bout counting (from the Perl script):
- States 0 and 4 (huddling): a bout counts only if the animal stayed in that state
  for **more than 3 seconds**.
- State 2 (center): every entry counts as an iteration, regardless of duration.
- States 1 and 3: no bout counting.

Activity = total center entries − 1 (the initial entry at start doesn't count).

Scaling: the summary scales all durations by `testDuration / totalScoredMinutes`
to normalize to a full test (default 180 min).

## Controls
- `Space`: start / end session
- `,`: move one state to the left
- `.`: move one state to the right
- `P`: pause / unpause (records the current state entry, resets the timer on unpause)
- Swipe left/right on touch devices: move state

## Output format
The text output must match the Perl script's `.txt` output exactly (see
`v1_perl/IntervoleTimer1.6-TIDSampleOutput.txt`):
- Header with test ID, date, vole IDs, video source
- RAW DATA section (one row per state change)
- SUMMARY DATA with actual scored totals and scaled totals

## Running locally
```bash
node v2_web/server.js   # http://localhost:3001
```
or open `v2_web/index.html` directly in a browser.

## Testing
Test end to end in a browser (e.g. with Playwright): title → setup → scoring → pause →
end → summary → results, and compare the downloaded `.txt` against the Perl format.
