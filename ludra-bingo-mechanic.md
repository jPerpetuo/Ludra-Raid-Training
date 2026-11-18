# Ludra – "Bingo board" mechanic reference (AION 2, Sanctuary raid)

A builder's reference for the Bingo board, in the same format as [`ludra-zikel-mechanic.md`](ludra-zikel-mechanic.md).
The board happens **twice** in the fight; this file covers the **phase 1** board, when Ludra is near 50% health
(Confirmed). **Work in progress:** what the orbs do is not yet known. Last updated 2026-11-19.

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
9. When the **"Ludra's Trial"** cast finishes, **everyone outside the safe square dies** (Confirmed). With about
   **2.5 s left** on the cast, a **huge red/magenta ball** (a meteor, with glowing cracks) appears over the middle of
   the board; it is what hits when the cast ends (Confirmed, Seen).
10. Circles come **4 times** (Confirmed). The team fills squares until someone finds the safe square.
11. **Two orbs** appear on **opposite sides** just outside the board: north + south or west + east, apparently at
    random (Confirmed). A red marker shows on the ground first; then the orb appears **high in the air** above it
    and **slowly floats down**. A player must **grab it before it reaches the ground**, by **jumping into it**
    while it floats. Right after it appears it's too high to reach: players wait for it to come down a bit
    (Confirmed). The two centre players handle the orbs.
12. **Ludra's breath** crosses the board along a **diagonal**, from one of its **4 vertices at random** (Confirmed).
    Ludra **flies to a spot past that vertex and turns to the middle**; her **orange line swings across the board
    with her aim** until it settles on the diagonal, then **fills up** like the circles; then she breathes along it
    and **touching it is an instant kill** (Confirmed, Seen). Her flight and turn are what tell players where it's
    coming from. It shows as a huge white-pink beam onto the
    board with the squares under it glowing orange-pink and purple flames bursting from them (Seen). Players whose
    square lies in it walk to the **far corner** of their square, away from the diagonal, and wait there (Confirmed,
    Seen). Players already **inside the safe square are immune** to it; players still running there can be killed by
    it on the way (Confirmed).
13. Ludra breathes **twice** per board, **never twice from the same corner**: the 2nd comes from one of the other 3
    (Confirmed). She starts the board **over the middle of it** and **slowly moves to her first spot from the moment
    the board appears** (Confirmed), and
    **as soon as the 1st breath ends** flies straight to her 2nd spot, waits there, then turns for the 2nd breath
    (Confirmed).

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

Breath timing, read off the cast bar in screenshots (times after the board = 20 − cast left):

| Event | Cast left | After the board | Source |
|---|---|---|---|
| 1st breath: orange line starts swinging in | 12.0 | 8.0 s | Confirmed |
| 1st breath: line settles on the diagonal, starts filling | 11.3 | 8.7 s | Confirmed |
| 1st breath fires (kills) | 10.8 | 9.2 s | Confirmed |
| 1st breath ends | 8.5 | 11.5 s | Confirmed |
| 2nd breath: line starts swinging in | 3.2 | 16.8 s | Confirmed |
| 2nd breath: line settles, starts filling | 2.4 | 17.6 s | Confirmed |
| 2nd breath fires (kills) | 1.9 | 18.1 s | Confirmed |
| 2nd breath ends | 0 (cast ends) | 20.0 s | Confirmed |

Ludra's 1st move (from over the middle of the board) starts with the board and lands just before the line appears;
her 2nd starts right as the 1st breath ends. The trainer uses 1.1 s for the 2nd flight (Estimate).

The 1st band appears just after the 2nd circle resolves (8.34 s), so a safe square found on circle 2 has to be
reached around the breath. The 2nd comes right after the last circle resolves (16.68 s), so it makes a last-circle
find even harder to reach.

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
| Centre A | [2,2] [2,3], then beside the north (or east) orb, drop the 3rd circle there, go under the orb, jump into it, then the safe square |
| Centre B | [3,3] [3,2], then beside the south (or west) orb, drop the 3rd circle there, go under the orb, jump into it, then the safe square |

The centre players must not wait under the orb while their 3rd circle forms, or it drops on the orb spot (Confirmed).
They wait a few metres to the side, let it snap there, step out, then go under the orb.

8 × 4 + 2 × 2 = **all 36 squares**, so the safe square is always found if everyone drops on their square. As soon as
it's found, everyone stops sweeping and runs into it.

**During each breath**, the band covers the squares on its diagonal and, with the trainer's width, most of the squares
next to it. Anyone whose square is in it holds the corner of that square farthest from the diagonal. Anyone running to
the safe square waits at the edge of the band instead of crossing it, then goes once it ends. Because the 3rd circles
snap at 11.84 s, right after the breath, players then cross the board while red circles are on the ground: go around
them or wait for them to pop (0.67 s).

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
| Meteor | appears 2.5 s before the cast ends (17.5 s), flies in from the north, hangs ~11 m over the middle, drops onto the board at 20.0 s; radius 7 m. Visual only: the kill is the Trial check | Timing Confirmed, look and size Estimate |
| Breath | twice, from two different random vertices: Ludra flies 1.1 s to a spot 8 m past the vertex; line swings in over 55° (side random), times as above; half-width 4.2 m (squares next to the diagonal are safe only in their far corner); only on the board; the safe square protects | Times as above, width Estimate |
| Teammates | 9 bots following the plan above; the player picks a corner and outside/inside, or a centre spot | Design |
| Bots once found | run into the safe square (centre players once they have their orb) | Confirmed behaviour |
| Bots and the breath | hold the far corner if their square is in the band; never step into it; if caught, leave the shortest way; while running to a found safe square just before it shows, don't cut through either diagonal | Design |
| Bots and red circles | never step into a snapped circle; if standing in one, leave the shortest way that doesn't lead into another | Design |
| Fail conditions | caught in any circle outside the safe square; touched by the breath outside the safe square; your orb lands before you grab it (centre); outside the safe square (or not found) when the cast ends | Design |
| Missing your square | not a death by itself (user-confirmed): it only matters if that square was the safe one, because then nobody finds it and the cast kills everyone; the death message and end screen say so | Confirmed |

With those numbers a jump first reaches the orb at about 12.2 s; standing under it, you'd touch it at about 13.3 s.

Tested against every safe square × every 1st-breath vertex (2nd vertex one of the other 3), with the test player
following the bot rules: corner players clear 1006 of 1152 and the centre player 123 of 144. Every miss is a **last-circle find**:
it resolves at 16.68 s and the 2nd breath fires at 18.1 s, so unless the safe square is close or on your side of the
breath, you can't get in before the meteor (the death message says so). When the safe square is found on circles 1–3,
nobody dies: no bot is touched by the breath or caught in a circle. A player whose square is next to the breath's
diagonal dies if they stay in the middle of it and survives in the far corner.

Teammates in the trainer fall (grey, lying down) when the breath touches them or they are outside the safe square
when the meteor lands; a fallen teammate drops no more circles.

## Open questions

1. **Orbs:** what happens if one is missed; whether anyone (not just the centre players) can grab them; the exact
   marker time, start height and landing time.
2. **Damage area:** the circle only, or the whole square?
3. **Off the board:** what happens if a circle resolves off the board (the centre players drop theirs at the orbs)?
4. **Normal vs hard** differences (the source video is normal mode), and how the second board differs.
5. **Breath:** the exact width of the band (the trainer's 4.2 m half-width is a guess from screenshots); whether it
   reaches past the board. When Ludra leaves the middle for her 1st spot, how fast she flies, and how far the
   line swings.

## Sources

| Video | Frame rate | Used for |
|---|---|---|
| [Ludra normal, Spiritmaster POV](https://youtu.be/r76j86Hw15o?t=171) (2:51–2:57) | 60 fps (counted in 1/30 s steps) | Circle timings (player frame counts), board look, safe square |
