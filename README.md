# AI Search Agent – Pacman 🟡👻

Search algorithms implemented for the classic **UC Berkeley Pacman AI** project (search module).  
The agent navigates mazes to reach food, visit corners, and clear all dots using both **uninformed** and **informed** search.

> Project report/details: see `Search_Agent_for_Pacman.pdf`. :contentReference[oaicite:0]{index=0}

---

## ✅ What’s implemented

### Uninformed search
- **DFS (Depth-First Search)** – explores deep paths first (not optimal).
- **BFS (Breadth-First Search)** – explores level by level (optimal in unweighted graphs).

### Cost-based / informed search
- **UCS (Uniform Cost Search)** – chooses the path with minimum accumulated cost `g(n)`.
- **A\*** – uses `f(n) = g(n) + h(n)` for fast optimal solutions (with admissible heuristics).

### Advanced tasks (Pacman Search)
- **CornersProblem**: state = `((x, y), (c1, c2, c3, c4))` to track visited corners.
- **cornersHeuristic**: admissible heuristic based on Manhattan distance to remaining corners (max distance).
- **FoodSearchProblem + foodHeuristic**:
  - heuristic = `max( distance(pacman, farthestFood), diameter(foodSet) )`
  - uses caching via `problem.heuristicInfo` to avoid recomputing maze distances.
- **Suboptimal / Greedy**:
  - **ClosestDotSearchAgent**: repeatedly goes to the nearest food using BFS (fast, not globally optimal).

All tasks were completed and passed the autograder with max score. :contentReference[oaicite:1]{index=1}

---

## 📁 Project structure (typical)
- `search.py` – implementations for DFS/BFS/UCS/A* and heuristics
- `searchAgents.py` – Pacman agents + problem definitions (Corners/Food/etc.)
- `pacman.py`, `game.py`, `util.py` – framework (from Berkeley starter code)
- `layouts/` – map layouts
- `autograder.py` – grading script

> Exact filenames can vary depending on the starter package, but the logic above matches the implementation described in the report. :contentReference[oaicite:2]{index=2}

---

## ▶️ How to run

### Requirements
- Python (usually **Python 3.x**)
- The Berkeley Pacman project files included in the repo

### Example commands
Run Pacman with a search agent (examples):
```bash
python pacman.py -l tinyMaze -p SearchAgent -a fn=depthFirstSearch
python pacman.py -l mediumMaze -p SearchAgent -a fn=breadthFirstSearch
python pacman.py -l mediumMaze -p SearchAgent -a fn=uniformCostSearch
python pacman.py -l mediumMaze -p SearchAgent -a fn=aStarSearch,heuristic=manhattanHeuristic
