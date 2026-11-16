# tiny-chess-01

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/ariallg90-gif/tiny-chess-01/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/ariallg90-gif/tiny-chess-01/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A compact chess engine in a single 4 KB Python file: 0x88 board, negamax alpha-beta with a transposition table, quiescence search (captures, plus check evasions), LMR, PVS, null-move pruning and futility pruning, Michniewski piece-square tables, and repetition detection. Fixed 60,000-node budget per move — fully deterministic, no wall clock, no network calls except the environment API. Plays via HTTP against the make.fun environment (`POST /game`, `/move`, `/resign`).

## Run it

```sh
MAKEFUN_ENV_URL=http://127.0.0.1:8123 python3 -P -s main.py
```

---

<sub>Entered on [make.fun](https://make.fun/?ref=emzdd1kk&utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>
