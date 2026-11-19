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
- Sizes: 40 m arena, 4 m line width, 3 m circle, beams 5 m apart with one crossing dead center.
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
- Roles are Outside / Inside (was melee/ranged) or Center (= Center A). Jump on Space (CFG.jump). Orbs: red
  marker, orb appears high and floats down (CFG.bingo.orb); grab by touching it (jump helps), lose it if it lands.
  Center player clears 131/144 in tests (5 unreachable, 8 ran into others' circles at the safe square).
- Small green ground arrow next to the player points at the next square / orb / safe square (callouts on).
- Done 2026-11-19: center players wait 4 m beside the orb (`orb.wait`, off the board) so their 3rd circle drops
  there, step out, then go under the orb (`orbTarget()`); the 4th circle also drops beside it if the safe square
  isn't found yet. All NPCs wait just outside their own red circle until it resolves (0 NPCs caught in their own
  circle across all test runs). The player's outline/arrow/callouts guide Center the same way.
- NPC names: `mtkです` (the user, always present) plus 8 random names from `GUILD` (the user's guildmates), shown
  as name tags and used in messages.
- Tests: corner roles 284/288, center 138/144; every miss is an unreachable last-circle find.
- Done 2026-11-19 (not pushed yet): 13 more guild names in `GUILD`.
- Ludra's breath (`CFG.bingo.breath`): random vertex; orange band from 8.5 s (11.5 s left on the cast), kills from
  9.1 s to 11.5 s (8.5 s left, user-confirmed). Half-width 4.2 m is a guess. Players/bots whose square is in it hold
  the far corner (`breathCorner()`, green ring + arrow for the player); nobody steps into it; runners wait at its edge.
- Bots never step into a snapped red circle and leave one by the shortest way that doesn't lead into another
  (`liveCircles()`, `circleExit()`); needed because everyone crosses the board right as the 3rd circles snap (11.84 s).
  Player callouts: "GET OUT OF THE RED CIRCLE", "Red circles on the way".
- Second breath (user, 2026-11-19): Ludra breathes twice per board. Each breath gets its own random vertex
  (`S.breaths`, `breathAt(t)`; `S.breath` = the current/next one). Inside the safe square you're immune; on the way
  in it can kill you.
- Breath timings from the user's cast-bar reads (2026-11-19): 1st line swings in 8.0, settles 8.7, fires 9.2, ends
  11.5; 2nd swings in 16.8, settles 17.6, fires 18.1, lasts until 20.0. Ludra (the `ludra` group, `ludraPose(t)`)
  starts high over the middle of the board and drifts slowly to her 1st spot (8 m past the vertex) from the moment
  the board appears, then turns to the middle; the 2nd flight (1.1 s) starts as soon as the 1st breath ends, then
  she waits at the spot; the 2nd corner is never the 1st; the line follows her aim (55° swing), then fills
  in width like the circles. User's reason: the breath felt like it came from nowhere; her flight is the warning.
- Breath look (from the user's screenshots): white-pink beam from high past the vertex onto the middle, orange-pink
  band on the squares, purple flame bursts.
- Bots: a runner who can be inside the safe square before a breath starts goes straight in ("BREATH: RUN IN NOW" for
  the player); center bots jump into their orb as soon as a jump reaches it once the safe square is found.
  Teammates caught by the breath or outside at the meteor fall (gray, lying down) and get no more circles.
- Missing your square is no longer a death (user, 2026-11-19): it's logged in `S.missed`; it only kills if that
  square was the safe one (never found -> the Trial-end death says it was yours). The end screen notes any misses.
- Meteor (`CFG.bingo.meteor`, visual only): huge cracked magenta ball over the middle for the last 2.5 s of the
  cast, hits at 20.0 s with a shockwave; the kill message now names it.
- `S.auto = true` (tests only) makes your character follow the bot rules. Tests with it (both breaths), every safe
  square x every 1st-breath vertex: corner roles 1006/1152, center 123/144; every miss is a last-circle find (the 2nd
  breath at 17.5 s blocks most of them; the user said a last-circle find can't be reached from far away); with a find on circles 1-3
  no teammate falls and no bot is caught in a circle.
- Next: confirm orb marker/height/landing times and the breath width; phase 2 board.
- The user's frame counts here were 1/30 s steps (first converted at 60 fps by mistake = everything 2x too fast).
  Always check a frame count against two timestamps before converting.
- Filled squares are visual only until the user confirms what they do.

## Colors (2026-11-19, from the user's description and the Spiritmaster video at 4:24)
- Third card on the start screen. Reference and open questions: `ludra-colors-mechanic.md`. Rules in `colorsStep()`,
  values in `CFG.colors`, visuals in `syncColors()`.
- Bots now wander instead of standing on fixed spots: 5 melee stay in the north strip near Ludra, 4 ranged spread
  across the rows, all inside their color's side (`CFG.colors.region`). Same colors may overlap. Test (300 runs,
  you standing still): no bot hits, opposite colors never closer than 4.3 m, 94% of bots on their own side at the end.
- Wrong-side bots now cross straight to their side (nearest edge as the goal) and walk around a crowd when jammed
  (stuck = under 0.6 m of progress in 0.8 s). 300-run test: 97% of bots on their own side at the end, 0 bot hits,
  opposite colors never closer than 4.3 m.
- Hits, not instant death: each contact with an opposite aura ticks (contact, then every 0.5 s); 5 hits = down
  (`CFG.colors.maxTicks`, `tickEvery`). Red screen flash on each hit (`#hurt`), "Hits x / 5" in the info line.
- Ludra's orbs (blue left, red right) show at 3.0 s; at 6.0 s every player and bot gets a random aura (spinning
  ring + ground field). Blue goes west, red goes east. Opposite auras within 4 m hurt both (you: death).
- Bots walk to their side and sidestep opposite auras (`SIDESTEP`, `colorsClash()`). Bot-only test, 300 runs, your
  character standing out of the way: 0 bot deaths; 95% of bots reach their spot; ~3% end on the wrong side (a
  crowd crossing in the middle leaves a few stuck). Not fixed yet.
- Nothing measured frame by frame yet: all timings and distances are estimates.

## Next
- User playtest for timing/size feel; tune `CFG`.
- Ideas not started: sound cues, party bots, other Ludra mechanics, hosting (GitHub Pages).

## Colors: teleport phases (2026-11-19)
- Ludra starts north, then teleports twice (always 3 stages). Each jump goes to W, S, E or north (random, not the same corner)
  `CFG.colors.tp` holds the placeholder timings.
- Strategy (menu): fixed (blue left, red right as seen from Ludra) or adaptive (least walking; the other color goes
  around). Frame and sides in `colorsFrame`-style helpers `frameOf`, `colorsSide`, `colorsBestLeft`.
- Melee use the boss-side strip (`CFG.colors.area.melee`), ranged the rows (`area.ranged`). Areas tightened (melee u 6..13, v 11..18; ranged u 6..16, v 0..12).
- Tests (60 runs each, all 6 combinations): no bot hits, no opposite colors within 4.3 m, 98–100% of bots on their
  side at the end. Fixed never flips sides; adaptive flips about half the time.
- Not checked in the browser visually after a teleport (the menu covered the screen in the last check).
