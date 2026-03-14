# Weather Tool — Claude Code Class Exercise

A beginner-friendly exercise repository for learning [Claude Code](https://docs.anthropic.com/en/docs/claude-code) fundamentals. Students build a simple command-line weather lookup tool in Python while practicing a structured **Research → Plan → Implement → Validate** workflow using Claude Code skills.

## What This Is

This is an **educational scaffold**, not a production application. The repo provides:

- A step-by-step exercise guide (~90 minutes)
- Pre-configured Claude Code skills (slash commands) for structured development
- A `CLAUDE.md` template for establishing project conventions

Students clone this repo and use Claude Code to build a CLI weather tool from scratch, learning how to leverage AI-assisted development effectively.

## Prerequisites

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) installed and authenticated
- [Python 3.10+](https://www.python.org/)
- [`uv`](https://docs.astral.sh/uv/) (Python package manager)
- Git

## Getting Started

```bash
git clone <this-repo-url>
cd weather-tool
claude
```

Then open `class-exercise-weather-tool.md` and follow the exercise from Part 1.

## Exercise Overview

| Part | Activity | Time |
|------|----------|------|
| 1 | Project Setup — initialize Python project with `uv` | 10 min |
| 2 | Research — explore APIs and libraries conversationally | 10 min |
| 3 | PRD — generate a lightweight product requirements doc | 15 min |
| 4 | Rules — create `CLAUDE.md` with project conventions | 10 min |
| 5 | Plan — create an implementation plan | 15 min |
| 6 | Implement — execute the plan with Claude Code | 15 min |
| 7 | Quality — review, simplify, and commit | 10 min |
| 8 | Reflect — review what you learned | 5 min |

The finished tool uses the [Open-Meteo API](https://open-meteo.com/) (free, no API key required) to look up weather by city name.

## Included Skills

Skills are reusable Claude Code slash commands located in `.claude/skills/`. This repo includes beginner-friendly versions alongside their advanced counterparts:

| Skill | Command | Description |
|-------|---------|-------------|
| **Create PRD (Simple)** | `/create-prd-simple` | Generate a lightweight, one-screen product requirements doc |
| **Create Rules** | `/create-rules` | Analyze the project and generate a `CLAUDE.md` conventions file |
| **Plan Feature (Simple)** | `/plan-feature-simple` | Create a scannable implementation plan |
| **Execute** | `/execute` | Execute an implementation plan step by step |
| **Prime** | `/prime` | Load and summarize project context |
| **Commit** | `/commit` | Create a well-formatted git commit |
| **Create PRD** | `/create-prd` | Full 15-section PRD (advanced) |
| **Plan Feature** | `/plan-feature` | Comprehensive feature planning with research (advanced) |

## Project Structure

```
weather-tool/
├── .claude/
│   ├── .agents/
│   │   └── CLAUDE-template.md      # Template for generating CLAUDE.md
│   ├── settings.local.json         # Claude Code permissions
│   └── skills/                     # Reusable slash commands
│       ├── commit/
│       ├── create-prd/
│       ├── create-prd-simple/
│       ├── create-rules/
│       ├── execute/
│       ├── plan-feature/
│       ├── plan-feature-simple/
│       └── prime/
├── class-exercise-weather-tool.md  # The exercise guide
└── README.md
```

## Key Concepts Taught

- **Conversational research** — explore options before committing to a plan
- **Structured planning** — use PRDs and implementation plans to stay organized
- **Context management** — start fresh sessions to keep Claude Code focused
- **Validation at every step** — test and verify as you go
- **Repeatable workflows** — use skills to make the process consistent

## Bonus Challenges

After completing the main exercise, students can extend their tool with:

- Multi-day forecasts
- Favorite/saved cities
- Rich terminal formatting
- Unit conversion (Celsius/Fahrenheit)

## Help

If you get stuck during the exercise, reach out at **ai_class@fastmail.com**.

## License

This project is for educational use in Claude Code workshops and classes.
