# Flappy Bird AI

A hands-on learning project: build Flappy Bird from scratch in Python, then teach an AI to play it using two different approaches, **neuroevolution (genetic algorithm)** and **Deep Q-Learning (DQN)**, with everything trained locally.

The focus is on *understanding* how these algorithms work, so the game environment, networks, and training loops are written by hand rather than pulled from a pre-trained model or an existing RL framework.

## Goals

- Build a complete Flappy Bird game with Pygame.
- Learn neural-network fundamentals: weights, biases, activation functions, loss functions, and backpropagation.
- Implement and train networks with PyTorch.
- Train an agent with a genetic algorithm and with DQN.
- Save trained models and load them for gameplay without retraining.
- Compare both approaches on score, consistency, and training time.

## Tech Stack

| Tool | Purpose |
|------|---------|
| Python 3.13 | Core language |
| Pygame | Game, rendering, and visualization |
| NumPy | Numerical work and the genetic algorithm |
| PyTorch | Neural networks and DQN training |
| Git | Version control |

## Getting Started

```bash
# Clone the repository
git clone https://github.com/<your-username>/ai-flappy-bird.git
cd ai-flappy-bird

# Create and activate a virtual environment (Windows)
python -m venv venv
venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Play the game manually
python flappybird.py
```

On macOS/Linux, activate the environment with `source venv/bin/activate`.

## Project Structure

```
ai-flappy-bird/
├── flappybird.py        # Playable game
├── assets/              # Sprites and images
├── ai/
│   ├── network.py       # Neural-network definitions
│   ├── genetic.py       # Genetic algorithm training
│   └── dqn.py           # DQN training
├── models/              # Saved checkpoints
├── requirements.txt
└── README.md
```

This is the planned layout and will evolve as the project grows.

## How the AI Sees the Game

**State (inputs)**

1. Bird's vertical position
2. Bird's vertical velocity
3. Horizontal distance to the next pipe
4. Vertical distance between the bird and the gap
5. Bird's position relative to the gap boundaries

**Actions (outputs)**

| Action | Meaning |
|--------|---------|
| `0` | Do nothing |
| `1` | Flap |

## Approaches

### 1. Genetic Algorithm
A population of networks plays the game at the same time. Each network's weights are treated as a genome. The best performers are selected, combined through crossover, and mutated to form the next generation. No gradients are needed.

### 2. Deep Q-Network (DQN)
A single agent observes the state, picks an action, and receives a reward. Experiences are stored in a replay buffer and sampled to train a Q-network with gradient descent, using a target network for stability.

## Roadmap

1. **Game development**: bird physics, gravity, pipe generation, collisions, scoring, and game-over logic.
2. **Neural-network fundamentals**: tensors, layers, activations, loss functions, and gradient descent.
3. **Genetic algorithm**: genome encoding, fitness evaluation, selection, crossover, and mutation.
4. **Deep Q-Network**: reward design, experience replay, and policy learning.
5. **Model integration**: save and load checkpoints, then run inference-only gameplay.
6. **Evaluation**: compare both methods side by side.

## Evaluation Metrics

Both methods will be compared on:

- Average and maximum score over many episodes
- Survival time
- Consistency across runs
- Training time

Results will be added here once training is complete.

## Usage (planned)

```bash
python -m ai.genetic          # Train with the genetic algorithm
python -m ai.dqn              # Train with DQN
python play.py --model models/best.pth   # Watch a trained agent play
```

## License

Released under the MIT License. See `LICENSE` for details.
