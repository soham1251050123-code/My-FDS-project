# CubeDS — Rubik's Cube Solver & Fundamental Data Structures Visualizer

An interactive academic software application bridging abstract data structures with physical 3D kinematics. Designed for students and computer science courses (EBDT / FDS Lab).

---

## Overview

CubeDS visualizes how fundamental computer science data structures synchronize in real time to model, track, and solve a 3D Rubik's Cube:

1. **3D Multi-Dimensional Array (`cubeArray[6][3][3]`):**
   - Serves as the single authoritative source of truth.
   - Maps 54 discrete facelets across six faces (Up, Right, Front, Down, Left, Back).
   - Visualized via an unfolded 2D Net Projection and a Memory Tensor Table.

2. **LIFO Move Stack:**
   - Records completed move vectors with an explicit `TOP` pointer.
   - Provides instant **Undo** capability by popping the top move and executing its mathematical inverse ($M \circ M' = I$).

3. **FIFO Solving Queue:**
   - Buffers pre-calculated solution moves with explicit `FRONT` and `REAR` pointers.
   - Dispatches moves in deterministic order with real-time completion progress tracking.

4. **Authentic Solving Engine (Herbert Kociemba 2-Phase Algorithm):**
   - Calculates true group-theoretic solutions ($\le 22$ moves) for any valid scramble.
   - Pre-calculates the complete sequence prior to animation.

5. **Two Solving Modes:**
   - **Auto Solve:** Sequentially animates all solution moves with pause/resume controls.
   - **Step-by-Step Solve:** Executes exactly one move per click, enabling inspection of each intermediate data structure state.

6. **Physical 3D Kinematics (Three.js WebGL):**
   - 27 individual cubies with smooth cubic easing and move locking to prevent concurrency glitches.
   - Complete Singmaster manual face rotation keypad ($U, D, L, R, F, B$, inverses, and $180^\circ$ turns).

---

## Practical Applications

- **Image Scrambling & Reconstruction (Encoding/Decoding):** Partitioning visual data into blocks and applying reversible permutation sequences.
- **Data Transformation Visualization:** Tracking multi-step data mutations and state restoration.
- **Educational Demonstration:** Hands-on visual learning for permutations, reversible operations, and step-by-step algorithms.

---

## Project Structure

```
├── index.html                     # Main application entry point
├── favicon.svg                    # Application vector icon
├── css/
│   └── styles.css                 # Minimalistic academic styling
├── js/
│   ├── app.js                     # Global coordinator & view router
│   ├── welcome.js                 # Welcome page 3D experience
│   ├── dashboard.js               # Main dashboard studio controller
│   ├── core/
│   │   ├── CubeModel.js           # 3D Array [6][3][3] & move logic
│   │   ├── MoveStack.js           # LIFO Stack with TOP pointer
│   │   ├── MoveQueue.js           # FIFO Queue with FRONT/REAR pointers
│   │   └── SolverEngine.js        # Kociemba 2-phase algorithm adapter
│   └── components/
│       ├── ThreeCubeEngine.js     # 3D WebGL Three.js cube kinematics
│       ├── ArrayVisualizer.js     # Net projection & tensor table
│       ├── StackQueueVisualizer.js# Live pointer & track inspector
│       └── ApplicationsModal.js   # Real-world applications slide deck
└── lib/
    ├── three.min.js               # Three.js 3D library (local/offline)
    ├── OrbitControls.js           # Three.js camera controller
    ├── cube.js                    # Cube state model
    └── solve.js                   # Two-phase solving algorithm
```

---

## Getting Started

### Prerequisites
- Python 3.x (or any static HTTP server)
- Modern web browser (Chrome, Edge, Firefox, Safari)

### Running Locally
1. Clone the repository:
   ```bash
   git clone <repository-url>
   cd FDSKAPROJECT
   ```

2. Start the local server:
   ```bash
   python -m http.server 3000
   ```

3. Open your browser and navigate to:
   ```
   http://localhost:3000
   ```
