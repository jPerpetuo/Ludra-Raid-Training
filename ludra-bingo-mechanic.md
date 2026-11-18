# Ludra – "Bingo board" mechanic reference (AION 2, Sanctuary raid)

A builder's reference for the Bingo board, in the same format as [`ludra-zikel-mechanic.md`](ludra-zikel-mechanic.md).
The board happens **twice** in the fight; this file covers the **phase 1** board, when Ludra is near 50% health
(Confirmed). **Work in progress:** what the orbs do is not yet known. Last updated 2026-11-18.

Unofficial, fan-collected information. Not affiliated with NCSOFT.

Tags: **Confirmed** = stated by an experienced raider · **Measured** = frame counts from video · **Seen** = visible in
video, not confirmed · **Estimate** = tunable guess.

## Summary

1. A **6 × 6 board** of squares appears on part of the arena floor (Confirmed). Players can walk off it (Seen).
2. One square is the **safe square**, chosen at random and hidden (Confirmed).
3. An orange circle appears under **every player** and **follows** them (Confirmed).
4. At about 70% of its fill it **snaps to the ground** where the player is and stops following (Confirmed).
5. When it resolves, anyone inside **any** circle, their own or someone else's, takes heavy damage. Trainers treat
   it as death (Confirmed). A **perfect dodge** right at the end avoids it (Confirmed).
6. Each resolved circle **fills the square** it landed on: the square glows red/magenta (Confirmed, Seen).
7. When a circle lands on the safe square, that square gets **tall translucent blue/cyan glass walls**: the safe
   zone is found (Confirmed, Seen).
8. A player **inside the safe square is immune** to damage, including circles resolving inside it. So as soon as
   it's found, **everyone runs into it** (Confirmed).
9. When the **"Ludra's Trial"** cast finishes, **everyone outside the safe square dies** (Confirmed).
10. Circles come **4 times** (Confirmed). The team fills squares until someone finds the safe square.
11. **Two orbs** appear on **opposite sides** just outside the board: north + south or west + east, apparently at
    random (Confirmed). A red marker shows on the ground first; then the orb appears **high in the air** above it
    and **slowly floats down**. A player must **grab it before it reaches the ground**, by **jumping into it**
    while it floats. Right after it appears it's too high to reach: players wait for it to come down a bit
    (Confirmed). The two centre players handle the orbs.

## Timing (Measured)

Frame counts by an experienced raider, stepping YouTube one frame at a time. On this video each step was **1/30 s**:
60 steps between the board (2:51) and the first circles (2:53) span 2 s. Always convert a frame count against two
known timestamps.

| Event | Steps | Seconds |
|---|---|---|
| Board appears | 0 | 0.00 |
| Circle appears under each player | 60 after the board | 2.00 |
| Circle snaps to the ground | 45 after it appears | +1.50 |
| Circle resolves | ~65 after it appears | +2.17 |
| Next circle appears | ~60 after the previous one resolves | +2.00 |

Circles appear at 2.0, 6.17, 10.34 and 14.51 s after the board; the last resolves at 16.68 s. After each snap you
have about **0.67 s** to get out.

The **"Ludra's Trial"** cast is **16.0 s** and starts just before the first circle resolves (Confirmed from the cast
bar), so it ends about **20 s** after the board: only about 3.3 s after the last circle resolves. If the safe square
is found on the last circle, players far from it can't reach it in time (Confirmed).

Orb timing, read off the cast bar in screenshots (Seen, times after the board = 20 − cast left):

| Event | Cast left | After the board | Source |
|---|---|---|---|
| Red marker on the ground | a little before 11.0 | ~8.5 s | Estimate |
| Orb appears high in the air | 11.0 | 9.0 s | Seen |
| Players jump into it | ~6.4 | ~13.6 s | Seen |
| It would reach the ground | ~4.5–5.4 | ~14.9 s | Estimate (1–2 s after the grab) |

Size, from screenshots (Seen): a circle is a little narrower than a square, and a player is a small fraction of a
square. The trainer's 4 m squares and 1.8 m circle radius fit that.

## Common solve: clockwise sweep in pairs (Confirmed)

Directions with Ludra as north. Corners: **1 = south-west, 2 = north-west, 3 = north-east, 4 = south-east**.
Squares are `[row, column]`, row 0 = north edge, column 0 = west edge.

```
        col 0  1  2  3  4  5
row 0     O2 →  →  →  I3 O3        O = outside, I = inside, number = corner
row 1     I2 →  →  →  ↓  ↓         Each pair covers 2 squares per circle and moves
row 2     ↑  ↑  C↗ C  ↓  ↓         one square clockwise after each snap.
row 3     ↑  ↑  C  C↙ ↓  ↓         C = the two centre players: 2 squares each,
row 4     ↑  ↑  ←  ←  ←  I4        then out to the orbs.
row 5     O1 I1 ←  ←  ←  O4
```

"Outside" walks the board's outer edge, "inside" the row or column next to it. (Melee usually take outside and
ranged inside, but it's the position that matters.)

| Player | Squares in order |
|---|---|
| Corner 1 outside | [5,0] [4,0] [3,0] [2,0] |
| Corner 1 inside | [5,1] [4,1] [3,1] [2,1] |
| Corner 2 outside | [0,0] [0,1] [0,2] [0,3] |
| Corner 2 inside | [1,0] [1,1] [1,2] [1,3] |
| Corner 3 outside | [0,5] [1,5] [2,5] [3,5] |
| Corner 3 inside | [0,4] [1,4] [2,4] [3,4] |
| Corner 4 outside | [5,5] [5,4] [5,3] [5,2] |
| Corner 4 inside | [4,5] [4,4] [4,3] [4,2] |
| Centre A | [2,2] [2,3], then to the north (or east) orb, jump into it, then the safe square |
| Centre B | [3,3] [3,2], then to the south (or west) orb, jump into it, then the safe square |

8 × 4 + 2 × 2 = **all 36 squares**, so the safe square is always found if everyone drops on their square. As soon as
it's found, everyone stops sweeping and runs into it.

## Trainer values (current)

In the `CFG.bingo` block of `ludra-raid-training.html`:

| Value | Setting | Source |
|---|---|---|
| Board | 6 × 6 | Confirmed |
| Circle timings | as above | Measured |
| Square size | 4 m | Estimate |
| Circle radius | 1.8 m (a little smaller than a square) | Estimate |
| "Ludra's Trial" | 16 s cast from 4.0 s, ends 20.0 s after the board | Confirmed length, start approximate |
| Orbs | 15 m from the centre (just off the board), random axis; marker 8.5 s, appears 9 m up at 9.0 s, lands 14.9 s | Estimates around the confirmed behaviour |
| Grabbing | touch the orb: a standing player reaches 2.2 m, a jump (Space) adds 1.5 m; within 1.4 m sideways | Estimate |
| Teammates | 9 bots following the plan above; the player picks a corner and outside/inside, or a centre spot | Design |
| Bots once found | run into the safe square (centre players once they have their orb) | Confirmed behaviour |
| Fail conditions | caught in any circle outside the safe square; your circle lands outside your square before the safe square is found; your orb lands before you grab it (centre); outside the safe square (or not found) when the cast ends | Design |

With those numbers a jump first reaches the orb at about 12.2 s; standing under it, you'd touch it at about 13.3 s.

Tested against every possible safe square: a corner player who sweeps and then runs straight to the safe square
clears 284 of 288; the other 4 are last-circle finds in the far corner, which can't be reached in time, as in the
real fight (the death message says so). A centre player who covers 2 squares, steps out of their red circles, jumps
into the orb and runs to the safe square clears 131 of 144; 5 are unreachable last-circle finds, and 8 ran into the
safe square just as the others' 4th circles resolved there (those circles reach a little past the square's edge).

## Open questions

1. **Orbs:** what happens if one is missed; whether anyone (not just the centre players) can grab them; the exact
   marker time, start height and landing time.
2. **Damage area:** the circle only, or the whole square?
3. **Off the board:** what happens if a circle resolves off the board (the centre players drop theirs at the orbs)?
4. **Normal vs hard** differences (the source video is normal mode), and how the second board differs.

## Sources

| Video | Frame rate | Used for |
|---|---|---|
| [Ludra normal, Spiritmaster POV](https://youtu.be/r76j86Hw15o?t=171) (2:51–2:57) | 60 fps (counted in 1/30 s steps) | Circle timings (player frame counts), board look, safe square |
