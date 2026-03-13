---
description: Create a simple Product Requirements Document from conversation
argument-hint: [output-filename]
---

# Create Simple PRD

Generate a lightweight Product Requirements Document based on the current conversation.

## Before You Start

Use AskUserQuestion to quickly confirm:

1. **What does the tool do?** — Core functionality in one sentence
2. **Who is it for?** — Target user (e.g., "developers", "myself", "general users")
3. **Any technology preferences?** — Language, libraries, APIs

Don't proceed until these are answered.

## Output File

Write the PRD to: `$ARGUMENTS` (default: `PRD.md`)

## PRD Template

```markdown
# PRD: {Project Name}

## What We're Building

{One paragraph describing what this tool/app does and why it's useful.}

## Features

- {Feature 1 — what it does}
- {Feature 2 — what it does}
- {Feature 3 — what it does}
- ...

## Tech Stack

- **Language:** {e.g., Python 3.x}
- **Libraries:** {e.g., httpx for HTTP requests}
- **APIs:** {e.g., Open-Meteo (no API key needed)}
- **Tools:** {e.g., uv for package management}

## How It Works

1. {Step 1 — e.g., User provides a city name}
2. {Step 2 — e.g., Tool looks up coordinates via geocoding API}
3. {Step 3 — e.g., Tool fetches weather for those coordinates}
4. {Step 4 — e.g., Tool displays results in the terminal}

## Success Criteria

- [ ] {Criterion 1 — e.g., User can look up weather for any city}
- [ ] {Criterion 2 — e.g., Handles city-not-found gracefully}
- [ ] {Criterion 3 — e.g., Shows temperature, wind, and conditions}
```

## Instructions

1. Review the conversation to understand what the user wants to build
2. Fill in the template with specific, concrete details
3. Keep it short — this should fit on one screen
4. Write the file and confirm the path

## After Creating

- Confirm where the file was saved
- Highlight any assumptions you made
- Suggest running `/create-rules` next
