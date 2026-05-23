Capture the String (CTS) is a simple LLM eval game.

Following von Neumann, we start with the one-person case: a pure maximization problem with no opponent.

## The Game

A CTS game is a tuple $(\Sigma, s^*, B)$:

- $\Sigma$ — a finite alphabet of messages.
- $s^* \in \Sigma$ — the target message.
- $B \in \mathbb{N}$ — a turn budget.

A single player $P$ emits a message $o^t \in \Sigma$ at each turn $t \in \{1, \dots, B\}$. The transcript is $c^t = (o^1, \dots, o^t)$.

## Termination

The game ends at the first $t$ such that either:

- **Win:** $o^t = s^*$.
- **Loss:** $t = B$ and no win has occurred.

Payoff is $u \in \{+1, -1\}$ accordingly.
