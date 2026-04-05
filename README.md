# Robot Path Planner — A* Algorithm Simulation

An interactive, browser-based simulation of the **A\* (A-star) pathfinding algorithm** — the same algorithm used in autonomous robots, drones, and self-driving cars to navigate from a start point to a goal while avoiding obstacles.

![A* Path Planner Demo](https://img.shields.io/badge/algorithm-A%2A-teal) ![HTML](https://img.shields.io/badge/built%20with-HTML%20%2F%20JS-amber) ![No dependencies](https://img.shields.io/badge/dependencies-none-green)

---

## What It Does

The planner visualizes every step of the A\* search in real time:

| Color | Meaning |
|-------|---------|
| 🟩 Green | Robot start position (S) |
| 🟧 Orange | Goal position (G) |
| ⬛ Dark | Wall / obstacle |
| 🟦 Blue | Open set — frontier cells being evaluated |
| 🟪 Purple | Closed set — cells already processed |
| 🟨 Yellow | Final shortest path |

---

## How A\* Works

A\* scores every candidate cell with:

```
f(n) = g(n) + h(n)
```

- **`g(n)`** — actual cost to reach cell `n` from the start
- **`h(n)`** — heuristic estimate of remaining cost to the goal (Manhattan/diagonal distance)
- **`f(n)`** — total estimated cost; the cell with the lowest `f` is always expanded next

By combining real cost with a forward-looking heuristic, A\* is both **complete** (always finds a path if one exists) and **optimal** (always finds the shortest one), while exploring far fewer cells than brute-force approaches like BFS or Dijkstra's.

### Movement & Cost

| Move type | Cost |
|-----------|------|
| Straight (↑ ↓ ← →) | 10 |
| Diagonal (↗ ↘ ↙ ↖) | 14 ≈ 10√2 |

Diagonal moves are blocked if either adjacent straight cell is a wall, preventing the robot from "cutting corners."

---

## Getting Started

No build step, no dependencies, no install required.

### Run locally

```bash
git clone https://github.com/YOUR_USERNAME/robot-path-planner.git
cd robot-path-planner
open index.html        # macOS
start index.html       # Windows
xdg-open index.html    # Linux
```

Or just drag `index.html` into any modern browser.

### Run via live server (optional)

```bash
npx serve .
# → http://localhost:3000
```

---

## Controls

| Control | Description |
|---------|-------------|
| **Draw walls** mode | Click and drag to place obstacles |
| **Set start** mode | Click a cell to move the robot's start |
| **Set goal** mode | Click a cell to move the goal |
| **Erase** mode | Click and drag to remove walls |
| **▶ Run A\*** | Start the pathfinding animation |
| **Clear path** | Remove visualization, keep walls |
| **Reset grid** | Clear everything |
| **Random maze** | Generate a random obstacle field (~30% density) |
| **Size** dropdown | Switch between 15×15, 20×20, and 25×25 grids |
| **Speed** dropdown | Slow / Medium / Fast / Instant |

---

## Project Structure

```
robot-path-planner/
└── index.html      # Self-contained app — all HTML, CSS, and JS in one file
└── README.md
```

---

## Real-World Applications

This algorithm (or close variants of it) powers:

- **Autonomous robots** — warehouse robots (Amazon Kiva), hospital delivery bots
- **Self-driving cars** — local path planning around obstacles
- **Drones** — aerial route planning with obstacle avoidance
- **Video game AI** — NPC navigation in nearly every major game engine
- **GPS/mapping** — turn-by-turn routing (often with weighted road graphs)

---

## Possible Extensions

- **Weighted terrain** — different movement costs for grass, mud, road, etc.
- **Bi-directional A\*** — search from both ends simultaneously for faster results
- **Jump Point Search (JPS)** — a faster variant that skips redundant nodes on open grids
- **3D grid** — extend to a voxel grid for drone path planning
- **Live obstacle avoidance** — add moving obstacles and replan in real time (D\* Lite)

---

## License

MIT — free to use, modify, and distribute.
