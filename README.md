# PPO with Human-Style Coaching Rewards on LunarLanderContinuous-v2

This repository contains my course project for the **Reinforcement Learning** class at the University of Tennessee, Knoxville (Instructor: Dr. Li).

The goal of this project is to investigate whether adding human-inspired *coaching rewards* can improve the learning efficiency and stability of an agent trained with **Proximal Policy Optimization (PPO)** on the `LunarLanderContinuous-v2` environment from Gymnasium.

---

## Project Idea

Standard PPO optimizes a policy using only the rewards provided by the environment. In many real-world scenarios, however, humans provide additional guidance in the form of feedback like “you’re going in the right direction” or “don’t tilt so much”.

In this project, I:

- Train a **baseline PPO agent** using only the original environment reward.
- Train a **coaching PPO agent** that receives an additional shaped reward based on simple heuristics, e.g.:
  - Staying near the center (reducing horizontal distance to the landing pad).
  - Maintaining a more upright orientation.

I then compare:

- Learning curves (episode return vs. training steps).
- Stability of the final policy.
- Sample efficiency (how quickly the agent reaches a certain performance threshold).

---

## Methods

**Environment**

- `LunarLanderContinuous-v2` (Gymnasium)
- Continuous action space (2D continuous thrust)
- Environment reward: standard dense/sparse reward defined by the environment.

**Algorithms**

- Policy Gradient: **Proximal Policy Optimization (PPO)**
- Implemented in **TensorFlow/Keras**.

**Reward Shaping / Coaching Reward**

- Total reward used for learning:
  \[
  r_{\text{total}} = r_{\text{env}} + \alpha \cdot r_{\text{coach}}
  \]
- Example coaching features:
  - Penalty for large horizontal distance from the landing pad.
  - Penalty for large tilt angle.
- The coaching reward is meant to mimic human feedback that rewards “good partial progress” even before the full landing is successful.

---

## Repository Structure
