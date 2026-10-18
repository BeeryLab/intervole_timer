# intervole_timer
Partner preference test scoring script

## Web app

**Use it in your browser: https://beerylab.github.io/intervole_timer/**

Version 2.0 is a web app with the same functionality as the original Perl script:
score the focal vole's location across the five arena zones while watching the
test video, then copy or download the results as a `.txt` file in the same
format the Perl script produces. Everything runs locally in the browser; no
data is uploaded anywhere.

Keyboard controls:

| Key | Action |
| --- | --- |
| `Space` | Start / end the scoring session |
| `,` | Move one zone to the left |
| `.` | Move one zone to the right |
| `P` | Pause / unpause |

On touch devices, swipe left or right to change zones.

## Repository layout

- `v2_web/`: Version 2.0, the web app. The whole app is the single file
  `index.html`. To run it locally, open that file in a browser, or run
  `node v2_web/server.js` and visit http://localhost:3001. Pushes to `main` that
  touch `v2_web/` redeploy the live site.
- `v1_perl/`: Version 1.6, the original command-line Perl script
  (`IntervoleTimer1.6.pl`), with its instructions
  (`IntervoleTimer1.6 Instructions.pdf` / `.rtf`) and sample output
  (`IntervoleTimer1.6-TIDSampleOutput.txt`).
