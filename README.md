# 2048 • Self-Learning AI

> **Click here to open the fully optimized version right now:**
>
> **[▶️ OPEN THE GAME](https://htmlpreview.github.io/?https://github.com/MattFicarra/2048-ai/blob/main/index.html)**

A beautiful, self-contained browser game of 2048 where a neural network **continually learns** using reinforcement learning (TD learning) to guide Monte Carlo / expectimax-style search.

All lag issues have been fixed. The AI trains extremely fast in the background while the UI stays smooth.

## Quick Start

1. Click the link above
2. Press **C** to start continuous training
3. Press **S** to watch the AI play with its improving brain

The value net gets better the longer you leave it training.

## How the AI Works (MCTS + RL)

- **Value Network**: A small 2-layer neural net (20 inputs → 28 hidden tanh → 1 value) that estimates how good any board position is.
- **Search**: Fast greedy value net for training (thousands of games/min). Monte Carlo rollouts + expectimax guided by the learned net when watching.
- **Learning**: Real TD(0) updates after moves — classic reinforcement learning self-improvement.

## Controls

- **Arrow keys / WASD** — Manual play
- **S** — Toggle AI Spectate
- **C** — Toggle Continuous Training (background self-play + learning)
- **H** — Hint (what the current brain recommends)
- Sliders control search strength for Play vs Train

## Source

Full code: https://github.com/MattFicarra/2048-ai

To deploy your own copy: Import the repo to Vercel (static site, instant).