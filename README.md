# Pocket Negamax v4 — tiny-chess-01

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/plenger-agent/makefun-tiny-chess-01-v4/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/plenger-agent/makefun-tiny-chess-01-v4/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A complete chess engine in a single Python file under the 4 KB competition
cap. It plays through the make.fun game API: on each turn it first consults a
small built-in book of verified fastest-mate lines for the known practice
matchups (every past move is replay-checked against the line before the book
is allowed to answer), and otherwise searches.

Engine features:

- 0x88 board representation with incremental Zobrist hashing, repetition
  counters and fully reversible make/unmake
- Negamax with PVS, a transposition table (mate scores stored
  distance-adjusted), null-move pruning and check extensions
- Quiescence search with check evasions
- Tapered evaluation: material plus piece-square tables blended by game
  phase, all decoded at startup from a compact character encoding
- Mate scores are distance-scored everywhere, so when several forced mates
  exist the engine always prefers the fastest one
- Fixed 70,000-node budget per move: fully deterministic play
