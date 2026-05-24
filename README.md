Capture the String (CTS) is a single-player LLM eval game. We start with the single-player case: turn minimization problem with no opponent. The "player" is just a single LLM.

<video src="assets/single_player_cts_example.mp4" controls width="600"></video>

A fixed target string and turn budget are set before play. Each turn the player emits one message; prior messages accumulate as context. Payoff is +1 or -1.

The game ends the first turn the player's message exactly matches the target (+1), or when the budget runs out without a match (-1).

## Implementation (`cts.html`)

Open `cts.html` in a browser. Set `OPENAI_API_KEY` in localStorage.

Game parameters:

- **target** — string to match (default: `hello world!`)
- **seedPrompt** — system prompt sent every turn
- **turns** — turn budget (default: 12)
- **hideTarget** — omit `Target: …` from LLM context when checked

Each turn the User service sends the LLM:

1. seed prompt (system)
2. target string (system), unless hidden
3. prior outputs (assistant)

The LLM (`gpt-4o-mini`) returns one message. User checks exact equality against the target, appends the output to the transcript, and continues or stops.

User and LLM are two services in a message-passing simulation. Traces are OpenTelemetry spans (`cts.game`, `cts.turn`, `cts.response`). The UI shows the game initialization options, a step-through game board view, and a trace log.
