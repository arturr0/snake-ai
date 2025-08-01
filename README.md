
# AI Snake Game with Q-Learning

This project implements a classic Snake game with an AI agent that learns to play using **Q-Learning**, a reinforcement learning algorithm. The game features a graphical interface using **SDL** and can be compiled for both native execution and **web deployment via Emscripten**.

---

## Features

- **Q-Learning AI**: The snake learns to navigate the game board, collect food, and avoid obstacles through reinforcement learning.
- **Dynamic Exploration Rate**: The AI balances exploration and exploitation with a decaying exploration rate.
- **Performance Tracking**: Logs and visualizes training progress, including scores, Q-values, and exploration rates.
- **Web-Ready**: When compiled with Emscripten, the game runs in a browser with interactive training charts.
- **Adaptive Difficulty**: The AI adjusts its strategy based on the game state, avoiding traps and optimizing paths.

---

## Requirements

### For Native Build

- C++ compiler with C++11 support  
- SDL2 development libraries  
- CMake (recommended)

### For Web Build

- [Emscripten SDK](https://emscripten.org/docs/getting_started/downloads.html)  
- Node.js (for local testing)

---

## Building and Running

### 🔧 Native Build

```bash
mkdir build
cd build
cmake ..
make
./ai_snake
```

### 🌐 Web Build (via Emscripten)

```bash
mkdir build
cd build
emcmake cmake ..
emmake make
```

This will generate JavaScript and WebAssembly files that can be served via a web server.

---

## Configuration Options

You can adjust the following constants in the source code to modify game behavior:

| Constant                  | Description                                      |
|--------------------------|--------------------------------------------------|
| `WIDTH`, `HEIGHT`        | Game board dimensions                            |
| `CELL_SIZE`              | Pixel size of each game cell                     |
| `AI_UPDATE_INTERVAL`     | How often the AI makes decisions (in frames)     |
| `MAX_TRAINING_EPISODES`  | Total training episodes                          |
| `learning_rate`          | Learning rate for Q-Learning                     |
| `discount_factor`        | Discount factor for future rewards               |
| `exploration_rate`       | Initial exploration probability                  |
| `exploration_decay`      | Decay rate for exploration                       |

---

## 🐳 Docker Support

This project includes Docker support for easy deployment and testing.

### Building the Docker Image

```bash
docker build -t ai_snake .
```

### Running the Container

```bash
docker run -p 8000:8000 ai_snake
```

The web version will be available at: [http://localhost:8000](http://localhost:8000)

---

## 📊 Performance Monitoring

During training, the system logs:

- Episode count  
- Current score  
- Lifetime score  
- Average Q-value  
- Exploration rate

In the web version, these metrics are visualized in real-time using **Chart.js**.

---

## 🧠 Key Algorithms

- **Q-Learning**: Core reinforcement learning algorithm that updates the Q-table based on state transitions and rewards.
- **State Representation**: Combines snake position, direction, food location, and danger detection.
- **Reward Calculation**: Complex reward function considering food proximity, body avoidance, and exploration.
- **Path Safety Check**: Uses BFS to detect and avoid trapped states.


