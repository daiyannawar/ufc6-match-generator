# UFC 6 Match Generator

A random fight picker for EA Sports UFC 6. Choose a roster, a weight class and a star range, and it books a red corner vs blue corner matchup between two fighters from the same division.

**Test it out!** https://daiyannawar.github.io/ufc6-match-generator/

![Main page](docs/home.png)
![Matchup screen](docs/matchup.png)

## Features

- **Men's or WMMA** rosters, with every division from strawweight (115) to heavyweight (265)
- **Weight class** filter, or "Any division" to pick one at random
- **Star rating range** with MIN and MAX pickers, in half-star steps
- **Matchup screen** with each fighter's country flag, 3-letter country code, an animated 8-bit fighter, the division and their star rating
- Never repeats the same matchup twice in a row
- Keyboard shortcuts: `Enter` generates a fight, `R` regenerates, `Esc` goes back
- Remembers your last filters in the browser
- Works on phones; the matchup screen stacks top and bottom on narrow screens

## Run it locally

It's one HTML file with no build step and no dependencies. Either open `index.html` in a browser, or serve the folder:

```sh
python3 -m http.server 8000
# then open http://localhost:8000
```

An internet connection is only needed for the Google Fonts (Outfit and Saira). Without it, the page falls back to system fonts.

## Editing the roster

Fighters live in the `ROSTER_TEXT` block near the top of the `<script>` in `index.html`. There's one fighter per line:

```
gender | division | name | country | stars | skin | hair | hair colour | beard
M|LW|Charles Oliveira|BRA|4.5|2|s|k|0
```

| Field | Values |
| --- | --- |
| gender | `M` men, `W` women |
| division | Men: `FLY` `BW` `FW` `LW` `WW` `MW` `LHW` `HW`. Women: `SW` `FLY` `BW` `FW` |
| country | 3-letter code with a flag in `FLAGS` (e.g. `USA`, `BRA`, `RUS`, `ENG`) |
| stars | `0.5` to `5` in half steps |
| skin | `0` (lightest) to `4` (darkest) |
| hair | `b` bald, `s` short, `c` curly, `l` long, `p` ponytail |
| hair colour | `k` black, `n` brown, `y` blond, `r` red, `g` grey |
| beard | `1` or `0` |

The star ratings are estimates, so adjust them to match the game. To add a new country, add an entry to `FLAGS`: a name, a glow colour and a small SVG drawn in a 90×60 box.

## Notes

The flags and fighter sprites are drawn in code, so the page loads no images.

Fan-made project. Not affiliated with or endorsed by EA Sports or the UFC.

## License

[MIT](LICENSE)
