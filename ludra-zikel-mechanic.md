# Ludra – "Zikel" mechanic reference (AION 2, Sanctuary raid)

A builder's reference for anyone who wants to make their own practice tool for this mechanic. It collects what is
known so far, says how sure we are of each number, and how it was measured.

"Zikel" is the name players use for the mechanic. The boss is **Ludra**.

Unofficial, fan-collected information. Not affiliated with the game's publisher. Last updated 2026-11-17.

## How sure are we?

Every fact below is tagged:

| Tag | Meaning |
|---|---|
| **Confirmed** | Stated by an experienced raider from playing the fight |
| **Measured** | Timed frame by frame from gameplay video (accuracy given) |
| **Estimate** | Eyeballed or chosen to feel right; treat as a tunable default |

## Orientation

Directions use **Ludra's side as north** (Confirmed convention). So "east–west" is the line running left–right as you
face the boss.

## Summary

1. Ludra flies backwards out of the arena and the fight area becomes a **square boxed in by walls**.
2. Four **orange lines** appear one after another, every 4 seconds, in a **fixed order**.
3. For each line: stay **off** it while it is orange, step **onto** it once the orange finishes, and be on it when the
   rest of the arena **detonates**.
4. After each line, a **wall of vertical lasers** forms on one side of the room, then sweeps across the whole room
   in about 2.5 seconds, still moving when the next line strikes; stand in a gap between beams.
5. **Hard mode only:** an orange circle drops under every player's feet after each line; be outside it (or perfect
   dodge) when it finishes filling.

## Fixed sequence

The order, angles and laser directions are the same every time (Confirmed).

| # | Orange line runs | Laser wall comes from (and sweeps toward) |
|---|---|---|
| 1 | East ↔ West, through the centre | South → North |
| 2 | South-west ↔ North-east (diagonal) | West → East |
| 3 | North ↔ South, through the centre | East → West |
| 4 | North-west ↔ South-east (diagonal) | North → South |

Lines 1 and 3 run through the middle of the room (Confirmed). The diagonals are assumed to run corner to corner
through the centre (Estimate).

## The line (each of the 4)

### Rules (Confirmed)

- **Inside the orange line when it finishes → instant death.** Stay out while it is orange.
- After it finishes, a lightning strip forms on the line. **Everything off the line then detonates → instant death.**
  You must be standing on the line at the detonation.

### Timing (Measured)

Times are relative to the **strike** = the moment the orange line finishes.

| Event | Time | Notes |
|---|---|---|
| Orange line appears | −0.65 s | Measured 0.65 s (30 fps video) and 0.67 s (60 fps video) |
| **Strike** – orange gone, kills anyone inside | 0.00 s | |
| Lightning strip visible on the line | +0.35 s | |
| **Detonation** – kills anyone off the line | +1.90 s | Measured once at 30 fps, consistent with the 60 fps video (±0.1 s) |
| Next orange line appears | +3.35 s | |
| Next strike | +4.00 s | Lines are exactly 4.0 s apart in both videos |

So the step-in window is **1.9 s**: from the strike to the detonation.

### Size (Estimate)

- The strip is about **2–3 character widths wide** (the trainer uses 4 m).
- It spans the whole room, wall to wall.

## The laser wall

### Rules

- A row of vertical laser beams forms on one wall and sweeps across to the opposite wall (Confirmed).
- Beams are evenly spaced; stand in a gap so the row passes around you (Confirmed).
- **Damage:** on hard mode a beam kills. On normal mode it kills most players, but very well geared players can survive
  (Confirmed). A trainer should treat a hit as death.

### Timing (Measured, 60 fps video, 1 sweep)

Frame counts by an experienced raider stepping through the video one frame at a time, plus a frame check of the
far-wall arrival. Times are relative to the strike of the line the row belongs to; the strike in that pull was taken
from the detonation (detonation − 1.9 s), so allow ±0.1 s.

| Event | Time | Notes |
|---|---|---|
| Row visible on its starting wall | ~+1.25 s | ~100 frames (1.65 s) before it starts moving |
| Row starts sweeping | ~+2.9 s | ~20 frames (0.33 s) after the hard-mode circle resolves |
| Row reaches the far wall | ~+5.4 s | ~150 frames (2.5 s) after it starts; arrival frame-checked at 4:39.92 |

So a row crosses the whole room in about **2.5 s**, at a steady speed, and is still moving when the next line
strikes (+4.0 s). Players dodge it while leaving the old line and stepping onto the new one.

### Size (Estimate)

| Value | Current guess |
|---|---|
| Beams per row | 8–10 seen across one wall |
| Beam spacing | ~5 m (trainer value) |
| Gap position | Unknown whether the room's centre is a beam or a gap |

## Hard-mode orange circle

### Rules (Confirmed)

- Hard mode only.
- An orange circle appears under a player's feet and fills up.
- When it **finishes filling**, you must be **outside it** or **perfect dodge**; otherwise you die.

### Behaviour (Measured)

- Every player gets their own circle at the same time (3+ circles seen at once).
- The circle **stays where it dropped**; it does not follow the player.
- It drops while players are standing on the line, and resolves **after** the detonation. So the solution is: step onto
  the line, survive the detonation, then move out of your own circle (or perfect dodge as it resolves).

### Timing (Measured, 60 fps video, ±0.02 s)

Relative to the line's strike:

| Line | Circle appears | Circle resolves | Fill time |
|---|---|---|---|
| 1 | +0.98 s | +2.80 s | 1.82 s |
| 2 | +0.71 s | +2.53 s | 1.82 s |
| 3 | +1.33 s | +3.21 s | 1.88 s |

- **Fill time is consistent: ~1.85 s.**
- **The drop time is not consistent:** 0.7–1.35 s after the strike. A trainer should randomise it in that range rather
  than use a fixed value.
- It resolves 0.6–1.3 s after the detonation.

### Size (Estimate)

- Radius roughly **3 m**: a little wider than the line strip.

### Unknown

- Whether standing in **another** player's circle when it resolves also kills.

## One full cycle at a glance

Relative to the strike (0.0 s). All measured except where marked.

```
-0.65  orange line appears                              (stay OFF it)
 0.00  STRIKE: orange gone, kills anyone inside it      (now step ON)
+0.35  lightning strip shows on the line
+0.70 .. +1.35  [hard] orange circle drops under each player
+1.25  this line's laser row appears on its wall
+1.40  lines 2-4: the previous line's laser row reaches the far wall
+1.90  DETONATION: kills anyone off the line
+2.55 .. +3.20  [hard] circle resolves: be out of it, or perfect dodge
+2.90  this line's laser row starts sweeping
+3.35  next orange line appears
+4.00  next strike (the laser row is still crossing)
+5.40  laser row reaches the far wall
```

## Player-side details (for a trainer)

| Topic | What we know |
|---|---|
| Starting position | Most players are in melee range under Ludra (north edge) when the mechanic starts (Confirmed) |
| Dodge | Uses a **stamina bar**, not a cooldown; a full bar is about **5 dodges** and refills over time (Confirmed). Refill rate unknown |
| Perfect dodge | Avoids the hard-mode circle (Confirmed). Invulnerability length unknown |
| Camera | Third-person camera work is a large part of why players fail: tracking the laser row, the line and your own position at once. A 3D trainer is much more useful than a top-down one (Confirmed) |
| Arena size, move speed | Unknown. The trainer uses a 40 m square and 6 m/s as feel values |

## Machine-readable summary

```json
{
  "orientation": "Ludra = north",
  "lineIntervalSec": 4.0,
  "line": {
    "orangeDurationSec": 0.65,
    "killIfInsideAtStrike": true,
    "lightningVisibleAfterStrikeSec": 0.35,
    "detonationAfterStrikeSec": 1.9,
    "killIfOutsideAtDetonation": true,
    "widthMeters": { "estimate": 4 }
  },
  "sequence": [
    { "line": "E-W",   "throughCentre": true, "laserFrom": "S", "laserTo": "N" },
    { "line": "SW-NE", "throughCentre": true, "laserFrom": "W", "laserTo": "E" },
    { "line": "N-S",   "throughCentre": true, "laserFrom": "E", "laserTo": "W" },
    { "line": "NW-SE", "throughCentre": true, "laserFrom": "N", "laserTo": "S" }
  ],
  "laser": {
    "lethal": true,
    "appearAfterStrikeSec": 1.25,
    "startMoveAfterStrikeSec": 2.9,
    "crossRoomSec": 2.5,
    "estimate": { "beamsPerRow": [8, 10], "spacingMeters": 5 }
  },
  "hardCircle": {
    "perPlayer": true,
    "followsPlayer": false,
    "dropAfterStrikeSec": { "min": 0.7, "max": 1.35 },
    "fillSec": 1.85,
    "killIfInsideAtResolve": true,
    "perfectDodgeAvoids": true,
    "radiusMeters": { "estimate": 3 }
  },
  "dodge": { "type": "stamina", "fullBarDodges": 5 }
}
```

## Open questions

1. Laser timing comes from one sweep. Still open: whether the sweep start is tied to the line strike or to the
   hard-mode circle resolving (the circle's drop time varies), and whether normal mode uses the same timing.
2. Laser beam count, spacing, and whether the room's centre is a beam or a gap.
3. Whether another player's hard-mode circle can kill you.
4. Real arena size, line width and circle radius.
5. Time from Ludra flying back to the first orange line.
6. Dodge stamina refill rate and perfect-dodge invulnerability length.
7. Whether normal mode differs from hard in anything other than the circles and laser damage.

## Sources and method

Timings were taken by pausing YouTube and stepping through individual video frames (1/30 s or 1/60 s), noting the
first and last frame each effect is visible.

| Video | Frame rate | Used for |
|---|---|---|
| [Ludra Hard, Cleric POV](https://youtu.be/vOb-LqzxLsE?t=793) (from 13:05) | 30 fps | Overall sequence, line timings (lines 2 and 4) |
| [Ludra Hard Mode clear, Templar POV](https://youtu.be/RNZA_QjX3NE?t=457) (from 7:37) | 60 fps | Hard-mode circle timings (3 circles), line 1 re-check, 4 s interval |
| [Same video, earlier pull](https://youtu.be/RNZA_QjX3NE?t=270) (4:30–4:40) | 60 fps | Laser sweep (player frame counts + far-wall frame check), detonation times |

Pitfalls when measuring:

- The camera rotates constantly; zoom in on the player to see small ground effects.
- The arena floor has **round platforms with orange rims** that look like hard-mode circles. The real circle has an
  orange shaded fill that disappears when it resolves; the platform rim stays.
- Bright detonation and lightning flashes can hide an effect for a frame or two.
- A laser row hitting the far wall flashes as a dense wall of beams, close in time to the next detonation, and is
  easy to mistake for the detonation itself. Follow the row's 8–10 thick beams across the floor to be sure.
- Don't assume where the recording player stands: they may still be on the previous line, near a wall. Time a
  sweep from wall to wall, not from wall to player.
- With the low third-person camera, a row moving toward the camera can look like it is standing still on the wall
  for a second. An earlier version of this file made that mistake.

## Reference implementation

A working 3D browser trainer built from this data: `ludra-raid-training.html` in this folder. All values above are in
the `CFG` block at the top of its script.
