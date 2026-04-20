# Copilot Workspace Instructions

## Mandatory Dev Checklist

Run these before every commit — all must pass:

```bash
uv run ruff check .   # lint: zero errors required
uv run pytest         # test: all 25 tests must pass
```

> No Tailwind, no `pip install`, no JSON routes. See conventions below.

## Project

**Soc Ops** — Social Bingo (FastAPI + Jinja2 + HTMX). Players get a randomized 5×5 board; mark squares by finding matching people. Five in a row = BINGO. See [README.md](../README.md).

**Dev server:** `uv run uvicorn app.main:app --reload --host 0.0.0.0 --port 8000`

## Architecture

| File | Role |
|---|---|
| `app/main.py` | FastAPI routes — all return `HTMLResponse` (HTMX partials) |
| `app/game_service.py` | `GameSession` dataclass — all mutable session state |
| `app/game_logic.py` | Pure functions: `generate_board()`, `toggle_square()`, `check_bingo()` |
| `app/models.py` | Frozen Pydantic models: `BingoSquareData`, `BingoLine`, `GameState` |
| `app/data.py` | `QUESTIONS` list (24 items) + `FREE_SPACE` constant |
| `app/static/css/app.css` | Custom utility classes — see [css-utilities.instructions.md](instructions/css-utilities.instructions.md) |
| `tests/` | `test_api.py` (TestClient) + `test_game_logic.py` (unit) |

## Design Guide

Use this visual direction for frontend work unless a task explicitly asks for a different style:

- **Creative direction** — playful, feminine, high-energy, and polished ("pop princess" vibe).
- **Avoid generic UI** — skip default-looking layouts and overused aesthetics.
- **Typography** — choose expressive fonts; avoid default stacks like Inter/Roboto/Arial unless preserving an existing pattern.
- **Color system** — define clear CSS variables and a cohesive palette with strong contrast.
- **Motion** — prefer a few meaningful animations (page load, staggered reveals) over many micro-animations.
- **Backgrounds** — avoid flat single-color pages; use gradients/shapes/patterns to add atmosphere.
- **Responsiveness** — mobile-first by default; verify layouts on both phone and desktop.
- **Accessibility** — keep readable hierarchy, clear contrast, and usable spacing.
- **Consistency rule** — when editing existing screens, preserve established structure and interaction patterns.

## Conventions & Pitfalls

- **Frozen models** — use `.model_copy(update={...})`, never `.copy()`.
- **Center square** (index 12) is always FREE SPACE — never toggle it.
- **HTMX target** is `#game-container` — all partials must include that element.
- **`_get_winning_lines()`** is `@functools.cache`-decorated — never mutate its return value.
- **Python 3.13 / uv** — use `uv add` / `uv sync`, not `pip`. Snake_case + type hints on all signatures.
- **SECRET_KEY** in `main.py` is a dev placeholder — use an env var in production.
