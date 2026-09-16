# Game Plan: New Super Mario Ultra Arcade

## Risk Tasks

### 1. Platforming transitions and collision timing
- **Why isolated:** The original prototype only checked top-landings and could feel inconsistent around pits, moving enemies, and jump state handoffs.
- **Approach:** Use a fixed-size canvas world with explicit player velocity, gravity, coyote time, grounded state, top-surface collision checks, enemy stomp detection, pit recovery, and a smoothed camera.
- **Verify:** Walking off a platform, jumping, landing, stomping an enemy, falling into a pit, and respawning all produce a deterministic and readable response without sticking or tunneling.

### 2. Audio unlock and feedback timing
- **Why isolated:** Browser audio requires a user gesture and must not block the game when unavailable.
- **Approach:** Lazily create a WebAudio context on the first start/input, synthesize short jump/coin/stomp/hit/goal/win cues, and expose a mute toggle plus keyboard shortcut.
- **Verify:** Starting the game unlocks sound, each major action has a distinct cue, mute is immediate, and the game remains playable when audio is suspended or unavailable.

### 3. Victory presentation
- **Why isolated:** The finish state needs a real state transition plus a readable celebratory presentation instead of simply stopping the update loop.
- **Approach:** Mark the goal once, award a completion bonus, trigger particles and a goal cue, then show a victory card with the generated princess cutout using a looping dance animation and score breakdown.
- **Verify:** Reaching the star gate exactly once opens the victory overlay, the princess visibly dances, the final score is displayed, and a new run resets the stage cleanly.

## Main Build

- **Assets needed:** Generated 16:9 visual direction reference for the start card; generated transparent princess cutout for the victory card. Gameplay actors, platforms, collectibles, enemies, particles, sky, and UI are rendered with deterministic canvas/CSS art so the runtime stays lightweight.
- **Visual direction:** High-energy Gen Z arcade palette with midnight navy, electric cyan, hot pink, gold, glassmorphism HUD, glowing platform trims, readable silhouettes, and layered parallax scenery.
- **Gameplay:** One complete horizontal stage with platforms, pits, six patrolling enemies, mystery boxes, 27 coins, a goal flag, combo scoring, lives, respawn, progress meter, and stage clear flow.
- **Controls:** Arrow keys or A/D to move; Space, W, or Arrow Up to jump; M to mute; touch controls on small screens.
- **Verify:**
  - HUD is readable and remains synchronized with score, coins, combo, lives, and progress.
  - Character animation, enemy motion, coin bob/spin, particle bursts, camera follow, and goal pulse are visible.
  - No missing images, clipped overlays, or console errors during browser capture.
  - Start, play, game-over, reset, and victory flows all work.
  - `?demo` deterministically starts an autopilot run for visual verification.
  - Reference consistency: neon arcade palette, layered scenic depth, glowing surfaces, and premium game UI hierarchy.
