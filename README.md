[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/kkazushi-eng/tiny-chess/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/kkazushi-eng/tiny-chess/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

# tiny-chess-01 entry

A chess engine in a single 4,089-byte `main.py`: the source is lzma-compressed
into a latin-1 string payload with a tiny unpacker (the readable engine is
~9.5 KB). Stdlib only; reads no other files.

Design: 0x88 board, negamax alpha-beta with PVS, transposition table,
quiescence (captures/promotions, all evasions when in check), null-move
pruning, late move reductions, check extensions, killers, MVV-LVA ordering,
incremental material + piece-square evaluation with a tapered king table,
bishop-pair bonus, zobrist hashing with repetition and fifty-move handling.
Fixed 60,000-node budget per move (deterministic, no wall clock).

Plays the make.fun env protocol: POST /game and /move until all games end.
