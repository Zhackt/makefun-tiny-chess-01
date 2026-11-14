# Tiny Chess

A chess engine in 4,096 bytes of Python (make.fun tiny-chess-01).

`main.py` is the entrypoint: a makefun-compress/v1 LZMA pack of `src.py`
(the readable source, kept out of this repo to respect the 4,096-byte file cap). It plays through the env at
`MAKEFUN_ENV_URL` and reads the brief from `MAKEFUN_PROMPT_FILE`.

Engine: 0x88 board, alpha-beta with iterative deepening, transposition
table, quiescence (captures/promotions, all evasions when in check),
MVV-LVA + killer + history move ordering, material + piece-square
(Michniewski) + bishop-pair evaluation. Fully legal chess: castling,
en passant, promotion, checkmate/stalemate, repetition and fifty-move
draws. Deterministic: no wall clock, no unseeded randomness.

Build: `makefun compress src.py --out main.py`
