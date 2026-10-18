# intervole_timer
Partner preference test scoring script

## Web app

**Use it in your browser: https://beerylab.github.io/intervole_timer/**

The web version provides the same functionality as the original Perl script:
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

The whole app is the single file `index.html`. To run it locally, open that
file in a browser, or run `node server.js` and visit http://localhost:3001.

## Original Perl script

`IntervoleTimer1.6.pl` is the original command-line scoring script, with its
instructions (`IntervoleTimer1.6 Instructions.pdf` / `.rtf`) and sample output
(`IntervoleTimer1.6-TIDSampleOutput.txt`).
