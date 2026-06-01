<p align="center">
  <img src="https://avatars.githubusercontent.com/u/271126266?s=200&v=4" width="100" height="100" alt="BitRoboticsLab Logo"/>
</p>

<h1 align="center">BitRoboticsLab</h1>
<p align="center"><strong>Open-source legged locomotion stack — planning & control, training & deployment, hands-on tutorials</strong></p>

<p align="center">
  <a href="https://github.com/bitroboticslab/AStarFootstepPlanner"><img src="https://img.shields.io/badge/Language-C%2B%2B-blue?logo=cplusplus" alt="C++"></a>
  <a href="https://github.com/bitroboticslab/robot-motion-player"><img src="https://img.shields.io/badge/Language-Python-3776AB?logo=python&logoColor=white" alt="Python"></a>
  <a href="https://github.com/bitroboticslab/Coppeliasim-Tutorials-for-Beginners"><img src="https://img.shields.io/badge/Language-MATLAB-orange" alt="MATLAB"></a>
  <img src="https://img.shields.io/badge/License-Apache%202.0-green" alt="License">
  <img src="https://img.shields.io/badge/Platform-Linux%20%7C%20macOS%20%7C%20Windows-lightgrey" alt="Platform">
</p>

---

## 🔭 Overview

**BitRoboticsLab** builds an open-source research stack for **legged robot locomotion** — covering the full pipeline from footstep planning and geometric computation to RL-based control, training, and deployment.

Our libraries are **modular, well-documented, and cross-platform** (C++/Python), designed for researchers and engineers working on humanoid and quadruped robot motion.

```
         Planning & Control                Training & Deployment
    ┌──────────────────────────┐      ┌──────────────────────────┐
    │  AStarFootstepPlanner ⭐6│      │  rsl-rl-ex          (WIP)│
    │  Footstep planning (A*)  │      │  RL for legged robots    │
    │                          │      │                          │
    │  Heuclid ⭐3             │      │  leggedlabultra     (WIP)│
    │  Geometry primitives     │      │  Legged robot framework  │
    │                          │      │                          │
    │  robot-motion-player ⭐3 │      │  boosterdeploy      (WIP)│
    │  Motion data analysis    │      │  Sim-to-deploy pipeline  │
    └──────────────────────────┘      └──────────────────────────┘

                   Hands-on Tutorials
              ┌──────────────────────────┐
              │  Coppeliasim-Tutorials ⭐2│
              │  Simulation education     │
              │                          │
              │  OpenClaw-Guide      ⭐9  │
              │  AI agent deployment      │
              └──────────────────────────┘
```

---

## 📦 Projects

| Project | Description | Language | Stars |
|---------|-------------|----------|-------|
| [**AStarFootstepPlanner**](https://github.com/bitroboticslab/AStarFootstepPlanner) | C++ implementation of A* graph search for humanoid footstep planning — kinematic constraints, obstacle avoidance, stepping stones, IHMC reimplementation | C++ | ⭐ 6 |
| [**Heuclid**](https://github.com/bitroboticslab/Heuclid) | Lightweight C++ Euclidean geometry library — 2D/3D primitives, convex hull (Graham scan), polygon intersection (SAT), Bézier curves, built on Eigen | C++ | ⭐ 3 |
| [**robot-motion-player**](https://github.com/bitroboticslab/robot-motion-player) | Python CLI/GUI for robot motion datasets — MuJoCo playback, IK tuning, AMP quality metrics, keyframe editing, GIF/video export | Python | ⭐ 3 |
| [**Coppeliasim-Tutorials-for-Beginners**](https://github.com/bitroboticslab/Coppeliasim-Tutorials-for-Beginners) | Bilingual (EN/CN) robotics simulation teaching kit — 6-hour curriculum with slides, models, and code, battle-tested at BIT | MATLAB | ⭐ 2 |
| [**OpenClaw-Guide-for-Beginners**](https://github.com/bitroboticslab/OpenClaw-Guide-for-Beginners) | Chinese deployment guide for OpenClaw AI agent gateway — platform setup, API config, 10+ messaging platform integration | Shell | ⭐ 9 |

> 🚧 **Coming soon:** `rsl-rl-ex`, `leggedlabultra`, `boosterdeploy` — RL-based legged locomotion control, training, and deployment frameworks.

---

## 🏗️ Architecture

### C++ Footstep Planning Stack

```
┌─────────────────────────────────────────────────────────┐
│              AStarFootstepPlanner (v2.0)                 │
│     A* footstep planner for humanoid robots              │
│     Kinematic constraints · Obstacle avoidance           │
│     Stepping stones · Body path guidance                 │
├──────────┬──────────────┬───────────────────────────────┤
│  LBlocks │ matplotlib_  │  jrl-cmakemodules             │
│  (modular│  cpp         │  (build system)               │
│   blocks)│  (optional)  │                               │
├──────────┴──────────────┴───────────────────────────────┤
│                    Heuclid (v2.4+)                        │
│     2D/3D geometry · Convex polygons · Quaternions       │
│     Pose · Bézier curves · Spatial queries               │
├─────────────────────────────────────────────────────────┤
│                    Eigen3 (3.4.0)                         │
│                    Linear algebra                         │
└─────────────────────────────────────────────────────────┘
```

### Python Motion Analysis Tool

```
┌─────────────────────────────────────────────────────────┐
│              robot-motion-player (v0.8.0)                 │
│     AMP motion dataset visualizer & editor               │
│     Playback · IK Tuning · Metrics · Export              │
├──────────┬──────────┬──────────┬────────────────────────┤
│  numpy   │  scipy   │  pyyaml  │  rich                  │
├──────────┴──────────┴──────────┴────────────────────────┤
│  Optional:                                               │
│  mujoco (playback) · pinocchio (IK) · dearpygui (GUI)  │
│  imageio (video export)                                  │
└─────────────────────────────────────────────────────────┘
```

> **Note:** AStarFootstepPlanner and robot-motion-player are **independent projects** in the same research domain. They share no compile-time or runtime dependencies, but complement each other in a typical research workflow: plan footstep sequences → visualize and validate motion data → train locomotion policies.

---

## 🛠️ Tech Stack

- **Languages:** C++11/14/17, Python 3.9+, MATLAB
- **Build System:** CMake 3.22+ with auto-fetched dependencies
- **Testing:** GoogleTest (C++), pytest (Python)
- **Documentation:** Doxygen API docs, bilingual Markdown (EN/CN)
- **CI/CD:** GitHub Actions
- **License:** Apache License 2.0

---

## 🚀 Getting Started

### C++ Projects (AStarFootstepPlanner / Heuclid)

```bash
git clone https://github.com/bitroboticslab/AStarFootstepPlanner.git
cd AStarFootstepPlanner
mkdir build && cd build
cmake ..
cmake --build .
ctest
```

All C++ dependencies (Heuclid, Eigen3, jrl-cmakemodules) are **auto-fetched** on first configure.

### Python Project (robot-motion-player)

```bash
pip install git+https://github.com/bitroboticslab/robot-motion-player.git
# With optional dependencies:
pip install "git+https://github.com/bitroboticslab/robot-motion-player.git[all]"
```

---

## 🤝 Contributing

We welcome contributions! Each project has its own `CONTRIBUTING.md` with guidelines. In general:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/my-feature`)
3. Commit with clear messages (`feat: add new feature`)
4. Open a Pull Request

---

## 📫 Contact

- **GitHub:** [@Mr-tooth](https://github.com/Mr-tooth)
- **Organization:** [bitroboticslab](https://github.com/bitroboticslab)

---

<p align="center">
  <sub>Built with ❤️ for the robotics research community</sub>
</p>
