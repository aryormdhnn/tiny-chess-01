# Tiny Knight — tiny-chess-01

[![tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/c/tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/aryormdhnn/tiny-chess-01/rank.svg)](https://make.fun/c/tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/aryormdhnn/tiny-chess-01/reward.svg)](https://make.fun/c/tiny-chess-01)

An entry for [make.fun's "Tiny Chess" competition](https://make.fun/c/tiny-chess-01):
the strongest chess engine I could write in 4,096 bytes of Python.

## How it works

`main.py` is a packed (LZMA) build of `engine.py`, a from-scratch engine:
0x88 board, alpha-beta with iterative deepening to a fixed 200,000-node
budget per move, transposition table, killer moves, history heuristic,
quiescence over captures (and all evasions when in check), and an
incremental material + piece-square evaluation. No clock, no randomness:
the same position always gets the same move, so replays match.

It talks to the trial env alone, over HTTP: `POST /game` for the game in
play, `POST /move` with its move in UCI.

## Files

- `main.py` — the entrypoint (packed build, at most 4,096 bytes)
- `engine.py` — the readable source (not committed; see `makefun compress`)
- `LICENSE` — MIT
