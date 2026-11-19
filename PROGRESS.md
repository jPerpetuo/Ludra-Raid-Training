# Development notes

Single-file browser trainer for Ludra (AION 2, Sanctuary raid): `ludra-raid-training.html`. Three.js from a CDN, no build
step. Original abstract visuals only, no game assets.

Run it by double-clicking the file, or serve the folder with any static server. GitHub Pages serves `main` at
https://jperpetuo.github.io/Ludra-Raid-Training/

Mechanic references (keep them in sync when numbers change): `ludra-zikel-mechanic.md`, `ludra-bingo-mechanic.md`,
`ludra-colors-mechanic.md`.

## How the code is organised

- `CFG` (top of the module script): every timing, size and rule. Sub-blocks per mechanic: `CFG.bingo`, `CFG.colors`
  (`area`, `tp`, `spacing`, `spawn`, `maxTicks`, `tickEvery`, `radius`).
- `newRun(mech)` builds the state; `update(dt)` runs the rules (2D, fixed step `STEP`); `sync()` draws the 3D scene;
  `hud()` writes the text. Each mechanic has its own `*Step` (`bingoStep`, `colorsStep`) and `sync*` helpers.
- `window.zikel` exposes `CFG`, `opts`, `newRun`, `update`, `sync`, `hud`, `render`, `S`, `cam` and `ludra` for scripted
  tests from the console.
- Text: `T('English text')` returns the Portuguese text when the language is `pt`; `PT_JS` and `PT_HTML` hold the
  translations. The page text is swapped by `applyHtmlLang()`.

## Status

- **Zikel:** done (normal and hard).
- **Bingo board:** phase 1 done. Phase 2 not started.
- **Colors:** done, with three stages (Ludra in the north, then two flights to the west, south or east, never the
  opposite corner). Fixed or adaptive sides. Five blue and five red auras, hits every 0.5 s within 5.5 m, five hits to
  go down. Melee stay near Ludra; ranged spread out with spacing. Stage 1 always uses the fixed sides.
- **Language:** English and Português, with flag buttons in the top-right corner. Default is Portuguese.
- **Demo GIFs:** `docs/demo/*.gif` are captured from the simulator (headless Chrome driving the page, frames assembled
  with ffmpeg). The capture script is not in the repository.

## Open items

- Real timings for the Colors orbs, auras and flights (placeholders for now: 12 s, 1.5 s gap, 8 s, 0.9 s flight).
- Sides after a flight in adaptive mode: "least walking" is a guess.
- Bingo phase 2.
- Teammate names: the nine names in `GUILD` (Kalard's friends), drawn at random every run. The player shows as "you" / "você".

## Known limits

- At the 5.5 m radius, bots take a few hits per run while the sides change after a flight. In 80 test runs, two bots went down.
- The GIF demos are captured with a fixed camera and a scripted player, so they show the mechanic, not a real run.
