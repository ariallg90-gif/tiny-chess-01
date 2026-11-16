# tiny-chess-01

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/ariallg90-gif/tiny-chess-01/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/ariallg90-gif/tiny-chess-01/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A compact chess engine in a single 4 KB Python file: 0x88 board, negamax alpha-beta with a transposition table, quiescence search (captures, plus check evasions), LMR, PVS, null-move pruning and futility pruning, Michniewski piece-square tables, and repetition detection. Fixed 60,000-node budget per move — fully deterministic, no wall clock, no network calls except the environment API. Plays via HTTP against the make.fun environment (`POST /game`, `/move`, `/resign`).

## How it is packed

The submitted `main.py` is produced by the kit's `makefun compress` from the readable source `engine.py` (same directory, not committed): an LZMA payload with the kit's unpacker stub. The source is the engine; `main.py` is only its packed form. Rebuild it with:

```sh
node <kit>/cli/makefun.mjs compress engine.py
```

Move ordering is TT move first, then captures by MVV-LVA, then killer moves. The search extends checks by a ply, runs quiescence on captures and promotions (all evasions while in check), and prunes with null-move (R=2), futility margins at depths 1–2, and late-move reductions for quiet moves.

## Verification

Move generation passes the standard perft suite (start position, Kiwipete, en-passant/promotion/castling positions) at depths 1–4, 15/15 checks. The search finds mate-in-1, runs at ~50,000 nodes/second on one CPU, and spends a fixed 60,000 nodes per move (about 1–2 seconds), well inside the 10-second move limit. Two runs of the same position give the same move and the same node count, so a trial replay matches.

## Run it

```sh
MAKEFUN_ENV_URL=http://127.0.0.1:8123 python3 -P -s main.py
```

---

<sub>Entered on [make.fun](https://make.fun/?ref=emzdd1kk&utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>
