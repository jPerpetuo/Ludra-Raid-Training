# Ludra – "Colors" (aura) mechanic reference (AION 2, Sanctuary raid)

A builder's reference for the moment Ludra holds two colored orbs and every player gets a blue or red aura, in the same
format as the other mechanic references in this folder. The orbs are seen in the Spiritmaster video starting at about
**4:24** (youtu.be/r76j86Hw15o?t=264). The flights between corners are a placeholder from the player's description and
have not been timed yet.

Unofficial, fan-collected information. Not affiliated with NCSOFT.

Tags: **Confirmed** = stated by a player who knows the fight · **Seen** = visible in video, not timed · **Estimate** =
tunable guess · **Design** = how the trainer models it.

## Summary

1. Ludra holds a **blue orb in her left hand** and a **red orb in her right** (Seen).
2. Every player gets a random **blue or red aura** (Confirmed). The trainer always gives five of each.
3. Opposite auras **hurt each other** when they get too close. Two players with the same aura can stand together (Confirmed).
4. The team splits by color: **blue on one side, red on the other**, as seen by the players facing Ludra (Confirmed).
5. Ludra **flies to another corner** and the team has to regroup. She starts in the north and flies twice (Design).

## Stages and timing

| Stage | What happens | Timing (trainer) |
|---|---|---|
| 1 | Ludra in the north. Orbs show in her hands, then auras are given | Orbs at 3.0 s, auras at 6.0 s |
| 2 | Ludra flies to a random corner (west, south or east) | First flight at 12.0 s |
| 3 | Ludra flies again, to any corner except the one she left and the opposite one | 8 s after she lands |

- A flight takes 0.9 s: she rises 14 m while fading out, is gone for 1.5 s, then drops back in at the new corner while
  fading in. These are **placeholder** timings until they are read from the video (`CFG.colors.tp`).
- She never flies to the opposite corner (north to south, west to east). From the north she goes west or east; from the
  west or east she goes north or south.

## Sides

"Left" and "right" are seen by the players facing Ludra, so they change when she moves.

- **Fixed strategy:** blue always takes the left and red the right. When Ludra moves, the sides move with her.
- **Adaptive strategy:** the first stage always uses the fixed sides (blue left). After each flight, the team picks the
  assignment that needs the least walking. The color already close to a side keeps it, and the other color walks around
  behind (through the middle, or around the wall). The adaptive choice is a trainer guess, not a confirmed rule
  (Estimate).

Melee and ranged stay on their color's side throughout:

- **Melee** stay close to Ludra, in the strip along the boss-side wall.
- **Ranged** stay in the rows on their side, further from her.

## Hits

- Opposite auras within **5.5 m** of each other hit both players (Estimate).
- The first hit happens on contact, then one more every **0.5 s** while the two stay close (Estimate).
- **5 hits** and the player (or bot) is down. For you, that means the attempt is lost.
- Same-colored players can stand together and never hit each other.

## Open questions

1. Real timings of the orbs, the auras and each flight (frame counts needed).
2. Damage radius and hit rate: is it really 5.5 m, and does it hit once per contact or continuously?
3. Does a player on the wrong side, but not touching the other color, take damage at the end?
4. Do the auras last until the end, or do they drop after some time?
5. How the team really chooses sides after a flight. The trainer uses "least walking", which is a guess.
6. Which corners Ludra really flies to, and whether she ever goes back to the north.

## Sources and method

| Video | Used for |
|---|---|
| [Ludra normal, Spiritmaster POV](https://youtu.be/r76j86Hw15o?t=264) (from 4:24) | The orbs in Ludra's hands, and the start of the aura mechanic |

Everything after the orbs (the auras, the sides, the flights and the hit rules) comes from the player's description and
has not been measured from the video frame by frame yet.
