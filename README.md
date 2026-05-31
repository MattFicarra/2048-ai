# 2048 • Self-Learning AI

A beautiful, self-contained browser game of 2048 where a neural network **continually learns** using reinforcement learning (TD learning) to guide Monte Carlo / expectimax-style search.

Open `index.html` in any modern browser. No server, no install. Everything (including the learned "brain") persists in localStorage.

## How the AI Works (MCTS + RL)

- **Value Network**: A small 2-layer neural net (20 inputs → 28 hidden tanh → 1 value) that estimates how good any board position is (expected future score).
- **Search**: 
  - During fast training: pure greedy on the value net (4 evaluations per decision) → extremely fast self-play.
  - During spectating / "Play": Monte Carlo rollouts (MCTS-style flat search) or deeper expectimax that use the learned value net for leaf evaluation and early cutoffs.
- **Learning**: After (and during) every AI move in training or spectate, it performs TD(0) updates: `V(s) ← V(s) + α · (r + γ·V(s′) − V(s))`. The net gets better, search gets smarter, data gets higher quality — classic self-improving RL loop.

The longer you leave Continuous Training on (or click "Train 2500"), the higher the scores the AI achieves when you watch it play.

## Controls

- **Arrow keys / WASD** — Play manually
- **S** — Toggle AI spectate (watch the current brain play beautifully)
- **C** — Toggle continuous background training (AI plays thousands of games rapidly)
- **H** — Ask the AI for a hint on the current manual board
- **R** — New game
- Sliders — "Play" strength (spectate quality) vs "Train" strength (how smart the self-play is during bulk training)

## Tips for Best Results

1. Click **"Train 2500 (fast)"** once or twice when you first open it.
2. Turn on **Continuous Training (C)** and leave the tab open while you do other things.
3. Watch with **Spectate (S)** using high Play strength — you'll see it reach 2048, 4096, and beyond as the value net improves.

The learning curve chart updates live. Recent average score and "Best Tile Ever" are the best indicators of progress.

## Technical Notes

- ~700 parameters in the value net. Trains in real time in your browser.
- All game logic, search, NN forward+backprop, and rendering are pure JavaScript in one file.
- Expect 1,000–8,000+ training episodes per minute on a modern machine depending on Train strength slider (lower = faster data, still improves well).

Enjoy watching an AI teach itself to master 2048!

---

**Live demo & source**: https://github.com/MattFicarra/2048-ai

Import the repo into Vercel for an instant deployed version (static hosting, worldwide CDN, free).