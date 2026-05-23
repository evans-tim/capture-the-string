Capture the String (CTS) is a simple LLM eval game.

Following von Neumann, we start with the one-person case: a pure maximization problem with no opponent.

## Single player game

A CTS game is a tuple $(\tau, B, t, P, o, c, u)$:

- $\tau$ — **Target** — the target message (a string).
- $B \in \mathbb{N}$ — **Budget** — a turn budget.
- $t \in \{1, \dots, B\}$ — **Turn** — the turn index.
- $P$ — **Player** — a single player who emits one message per turn.
- $o^t$ — **Output** — the message emitted by $P$ at turn $t$.
- $c^t = (o^1, \dots, o^t)$ — **Context** — the transcript through turn $t$.
- $u \in \{+1, -1\}$ — **Utility** — the payoff.

## Termination

The game ends at the first turn such that either:

- **Win:** $o^t = \tau$, with $u = +1$.
- **Loss:** $t = B$ and no win has occurred, with $u = -1$.


# Instantiation

Hello world: (Target="hello world", Budget=5, P=GPT-4)

# Game Engine

The engine drives turns, exposes context to the player, and adjudicates termination.