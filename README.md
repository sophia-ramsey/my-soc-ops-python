🌐 [Português (BR)](README.pt_BR.md) | [Español](README.es.md)

# 🎀 Soc Ops: Social Bingo, But Make It Sparkly

> Break the ice, find your people, and snatch that 5-in-a-row win.

Soc Ops is a social bingo game for in-person mixers, team meetups, and community events. Everyone gets a unique board, then mingles to find people who match each square.

## 💖 Why You'll Love It

- 🎲 **Fresh every game**: boards are randomized so no two players get the same layout.
- 💾 **Progress stays with you**: session state is persisted with cookies.
- 🏆 **Built-in bingo checks**: rows, columns, and diagonals are automatically validated.
- 🎉 **Win moment included**: players get a celebratory bingo modal.
- 📱 **Event-friendly UX**: mobile-first design for phone play on the go.

## 🎯 How It Works

1. Start a new game.
2. Walk around and find people who match each prompt.
3. Tap squares to mark them (the center square is always FREE SPACE).
4. Get 5 in a row to trigger BINGO.

## 📚 Lab Guide

Want the full build journey with Copilot agents? Pick your chapter:

| Part | Title |
|------|-------|
| [**00**](https://copilot-dev-days.github.io/agent-lab-python/docs/step.html?step=00-overview) | Overview & Checklist |
| [**01**](https://copilot-dev-days.github.io/agent-lab-python/docs/step.html?step=01-setup) | Setup & Context Engineering |
| [**02**](https://copilot-dev-days.github.io/agent-lab-python/docs/step.html?step=02-design) | Design-First Frontend |
| [**03**](https://copilot-dev-days.github.io/agent-lab-python/docs/step.html?step=03-quiz-master) | Custom Quiz Master |
| [**04**](https://copilot-dev-days.github.io/agent-lab-python/docs/step.html?step=04-multi-agent) | Multi-Agent Development |

> 📝 Lab guides are also available in the [`workshop/`](workshop/) folder for offline reading.

## 🚀 Quick Start

### Prerequisites

- [Python 3.13+](https://www.python.org/downloads/)
- [uv](https://docs.astral.sh/uv/) package manager

### Install + Run

```bash
uv sync
uv run uvicorn app.main:app --reload --host 0.0.0.0 --port 8000
```

### Quality Checks

```bash
uv run ruff check .
uv run pytest
```

Expected project baseline is zero lint errors and all 25 tests passing.

## 🫧 Customize The Prompts

Open [`app/data.py`](app/data.py) and update the `QUESTIONS` list with your own conversation starters.

## 🛠️ Tech Stack

- **Backend**: FastAPI
- **Templating**: Jinja2 + HTMX
- **Styling**: custom utility CSS (Tailwind-inspired, no Tailwind dependency)
- **State**: server-side session data with cookie persistence
- **Tooling**: `uv`, `pytest`, `ruff`

## 📁 Project Structure

```text
app/
├── templates/       # Jinja2 templates
│   ├── base.html
│   ├── home.html
│   └── components/  # bingo_board, bingo_modal, game_screen, start_screen
├── static/          # CSS and JS assets
├── data.py          # Question bank + free space text
├── game_logic.py    # Board generation, square toggling, bingo checks
├── game_service.py  # Session game state management
├── models.py        # Pydantic game models
└── main.py          # FastAPI routes
tests/
├── test_api.py
└── test_game_logic.py
```

## 🤝 Contributing

See [`CONTRIBUTING.md`](CONTRIBUTING.md) and [`CODE_OF_CONDUCT.md`](CODE_OF_CONDUCT.md).

## 📝 License

MIT. Build it, remix it, and make your next event way more fun.
