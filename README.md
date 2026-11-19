# Ludra Raid Training (fork)

A free 3D practice tool for **Ludra**, the boss of the Sanctuary raid in AION 2. Practice three of her mechanics with a
real third-person camera, at full or reduced speed, as many times as you like:

- **Zikel:** the orange lines, the laser walls and the hard-mode circles.
- **Bingo board** (phase 1): sweep the board with 9 bot teammates, find the safe square, dodge Ludra's two breaths and
  get inside before the meteor lands.
- **Colors:** Ludra's blue and red orbs. Everyone gets a blue or red aura and must split up by color without standing
  close to the other color. Ludra flies between corners, so the team has to regroup each time.

**Original trainer:** made by **mtkです [Siel] · South America**.
**This fork:** by **Kalard [Marchutan]**, adding the Colors mechanic, the Portuguese language and the demo GIFs.

## ▶ [Play it in your browser](https://jperpetuo.github.io/Ludra-Raid-Training/)

Nothing to download and no account needed. Use a computer with a keyboard and mouse, in Chrome, Edge or Firefox.

> **Unofficial fan project.** Made by players, for players. Not affiliated with, endorsed by or connected to NCSOFT.
> AION is a trademark of NCSOFT. No game files, art or sounds are used: everything you see is drawn with simple
> original shapes.

## Language

Click the flags in the top-right corner to switch between Portuguese (🇧🇷, the default) and English (🇺🇸). The inactive
flag is shown in grey. Your choice is saved in the browser.

## Demos

Each mechanic card in the menu shows a short demo, captured from the simulator itself:

| Mechanic | Demo |
|---|---|
| Zikel | [`docs/demo/zikel.gif`](docs/demo/zikel.gif): step onto the line after the strike, then dodge the laser wall |
| Bingo board | [`docs/demo/bingo.gif`](docs/demo/bingo.gif): the circles follow the team and snap onto the board |
| Colors | [`docs/demo/colors.gif`](docs/demo/colors.gif): auras are given and the team splits by color |

## Want your own copy? (optional)

You don't need this to play: the link above is enough. To keep the trainer on your computer, download
`ludra-raid-training.html` (the only file you need) from this repository and double-click it. You need an internet
connection while playing, because the page loads its 3D library when it opens.

## Controls

| Key | Action |
|---|---|
| `W` `A` `S` `D` | Move (relative to the camera) |
| Mouse | Look around (click the screen to capture the mouse) · wheel zooms |
| `Shift` | Dodge (uses stamina: a full bar is 5 dodges) |
| `Space` | Jump (Bingo board: jump into your orb) |
| `R` or `Enter` | Restart |
| `Esc` | Menu |

The menu lets you pick the mechanic (tabs at the top), **Normal** or **Hard** mode for Zikel, the **Strategy** for Colors
(Fixed or Adaptive), slow the fight down to 50% or 75%, change mouse sensitivity, turn on-screen callouts on or off, and
keep playing after a mistake to see everything you missed.

## The mechanics in short

**Zikel.** Ludra (north) flies back and four orange lines appear one after another, every 4 seconds, always in the same
order. Stay off a line while it is orange, step onto it once it strikes, and be on it when the rest of the room
detonates. Between lines, a wall of lasers sweeps across the room: stand in a gap. On hard mode, an orange circle also
drops under your feet; be out of it (or perfect dodge) when it fills.

**Bingo board.** A 6 × 6 board appears and a circle follows every player four times; each one fills the square it lands
on. Pick your corner and role (outside, inside, or center for the orbs) and sweep your squares with the team until
someone finds the hidden safe square, then everyone runs inside it: it makes you immune. Twice, Ludra flies to a corner
and breathes across the board along the diagonal; hold the far corner of your square or wait at the edge. When "Ludra's
Trial" ends, a meteor kills everyone outside the safe square.

**Colors.** Ludra holds a blue orb in her left hand and a red one in her right. Everyone gets a random aura: blue or red
(five of each). Opposite auras that get too close hit each other: after 5 hits you're down. Each color keeps to one side
of the room, as seen by the players facing Ludra. Ludra starts in the north and then flies, twice, to a random corner
(never the opposite one). Fixed strategy: blue always takes the left. Adaptive strategy: after each flight, the team picks
the sides that need the least walking. Your teammates are bots: five melee stay near Ludra, the other four spread
across the room.

The full breakdowns, with every timing and how it was measured, are in
[`ludra-zikel-mechanic.md`](ludra-zikel-mechanic.md), [`ludra-bingo-mechanic.md`](ludra-bingo-mechanic.md) and
[`ludra-colors-mechanic.md`](ludra-colors-mechanic.md). They are written so anyone can build their own trainer from them.

## Open source: use it, share it, improve it

Anyone can use this tool, share it with their static or legion, and improve on it.

- **Found a wrong timing or a missing detail?** Open an issue, ideally with a video link and timestamp.
- **Want to change something?** Fork the repository and send a pull request. The mechanic timings and sizes are in the
  `CFG` block at the top of the script in `ludra-raid-training.html`, so most fixes are a one-line change.
- **Building your own tool?** Take whatever you need, including the mechanic reference.

## Files

| File | What it is |
|---|---|
| `ludra-raid-training.html` | The trainer: one self-contained page |
| `ludra-zikel-mechanic.md` | Zikel reference: rules, timings, sources, open questions |
| `ludra-bingo-mechanic.md` | Bingo board reference: rules, timings, the common solve, open questions |
| `ludra-colors-mechanic.md` | Colors reference: auras, flights, strategies, open questions |
| `PROGRESS.md` | Development notes |
| `index.html` | Sends the website address straight to the trainer |
| `docs/` | Images and demo GIFs used by this README and the menu |
| `LICENSE` | MIT license |

## Credits

Original trainer by **mtkです** of the **[Siel]** server (South America), with mechanic timings checked frame by frame
against raid videos. The nine teammates in the Bingo board and Colors trainers are named after Kalard's friends, drawn at random every run.

Fork by **Kalard** of the **[Marchutan]** server.

## License

[MIT](LICENSE): free to use, change and share, including in your own projects, as long as the license notice stays
with the code.
