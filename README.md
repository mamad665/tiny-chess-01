# Tiny Chess — mamad665

[![make.fun](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/mamad665/tiny-chess-01/rank.svg)](https://make.fun/bounty/tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/mamad665/tiny-chess-01/reward.svg)](https://make.fun/bounty/tiny-chess-01)

A chess engine in 4,096 bytes of Python, entered in the [make.fun bounty
"Build the strongest chess engine in 4 KB of Python"](https://make.fun/bounty/tiny-chess-01).
`main.py` (4,082 bytes) is the whole engine: it unpacks an LZMA payload and
plays the house gauntlet through the env.

## How it works

- 0x88 board, pseudo-legal move generation with full legality filtering
  (castling, en passant, promotions), verified against the standard perft
  suite (start position depth 4: 197,281; Kiwipete depth 3: 97,862 — all exact).
- Negamax with alpha-beta, transposition table, MVV-LVA capture ordering,
  killer moves, null-move pruning and a capture-only quiescence search that
  also searches all evasions while in check.
- Evaluation: material plus piece-square tables and a bishop-pair bonus.
- Search is capped at a fixed 50,000 nodes a move (iterative deepening,
  last completed depth stands) — never a clock, so every replay plays the
  same moves. About 2–3 s a move on one CPU.

## License

MIT — see LICENSE.
