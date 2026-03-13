# Urchin ZMK Firmware — Claude Code Guide

## Project overview
Custom ZMK firmware for a 34-key Urchin split keyboard (Ferris Sweep variant) with nice!nano v2 and nice!view displays. Uses Colemak-DH with Callum-style one-shot mods.

## Key files
- `config/urchin.keymap` — the keymap (all layers, combos, behaviors)
- `config/urchin.conf` — ZMK config (bluetooth, display, sleep)
- `config/urchin.json` — keyboard layout metadata for ZMK keymap editor
- `build.yaml` — GitHub Actions build matrix
- `config/west.yml` — Zephyr west manifest (ZMK version)
- `ISSUES.md` — user-reported layout annoyances and ideas for discussion

## Layout design principles
- Colemak-DH alpha layout
- Callum-style one-shot mods (`&sk`), NO home row mods, NO timing-dependent hold-taps on finger keys
- Momentary layers on thumb holds (`&mo` / `&lt`), not toggles (`&to`)
- Tri-layer: Nav + Sym → Num (ZMK conditional layer)
- Combos use `require-prior-idle-ms` to prevent misfires during fast typing

## Layers
0. **BASE** — Colemak-DH alphas, mod-morph comma/period
1. **NAV** — left: one-shot mods + clipboard, right: arrows + nav
2. **SYM** — left: symbols, right: mirrored one-shot mods
3. **NUM** — conditional (Nav+Sym), numbers on home row, F-keys
4. **SETTINGS** — bluetooth, bootloader (both left thumbs combo)

## Key position reference
```
 0  1  2  3  4       5  6  7  8  9
10 11 12 13 14      15 16 17 18 19
20 21 22 23 24      25 26 27 28 29
         30 31      32 33
```

## Workflow
- After editing `urchin.keymap`, commit and push to `main`
- GitHub Actions builds firmware automatically
- Download `firmware.zip` from Actions, flash `.uf2` files to each half
- Always update `README.md` layout diagrams when changing the keymap
- User tracks issues in `ISSUES.md` — review these when making changes

## ZMK notes
- ZMK version locked to v0.3.0 (see `config/west.yml`)
- `&sk` configured with `ignore-modifiers` for stacking one-shot mods
- Mod-morph behaviors for comma→semicolon and period→colon on shift
- Hold-tap `bspc_gui` for right outer thumb (tap=Backspace, hold=LGUI)
