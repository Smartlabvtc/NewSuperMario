# Structure: New Super Mario Ultra Arcade

This repository intentionally remains a dependency-free static browser game. `index.html` is the host, UI shell, CSS system, and canvas runtime so it can be opened directly or served by any static host.

| Area | Ownership |
|---|---|
| HTML shell | Header, HUD, canvas frame, overlays, responsive mobile controls |
| CSS visual system | Neon palette, glassmorphism panels, responsive layout, buttons, victory animation |
| Canvas runtime | `state`, `player`, `world`, `goal`, update loop, rendering, collision, particles |
| Audio | Lazy WebAudio context, synthesized SFX, short procedural loop, mute control |
| Generated art | `art-direction-reference.png` on the start card; `princess.png` on the victory card |
| Documentation | `PLAN.md`, `STRUCTURE.md`, `MEMORY.md`, `ASSETS.md` |

## Runtime contract

- Canvas internal resolution is 960×540 and scales responsively with a 16:9 aspect ratio.
- `requestAnimationFrame` drives `update(dt)` and `draw()`.
- Gameplay is framework-independent and has no React coupling.
- Audio is created only after a gesture or explicit start action to respect browser autoplay policy.
- `?demo` starts an autopilot mode for deterministic visual QA.

## Important state transitions

`START → PLAYING → VICTORY` and `PLAYING → GAMEOVER`. Reset returns to `START`. The goal transition is guarded by `goal.reached` so completion scoring cannot repeat.
