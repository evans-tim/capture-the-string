Capture the String (CTS) is a simple LLM eval game. Following von Neumann, we start with the one-person case: a pure maximization problem with no opponent.

In the single-player game, a fixed target string is chosen in advance, along with a turn budget that caps how long the game can run. A single player takes turns emitting one message per turn, and the running transcript of everything the player has said so far accumulates as the game's context. The game resolves to a payoff of either +1 or -1.

Termination is straightforward: the game ends the first turn the player's message exactly matches the target (a win, payoff +1), or when the budget runs out without a match (a loss, payoff -1).

To instantiate a game, you pick a concrete target, budget, and player — for example, target "hello world", budget 5, player GPT-4. That tuple alone doesn't fully specify behavior, though, since it leaves open what the player actually sees on each turn.

The game engine is what fills that gap: it drives turns, decides what context the player is shown, and adjudicates termination. Open questions include whether the player sees a system prompt explaining the rules, whether it sees its own prior outputs, and how the win-check is performed (exact match, normalized, etc.).
