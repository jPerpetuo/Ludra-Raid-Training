# Ludra Raid Training

A free 3D practice tool for the **"Zikel" mechanic of Ludra**, the boss of the Sanctuary raid in AION 2. Practise the
orange lines, the laser walls and the hard-mode circles with a real third-person camera, at full or reduced speed,
as many times as you like.

> **Unofficial fan project.** Made by players, for players. Not affiliated with, endorsed by or connected to NCSOFT.
> AION is a trademark of NCSOFT. No game files, art or sounds are used: everything you see is drawn with simple
> original shapes.

## How to use it

1. Open [`ludra-raid-training.html`](ludra-raid-training.html) on this page.
2. Click the **Download raw file** button (the download arrow at the top right of the file view).
3. Double-click the downloaded file. It opens in your browser (Chrome, Edge or Firefox).

There is nothing to install. You need an internet connection, because the page loads its 3D library when it opens.

## Controls

| Key | Action |
|---|---|
| `W` `A` `S` `D` | Move (relative to the camera) |
| Mouse | Look around (click the screen to capture the mouse) · wheel zooms |
| `Shift` | Dodge (uses stamina: a full bar is 5 dodges) |
| `R` or `Enter` | Restart |
| `Esc` | Menu |

The menu lets you pick **Normal** or **Hard** mode, slow the fight down to 50% or 75%, change mouse sensitivity, turn
on-screen callouts on or off, and keep playing after a mistake to see everything you missed.

## The mechanic in short

Ludra (north) flies back and four orange lines appear one after another, every 4 seconds, always in the same order.
Stay off a line while it is orange, step onto it once it strikes, and be on it when the rest of the room detonates.
Between lines, a wall of lasers sweeps across the room: stand in a gap. On hard mode, an orange circle also drops under
your feet; be out of it (or perfect dodge) when it fills.

The full breakdown, with every timing and how it was measured, is in
[`ludra-zikel-mechanic.md`](ludra-zikel-mechanic.md). It is written so anyone can build their own trainer from it.

## Open source: use it, share it, improve it

Anyone can use this tool, share it with their static or legion, and improve on it.

- **Found a wrong timing or a missing detail?** Open an issue, ideally with a video link and timestamp.
- **Want to change something?** Fork the repository and send a pull request. All mechanic timings and sizes are in
  the `CFG` block at the top of the script in `ludra-raid-training.html`, so most fixes are a one-line change.
- **Building your own tool?** Take whatever you need, including the mechanic reference.

## Files

| File | What it is |
|---|---|
| `ludra-raid-training.html` | The trainer: one self-contained page |
| `ludra-zikel-mechanic.md` | Mechanic reference: rules, timings, sources, open questions |
| `PROGRESS.md` | Development notes |
| `LICENSE` | MIT license |

## License

[MIT](LICENSE): free to use, change and share, including in your own projects, as long as the license notice stays
with the code.
