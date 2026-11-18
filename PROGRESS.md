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

## Next
- User playtest for timing/size feel; tune `CFG`.
- Ideas not started: sound cues, party bots, other Ludra mechanics, hosting (GitHub Pages).
