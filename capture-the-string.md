Capture the String (CTS) is a simple LLM eval game.

Following von Neumann, we start with the one-person case: a pure maximization problem with no opponent.

## The Game

A CTS game is a tuple $(\tau, B, t, P, o, c, u)$:

- $\tau$ — the target message (a string).
- $B \in \mathbb{N}$ — a turn budget.
- $t \in \{1, \dots, B\}$ — the turn index.
- $P$ — a single player who emits one message per turn.
- $o^t$ — the message emitted by $P$ at turn $t$.
- $c^t = (o^1, \dots, o^t)$ — the transcript through turn $t$.
- $u \in \{+1, -1\}$ — the payoff.

## Termination

The game ends at the first turn such that either:

- **Win:** $o^t = \tau$, with $u = +1$.
- **Loss:** $t = B$ and no win has occurred, with $u = -1$.
