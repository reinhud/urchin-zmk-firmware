# Urchin ZMK Firmware

Custom ZMK firmware for the [Urchin keyboard](https://github.com/duckyb/urchin) (34-key Ferris Sweep variant) with nice!nano v2 controllers and nice!view displays.

## Layout: Colemak-DH

Callum-style one-shot mods — no home row mods, no timing-dependent hold-taps on finger keys. Layers activated via thumb holds (`&mo`), with a tri-layer (Nav + Sym → Num) via ZMK conditional layers.

### Base Layer (Colemak-DH)
```
┌─────┬─────┬─────┬─────┬─────┐   ┌─────┬─────┬─────┬─────┬─────┐
│  Q  │  W  │  F  │  P  │  B  │   │  J  │  L  │  U  │  Y  │  '  │
├─────┼─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┼─────┤
│  A  │  R  │  S  │  T  │  G  │   │  M  │  N  │  E  │  I  │  O  │
├─────┼─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┼─────┤
│  Z  │  X  │  C  │  D  │  V  │   │  K  │  H  │ , ; │ . : │  /  │
└─────┴─────┴──┬──┴──┬──┴─────┘   └─────┴──┬──┴──┬──┴─────┴─────┘
               │ SPC │Nav/Ent│       │Sym/Tab│Bk/⌘ │
               └─────┴──────┘       └──────┴─────┘
```
- `,` shifts to `;` · `.` shifts to `:` (mod-morph)
- W+F combo → Escape · N+E combo → CapsWord

### Nav Layer (hold left inner thumb)
```
┌─────┬─────┬─────┬─────┬─────┐   ┌─────┬─────┬─────┬─────┬─────┐
│     │Redo │Undo │ Tab │     │   │ Ins │Home │  ↑  │ End │PgUp │
├─────┼─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┼─────┤
│ ⌘°  │Alt° │Ctrl°│Shft°│     │   │CapsW│  ←  │  ↓  │  →  │PgDn │
├─────┼─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┼─────┤
│     │ Cut │Copy │Paste│     │   │     │ W←  │Enter│ W→  │ Esc │
└─────┴─────┴──┬──┴──┬──┴─────┘   └─────┴──┬──┴──┬──┴─────┴─────┘
               │ SPC │▓▓▓▓▓▓│       │Sym/Tab│Bk/⌘ │
               └─────┴──────┘       └──────┴─────┘
```
`°` = one-shot (sticky) modifier

### Sym Layer (hold right inner thumb)
```
┌─────┬─────┬─────┬─────┬─────┐   ┌─────┬─────┬─────┬─────┬─────┐
│  !  │  @  │  #  │  $  │  %  │   │  ^  │  &  │  *  │  -  │  +  │
├─────┼─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┼─────┤
│  {  │  (  │  )  │  }  │  `  │   │     │Shft°│Ctrl°│Alt° │ ⌘°  │
├─────┼─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┼─────┤
│  ~  │  [  │  ]  │  |  │  \  │   │     │  =  │  <  │  >  │     │
└─────┴─────┴──┬──┴──┬──┴─────┘   └─────┴──┬──┴──┬──┴─────┴─────┘
               │ SPC │Nav/Ent│       │▓▓▓▓▓▓│Bk/⌘ │
               └─────┴──────┘       └──────┴─────┘
```

### Num Layer (Nav + Sym held = tri-layer)
```
┌─────┬─────┬─────┬─────┬─────┐   ┌─────┬─────┬─────┬─────┬─────┐
│ F1  │ F2  │ F3  │ F4  │ F5  │   │ F11 │  -  │  +  │  *  │ F12 │
├─────┼─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┼─────┤
│  1  │  2  │  3  │  4  │  5  │   │  6  │  7  │  8  │  9  │  0  │
├─────┼─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┼─────┤
│ F6  │ F7  │ F8  │ F9  │ F10 │   │     │  =  │  ,  │  .  │  /  │
└─────┴─────┴──┬──┴──┬──┴─────┘   └─────┴──┬──┴──┬──┴─────┴─────┘
               │ SPC │▓▓▓▓▓▓│       │▓▓▓▓▓▓│Bk/⌘ │
               └─────┴──────┘       └──────┴─────┘
```

### Settings Layer (both left thumbs combo)
Bluetooth profile selection, bootloader, ZMK Studio unlock.

## Combos
| Keys | Action | Guard |
|------|--------|-------|
| W + F (pos 1+2) | Escape | require-prior-idle 150ms |
| N + E (pos 16+17) | CapsWord | require-prior-idle 150ms |
| Left thumbs (pos 30+31) | Settings layer | — |

## Building
Push to `main` triggers GitHub Actions. Download `firmware.zip` from the completed run.

## Flashing
1. Double-tap reset on the nice!nano to enter bootloader (USB mass storage appears)
2. Copy the matching `.uf2` file onto the drive
3. It flashes and reboots automatically
4. Repeat for the other half

**OS keyboard layout must be set to US.**
