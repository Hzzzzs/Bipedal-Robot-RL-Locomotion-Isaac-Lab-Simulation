# Bipedal Robot RL Locomotion: Isaac Lab Simulation

[![IsaacSim](https://img.shields.io/badge/IsaacSim-4.5.0-silver.svg)](https://docs.omniverse.nvidia.com/isaacsim/latest/overview.html)
[![Isaac Lab](https://img.shields.io/badge/IsaacLab-2.1.0-silver)](https://isaac-sim.github.io/IsaacLab)
[![Python](https://img.shields.io/badge/python-3.10-blue.svg)](https://docs.python.org/3/whatsnew/3.10.html)
[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)

## 📖 Overview

This repository contains the training and simulation framework for a point-foot bipedal robot (inspired by platforms like the [limxdynamics TRON1](https://www.limxdynamics.com/en/tron1)). Built on top of **NVIDIA Isaac Lab**, this project leverages GPU-accelerated massive parallel simulation to train robust reinforcement learning (RL) policies for versatile locomotion across various environments.

# You can find the test videos and GIFs in the ['media'](./media/) folder.

### 🌟 Key Features
- **Multi-Terrain Navigation:** Capable of traversing flat ground, stairs, and slopes.
- **Curriculum Learning:** Automated progressive difficulty adjustment for complex terrain adaptation.
- **Robustness & Disturbance Rejection:** Capable of maintaining balance under external force perturbations.
- **Proprioceptive Control (Blind):** Navigates complex terrains without relying on height scanners or exteroceptive vision sensors.
- **Bunny Hopping Mode:** Specialized policy for highly dynamic jumping motions.

## 🛠️ Installation & Setup
*(Recommendation: Add your specific Conda environment setup instructions here, e.g., `conda create -n isaaclab python=3.10`, to help others reproduce your work easily.)*

## 🚀 Usage Guide

Use the `scripts/rsl_rl/train.py` script to train the agent and `scripts/rsl_rl/play.py` to evaluate the trained policies.

### 1. Flat Ground Locomotion
**Train:**
```bash
python3 scripts/rsl_rl/train.py --task=Isaac-Limx-PF-Blind-Flat-v0 --headless

```

**Play:**

```bash
python3 scripts/rsl_rl/play.py --task=Isaac-Limx-PF-Blind-Flat-Play-v0 --checkpoint_path=model/flat.pt

```

**Disturbance Testing:**

```bash
python3 scripts/rsl_rl/play.py --task=disturb-PF-Flat-v0 --checkpoint_path=model/flat.pt

```

### 2. Complex Terrain (Stairs & Slopes)

*Trained using Curriculum Learning.*

**Train:**

```bash
python3 scripts/rsl_rl/train.py --task=hzs_stairs_without_height --headless

```

**Play:**

```bash
python3 scripts/rsl_rl/play.py --task=hzs_stairs_without_height_play --checkpoint_path=model/stairs_terrains.pt

```

### 3. Bunny Hopping

**Train:**

```bash
python3 scripts/rsl_rl/train.py --task=hzs_hopping --headless

```

**Play:**

```bash
python3 scripts/rsl_rl/play.py --task=hzs_hopping --checkpoint_path=model/hopping.pt

```

### ⚙️ Common Arguments

* `--headless`: Run simulation without GUI (faster training).
* `--resume=true`: Resume training from a checkpoint.
* `--checkpoint_path=path/to/checkpoint`: Specify the model weights to load.

## 🤝 Acknowledgments

**Author:** Zishuo Huang

