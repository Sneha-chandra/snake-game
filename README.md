# Snake Game

A classic Snake game built with **vanilla JavaScript and HTML5 Canvas API** — no libraries, no frameworks, no build step. Runs entirely in the browser.

## Live Demo

[Play Now](https://sneha-chandra.github.io/snake-game) &nbsp;·&nbsp; [GitHub](https://github.com/Sneha-chandra/snake-game)

---

## Architecture

```
┌─────────────────────────────────────────────────────┐
│                    Browser Runtime                   │
│                                                      │
│   ┌──────────────┐    ┌──────────────────────────┐  │
│   │ Input Layer  │    │      Game State Engine    │  │
│   │              │    │                          │  │
│   │ Keyboard     │───▶│  Snake (Array<{x,y}>)    │  │
│   │ Arrow Keys   │    │  Food {x, y}             │  │
│   │ Touch Swipe  │    │  Score / High Score      │  │
│   │ (Mobile)     │    │  Direction Lock          │  │
│   └──────────────┘    │  Game State (PLAYING /   │  │
│                        │    PAUSED / GAME_OVER)  │  │
│   ┌──────────────┐    └──────────────┬───────────┘  │
│   │ Game Loop    │◀── setInterval()  │              │
│   │ (Tick Rate)  │                   ▼              │
│   │ Slow: 130ms  │    ┌──────────────────────────┐  │
│   │ Normal: 80ms │    │   Canvas 2D Renderer     │  │
│   │ Fast:  45ms  │───▶│                          │  │
│   └──────────────┘    │  Grid: 21×21 cells       │  │
│                        │  CELL_SIZE = 20px        │  │
│   ┌──────────────┐    │  roundRect() snake body  │  │
│   │ Persistence  │    │  arc() food + snake eye  │  │
│   │ localStorage │    │  fillText() score/UI     │  │
│   │ High Score   │    └──────────────────────────┘  │
│   └──────────────┘                                   │
└─────────────────────────────────────────────────────┘
```

---

## Project File Structure

```
snake-game/
├── index.html          # Complete game — HTML structure, CSS styles, and JS game logic
└── README.md
```

> Single-file architecture: everything lives in `index.html` for zero-dependency deployment.

---

## Technical Knowledge Implemented

### HTML5 / Canvas API
| Concept | Application |
|---|---|
| `<canvas>` element | 420×420px game board |
| `CanvasRenderingContext2D` | 2D drawing context for all rendering |
| `fillRect()` | Grid cells, background |
| `roundRect()` | Rounded snake body segments |
| `arc()` | Circular food, snake eye animation |
| `fillText()` | Overlay messages (Game Over, Pause) |
| `clearRect()` | Frame clear before each redraw |

### JavaScript Game Engine Concepts
| Concept | Details |
|---|---|
| **Game Loop** | `setInterval()` with configurable tick rate (130 / 80 / 45 ms) |
| **State Machine** | Three states: `PLAYING`, `PAUSED`, `GAME_OVER` |
| **Linked-List Movement** | Snake body as `Array<{x,y}>` — unshift new head, pop tail |
| **Collision Detection** | Self-collision (head vs body array scan); wall = wrap-around |
| **Direction Lock** | Prevents 180° reversal; buffered input queue |
| **Random Placement** | Food placed at random empty cell (excludes snake body) |
| **Touch Gesture** | `touchstart` + `touchend` delta to detect swipe direction |
| **Web Storage API** | `localStorage.getItem/setItem` for high score persistence |

### CSS3 Techniques
| Concept | Application |
|---|---|
| CSS Variables | `--green`, `--dark`, `--accent` color tokens |
| Flexbox | Centered layout, control button row |
| Box Shadow | Neon glow effect on canvas and buttons |
| `border-radius` | Card UI for score panel |
| Gradient | Radial gradient background |

---

## Game Mechanics Reference

| Feature | Behavior |
|---|---|
| Grid Size | 21 × 21 cells, each 20×20 px → 420×420 px canvas |
| Starting State | Snake length 3, moving right, center of grid |
| Wall Behavior | Wrap-around (exits right → enters left, etc.) |
| Food Respawn | Immediately after eating, random empty cell |
| Scoring | +10 points per food eaten |
| Speed Levels | Slow / Normal / Fast via button; changes `setInterval` delay |
| High Score | Persisted in `localStorage`; survives page refresh |
| Eye Animation | Right eye drawn on head segment based on current direction |

---

## How to Run

```bash
# Option 1 — Open directly
open index.html

# Option 2 — Local server (recommended for localStorage)
python3 -m http.server 8080
# → http://localhost:8080
```

---

## Controls

| Input | Action |
|---|---|
| Arrow Keys | Change direction |
| `P` | Pause / Resume |
| `R` | Restart after Game Over |
| Swipe (Mobile) | Change direction |
| Speed Buttons | Toggle Slow / Normal / Fast |

---

## Skills Demonstrated

`HTML5 Canvas API` · `Vanilla JavaScript (ES6+)` · `Game Loop Design` · `State Machine Pattern` · `Collision Detection` · `Touch/Swipe Events` · `CSS3 Animations` · `Web Storage API` · `Responsive Design`
