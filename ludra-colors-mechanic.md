# Ludra – "Colors" mechanic reference (AION 2, Sanctuary raid)

A builder's reference for the moment Ludra holds two colored orbs and every player gets an aura, in the same format as
the other mechanic references in this folder. Ludra's orbs are a *mid-fight* event, seen in the Spiritmaster video
starting at about **4:24** (youtu.be/r76j86Hw15o?t=264).

Unofficial, fan-collected information. Not affiliated with NCSOFT. Last updated 2026-11-19.

Tags: **Confirmed** = stated by a player who knows the fight · **Seen** = visible in video, not timed · **Estimate** =
tunable guess.

## Summary

1. Ludra holds a **blue orb in her left hand** and a **red orb in her right** (Seen).
2. Every player and teammate gets a **random aura**, blue or red. The aura is a **spinning ring** around the player
   (Confirmed, Seen).
3. Blue auras go to the **left side of the room** (west, as you face Ludra), red auras to the **right side** (east)
   (Confirmed).
4. Auras act like colorss: standing **close to someone with the opposite aura hurts both of you**. Two players with
   the **same** aura can stand together (Confirmed).

## Timing

| Event | Time | Source |
|---|---|---|
| Orbs appear in Ludra's hands | ~4:24 on the video | Seen (the video time the player gave) |
| Auras are given | just after the orbs show | Estimate |
| Players walk to their side | a few seconds | Estimate |
| Mechanic ends | ~10 s after the auras | Estimate |

The trainer uses: orbs at 3.0 s, auras at 6.0 s, end at 16.0 s. None of these were timed frame by frame yet.

## Rules

| Topic | Value | Source |
|---|---|---|
| Damage distance | 4 m between opposite auras | Estimate |
| Same aura | can stand together, no damage | Confirmed |
| Hits | each contact with an opposite aura is a hit (tick): one on contact, then one every 0.5 s while the other stays close. Both players in the pair take the hits. 5 hits = down (for you: a loss) | Estimate |
| Feedback | a red screen flash on every hit you take, and a "Hits x / 5" counter | Design |
| Side for blue | west (left as you face Ludra) | Confirmed (user: "lado esquerdo da sala") |
| Side for red | east (right) | Confirmed (user: "lado direito da sala") |
| Dodge | does not avoid the damage | Estimate |

## Open questions

1. Exact damage distance, and whether it depends on how fast a player is moving.
2. Exact timing of the orbs, auras and the walk to each side (frame counts needed).
3. Does a player on the wrong side (but not touching an opposite aura) take damage at the end?
4. Does the aura last until the end of the mechanic, or drop after a while?
5. Is the damage a kill, or partial damage?
6. Do the sides match exactly "left/right" as the player sees them, or as Ludra's left and right hands?

## Trainer values

In the `CFG.colors` block of `ludra-raid-training.html`:

| Value | Setting | Source |
|---|---|---|
| Orbs appear | 3.0 s | Estimate |
| Auras given | 6.0 s | Estimate |
| End | 16.0 s | Estimate |
| Damage distance | 4 m | Estimate |
| Side layout | columns 7 m and 11.5 m from the middle, 5 rows per column | Design |
| Spawns | random, at least 4.5 m apart: you and 4 bots in the north strip (melee/tanks, y −18 to −15); 5 bots spread across the north half, west to east, to about 2 m past the middle | Design |
| Teammates | 9 bots: 5 melee stay in the north strip (y −18 to −10) near Ludra; 4 ranged walk the rows y −14 to 2. Both wander inside their color's side (blue west, red east) and pause now and then. Same colors can overlap; opposite colors never get closer than 4.3 m | Design |

## Sources

| Video | Used for |
|---|---|
| [Ludra normal, Spiritmaster POV](https://youtu.be/r76j86Hw15o?t=264) (from 4:24) | The orbs in Ludra's hands. Confirmed by the player's screenshot at the start of the mechanic |

## Teleport phases (added 2026-11-19, from the user's description)

Ludra always starts in the north. After the auras are given she can teleport to one of the other three corners,
picked at random, and do it again (always 3 stages: north, then two teleports). The players keep their
auras all the time.

- **Fixed strategy:** blue always takes the left and red the right, as seen by players facing Ludra. So when she moves,
  the sides move with her.
- **Adaptive strategy:** after each teleport the team picks whichever assignment needs less walking. The color that
  is already close to a side keeps it, and the other color walks around behind (through the middle, or around the
  wall).
- **Melee** stay near Ludra (the boss-side strip) on their color's side, even after she moves. Ranged stay in the
  rows on their side.
- Timings are placeholders until they are read from the video: Ludra vanishes at 12 s, reappears 1.5 s later at the
  new corner, and the team has 8 s before the next teleport (`CFG.colors.tp`).

Open: real teleport timings, how the adaptive choice is made in the game (least walking is only our guess), and whether
the other color ever walks through the middle while the sides are changing.
