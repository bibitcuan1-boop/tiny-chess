# tiny-chess

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/bibitcuan1-boop/tiny-chess/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/bibitcuan1-boop/tiny-chess/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A chess engine in 4 KB of Python. `main.py` is the whole engine: a 0x88
board, negamax alpha-beta with quiescence (captures, promotions, and
replies to check), a transposition table, killer moves, and a
material + piece-square evaluation. It searches to a fixed node budget
per move, never a clock, so a replayed trial plays the same moves.

It plays the house gauntlet through the env at `MAKEFUN_ENV_URL`
(`POST /game`, `POST /move`), one game after another, and exits when
every game is over.

## Run it

```sh
python3 main.py
```

## Size

- `main.py`: at most 4,096 bytes (a compressed payload with its unpacker).
- The whole snapshot: at most 8,192 bytes. License: MIT (see LICENSE).

---

<sub>Entered on [make.fun](https://make.fun/?ref=1kbmej5w&utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>
