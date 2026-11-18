# Ludra Raid Training — progress

Browser practice tool for the "Zikel" mechanic of Ludra (AION 2, Sanctuary raid). Single file: `ludra-raid-training.html`
(Three.js from CDN, no build step). Original abstract visuals only — no game assets.

Mechanic reference for other builders: `ludra-zikel-mechanic.md` (keep it in sync when numbers change).

Run: double-click `ludra-raid-training.html` (how the user runs it; no server needed). A local server now shows a
directory listing at `/` because the file is no longer `index.html`; rename or add a redirect when hosting.

## Done
- 3D third-person view, mouse-look camera (pointer lock, drag fallback, arrow keys), camera-relative WASD.
- Normal / Hard toggle, speed 50/75/100%, callouts toggle, keep-going-after-mistake, mouse sensitivity.
- Rules live in the `CFG` block at the top of the script; game logic is 2D, the scene only draws it.
- `window.zikel` exposes `newRun/update/STEP/S/render` for scripted tests from the console.

## Mechanic as confirmed by the user (boss = north)
- Orange line telegraph fills; standing on it when it strikes kills. After the strike, step onto it; everything
  off the line then detonates (kill).
- Fixed order: 1) E–W, lasers from south  2) SW–NE, lasers from west  3) N–S, lasers from east
  4) NW–SE, lasers from north. Lasers kill.
- Hard only: orange circle under the player; be outside it or dodging when it fills.
- "Zikel" is the players' name for the mechanic; the boss is Ludra.

## Estimated from one video (youtu.be/vOb-LqzxLsE, 13:13), not confirmed
- Line timings, measured frame by frame on lines 2 and 4 (30 fps, so ±0.03 s), from the orange line appearing:
  orange gone at 0.65 s, lightning strip at 1.00 s, detonation at 2.55 s, next orange at 4.00 s. Second video
  (youtu.be/RNZA_QjX3NE ~7:40, 60 fps) agrees: orange 0.67 s, lines exactly 4.0 s apart.
  User confirmed (2026-11-17): the line kills when the orange finishes, if you are inside it.
- Lasers, from the user's frame counts (RNZA_QjX3NE 4:30-4:40, 60 fps): visible on its wall ~100 frames before it
  moves, starts sweeping ~20 frames after the hard circle resolves (~strike +2.9 s), crosses in ~150 frames (2.5 s);
  far-wall arrival frame-checked at 4:39.92. Wrong earlier versions: 0.7 s crossing; "stands 1 s, moves at next strike".
  User played it and confirmed the sweep feels right (2026-11-17).
- Sizes: 40 m arena, 4 m line width, 3 m circle, beams 5 m apart with one crossing dead centre.
- Hard-mode circle, measured on 3 circles in the 60 fps video: appears 0.71 / 0.98 / 1.33 s after the strike
  (not fixed), stays where it dropped, resolves 1.82-1.88 s later (0.6-1.3 s after the detonation). Trainer uses
  a random 0.7-1.35 s delay and a 1.85 s fill. Watch out: the floor's round platforms have orange rims too. Dodge only saves from the circle.
- Dodge is on Shift and costs stamina (user: about 5 dodges per full bar). Refill rate 10/s is a guess.
- Move speed 6 m/s (user asked for slower than 7).

## Bingo board (early version, 2026-11-17)
- Second card on the start screen; same arena, player, camera and dodge. Rules in `bingoStep()`, values in `CFG.bingo`.
- Reference and open questions: `ludra-bingo-mechanic.md`. Measured: circle at +2.0 s, follows 1.5 s, resolves
  2.17 s after appearing, next one 2.0 s later, 4 in a row. Confirmed 6x6. Estimates: 4 m squares, radius 1.8 m.
- Team version: player picks corner (1 SW, 2 NW, 3 NE, 4 SE) and melee/ranged; 9 bots run the clockwise pair sweep
  from the user's diagram (`CFG.bingo.paths` / `center`). Random safe square -> cyan glass box when a circle lands
  on it. Any player's circle can kill you. Tested: following the plan clears 80/80 (all corners/roles).
- Phase 1 board (boss ~50%; a second board comes later in the fight). Safe square = immunity; everyone runs in once
  found; "Ludra's Trial" (16 s cast from ~4.0 s, ends ~20 s, confirmed) kills anyone outside. Two orbs, opposite
  sides, random N+S or W+E: shown only. Full plan clears 284/288 (all corners/roles x all safe squares); the 4 misses
  are last-circle finds out of reach, which the user confirmed happens in the game.
- Roles are Outside / Inside (was melee/ranged) or Centre (= Centre A). Jump on Space (CFG.jump). Orbs: red
  marker, orb appears high and floats down (CFG.bingo.orb); grab by touching it (jump helps), lose it if it lands.
  Centre player clears 131/144 in tests (5 unreachable, 8 ran into others' circles at the safe square).
- Small green ground arrow next to the player points at the next square / orb / safe square (callouts on).
- **TODO (next session, 2026-11-19):** the centre players grabbing the orbs must leave their **third circle outside
  the orb area**. Right now the centre bots stand at the orb spot while waiting, so their 3rd circle snaps and
  resolves on top of them (and on the orb spot). Fix: before the 3rd circle snaps (~11.84 s), the centre player
  stands a few metres away from the orb marker, lets the circle snap there, steps out, then goes back under the orb
  to jump. Apply to the centre bots' path in `bingoStep()`, and make the green target/arrow guide the player the
  same way when playing Centre. Ask the user where exactly players drop it if unsure.
- Next after that: confirm orb marker/height/landing times; phase 2 board.
- The user's frame counts here were 1/30 s steps (first converted at 60 fps by mistake = everything 2x too fast).
  Always check a frame count against two timestamps before converting.
- Filled squares are visual only until the user confirms what they do.

## Next
- User playtest for timing/size feel; tune `CFG`.
- Ideas not started: sound cues, party bots, other Ludra mechanics, hosting (GitHub Pages).
