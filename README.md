# Flappy Bird Clone (Unity)

A simple, fully playable Flappy Bird clone built in Unity using C#. This project recreates the classic side-scrolling gameplay loop — a bird that flaps against gravity, dodging procedurally spawned pipes while the score increases over time.



## Features

- Physics-based player controller with gravity, jump input, and tilt animation
- Procedural pipe spawning with randomized heights and configurable gap size
- Scrolling parallax background for a continuous side-scrolling effect
- Trigger-based collision detection for scoring and game-over events
- Centralized game state management (Play / Pause / Game Over) via a singleton GameManager
- UI score display, Play button, and Game Over screen

## Tech Stack

- **Engine:** Unity (2D)
- **Language:** C#
- **Rendering:** Sprite Renderer, UI (uGUI)

## Project Structure

```
Assets/
├── Scripts/
│   ├── GameManager.cs   # Singleton controlling game state, score, and UI
│   ├── Player.cs         # Bird movement, gravity, input, sprite animation
│   ├── Pipes.cs           # Pipe movement, gap setup, and destruction
│   ├── Spawner.cs        # Spawns pipe prefabs at randomized heights
│   └── Parallax.cs        # Scrolling background effect
├── Prefabs/
│   └── Pipes.prefab     # Pipe pair prefab with collider and tags
├── Sprites/
└── Scenes/
```

## How It Works

- **GameManager** is a singleton that controls the overall game state. On `Play()`, it resets the score, resumes time scale, clears existing pipes, and enables the Player and Spawner. On `GameOver()` / `Pause()`, it stops time, disables player input, and stops pipe spawning.
- **Spawner** uses `InvokeRepeating` to instantiate a new `Pipes` prefab at a random vertical offset at a fixed interval. It is enabled/disabled by the GameManager so pipes only spawn during active gameplay.
- **Pipes** moves left at a constant speed and destroys itself once off-screen. It also positions its top and bottom segments based on a configurable gap.
- **Player** applies gravity each frame, jumps on Space/Click, animates its sprite, and tilts based on velocity. Collisions are detected via `OnTriggerEnter2D` using `"Obstacle"` and `"Scoring"` tags.
- **Parallax** continuously offsets the background texture to create a scrolling effect.

## Getting Started

1. Clone the repository:
   ```bash
   git clone https://github.com/abhiruppauliitkgp/Flappy-Bird-Game-Unity.git
   ```
2. Open the project in **Unity Hub** (tested on Unity 2021.3 LTS or later, 2D template).
3. Open the main scene from `Assets/Scenes/`.
4. Press **Play** in the Editor, then click the **Play** button in-game to start.

## Controls

| Action | Input |
|---|---|
| Jump / Flap | `Spacebar` or `Left Mouse Click` |
| Start Game | Click **Play** button |
| Retry | Click **Play** button after Game Over |

## Credits

- Sprites and assets sourced from free Flappy Bird-style asset packs (replace with your actual source/credits).
- Built as a learning project to practice Unity fundamentals: state management, prefabs, physics, and UI.
