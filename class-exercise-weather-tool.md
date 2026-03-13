# Class Exercise: Building a Weather Lookup Tool

## Exercise Overview

In this exercise, you'll build a simple command-line weather lookup tool using Python. The tool takes a city name and returns the current weather conditions. Along the way, you'll practice the full Research → Plan → Implement → Validate loop using Claude Code commands.

**What you'll practice:**
- Using conversational research to explore APIs and packages before committing to a plan
- Using `/create-prd-simple` to plan a project
- Using `/create-rules` to set up your CLAUDE.md
- Using `/prime` to orient Claude at the start of a session
- Using `/plan-feature-simple` to create an implementation plan
- Using `/execute` to have Claude implement the plan
- Using `/commit` to make a standardized git commit
- Using `/simplify` (built-in) for an automated quality pass

**Prerequisites:**
- Claude Code installed and working (Desktop Code tab or CLI)
- Python installed (via `uv` — already set up from our prerequisites session)
- Git installed and configured
- A terminal you're comfortable typing in

**Time estimate:** 75–100 minutes

---

## Part 1: Project Setup (10 minutes)

### Step 1.1: Create the project folder

```bash
mkdir weather-tool
cd weather-tool
uv init # initial git and more
uv run python --version # create the .venv virtual environment folder
```

### Step 1.2: Set up the plans directory

The Claude Code skills (`/create-prd-simple`, `/prime`, `/plan-feature-simple`, etc.) are already installed in your project under `.claude/skills/`. The only folder we need to create manually is where implementation plans will be saved:

```bash
mkdir -p .agents/plans
```

### Step 1.3: Verify skills are available

Using the Code tab of Claude Desktop (while in the weather-tool directory), ask, "What skills are available to this project?" Or open Claude Code (terminal) in your project directory and type `/` to see the list of available skills. You should see these skills that we'll use during the exercise:

| Skill | Purpose |
|-------|---------|
| `/create-prd-simple` | Create a lightweight Product Requirements Document |
| `/create-rules` | Generate a CLAUDE.md with project conventions |
| `/prime` | Orient Claude on your codebase at the start of a session |
| `/plan-feature-simple` | Create a short implementation plan |
| `/execute` | Have Claude implement a plan |
| `/commit` | Make a standardized git commit |
| `/simplify` | Automated code quality pass |

If any are missing, ask your instructor for help.

### Step 1.4: Make an initial commit

`uv init` already ran in Step 1.1 and created `pyproject.toml` and a basic project structure. We'll let Claude figure out the dependencies during implementation.

Make an initial commit so we have a clean starting point:

```bash
git add -A
git commit -m "chore: initialize project with AI layer and uv"
```

---

## Part 2: Research Phase (10 minutes)

Before jumping into a PRD, take a few minutes to explore the solution space. This is where you figure out *what tools and APIs to use* through conversation with Claude. You don't need to know the answers up front — that's the point.

**Start a conversation with Claude** (Claude Desktop Code tab or Claude Code CLI, from your project directory).

### Step 2.1: Describe what you want to build

Send this as your first message:

```
I want to build a simple command-line weather lookup tool in Python. The user
enters a city name and gets back current weather conditions — temperature, wind
speed, and a short description like "Partly cloudy." It should handle ambiguous
city names gracefully. Keep it simple — a single script is fine. For the API,
only consider free weather APIs that don't require an API key or have restrictive
rate limits. Suggest which Python packages I should use.

Do not write any code yet. This is the research phase.
```

Claude will suggest an API and a Python HTTP library. Read the suggestions — but don't just accept them.

### Step 2.2: Challenge the first suggestion

Claude will likely recommend the `requests` library. Push back:

```
Don't write the script yet.
What are the alternatives to requests? This project is a simple starter example
for a larger project.
```

Claude should walk you through alternatives like `httpx`, `aiohttp`, and `urllib3`, with trade-offs for each. This is a key habit: **don't accept the first answer without exploring alternatives.**

### Step 2.3: Lock in your decisions

Once you've seen the options, confirm your choices and ask Claude to summarize:

```
Good. Let's go with httpx and Open-Meteo. Summarize what we've decided so far —
API choice, packages, and key behaviors — so I can use it as input for the next
step. Do not write code.
```

Claude will produce a clean summary of your decisions. **Save or copy this summary** — you'll feed it into the PRD step next.

> **What this phase teaches:** Explore before you commit. The research conversation helps you (1) discover options you didn't know about, (2) challenge default suggestions, and (3) checkpoint decisions in writing before they get baked into a formal plan. Changing your mind here costs nothing. Changing it after implementation costs real time.

---

## Part 3: Planning with /create-prd-simple (15 minutes)

**Continue in the same conversation** from Part 2. You already have Claude's summary of your research decisions.

If you like, hit the microphone on Claude Desktop (lower right) or type /voice on claude code cli.

### Step 3.1: Feed in your research and start the PRD conversation

Take the summary Claude produced at the end of Part 2 and use it as the starting point. Tell Claude you want to discuss details before creating the PRD:

```
Based on the research summary above, I'd like to turn this into a PRD. But first,
ask me questions so we can get aligned on the details before creating it.
```

### Step 3.2: Answer Claude's questions

Claude should come back with several questions. These might include:
- Should the tool handle ambiguous city names (e.g., "Portland" matches Portland OR and Portland ME)?
- What temperature units — Celsius, Fahrenheit, or let the user choose?
- Should it show a multi-day forecast or just current conditions?
- How should errors be displayed (city not found, API down, no internet)?
- Should results be plain text or formatted with colors?

Answer each question. If Claude offers multiple-choice options, pick the one you prefer. If none fit, type your own answer. **Every question you answer is removing an assumption that would otherwise lead to wrong code.**

### Step 3.3: Generate the PRD

Once you've answered all the questions, run:

```
/create-prd-simple
```

Claude will synthesize your conversation into a short, focused PRD and save it as `PRD.md`. This simplified version covers just the essentials: what you're building, features, tech stack, and success criteria.

**Important:** Read through the PRD. Make sure it captures what you actually want. If something is wrong or missing, tell Claude and have it update the PRD before moving on.

---

## Part 4: Setting Up Rules with /create-rules (10 minutes)

### Step 4.1: Generate your CLAUDE.md

In the same conversation, run:

```
/create-rules
```

Claude will analyze your PRD and project setup, then create a `CLAUDE.md` file with:
- Your tech stack (Python, httpx, uv)
- Commands to run and test the project
- Project structure
- Code patterns and conventions
- Testing approach

### Step 4.2: Review and customize

Open `CLAUDE.md` and read through it. A few things to check:
- Are the run/test commands correct?
- Do the code patterns match what you'd expect for a simple Python project?
- Is there anything obviously wrong?

If you want to add your own preferences (for example: "Use f-strings for string formatting" or "Include type hints on all functions"), add them now.

Commit everything:

```
/commit
```

---

## Part 5: Planning the Feature with /plan-feature-simple (15 minutes)

Now we'll do the "Plan" step of the loop. **Start a fresh Claude Code conversation** — this is the context reset that keeps things focused.

### Step 5.1: Prime Claude

In the new conversation, run:

```
/prime
```

Claude will explore your project, read the PRD and CLAUDE.md, check the git log, and output a summary of its understanding. Read the summary and confirm it looks right.

### Step 5.2: Discuss the implementation

Tell Claude you want to plan the first (and in this case, only) phase. Something like:

```
The PRD looks good. Let's plan the implementation. I want to build the weather 
lookup tool as described in the PRD. Let's think through exactly how to structure 
the code, handle errors, and test it. Don't code anything yet.
```

Have a brief conversation about implementation details. Claude might raise points about:
- How to structure the HTTP calls (separate functions for geocoding vs. forecast?)
- Error handling strategy (what if the city isn't found? what if the API is down?)
- How to format the output
- What to test and how

### Step 5.3: Generate the plan

When you're satisfied with the discussion, run:

```
/plan-feature-simple
```

Claude will create a short implementation plan and save it to `.agents/plans/`. The plan will include:
- What we're building (the goal)
- Files to create
- Steps in dependency order
- How to test it

**Read the plan.** Make sure the steps make sense and the testing approach is solid. If something looks off, tell Claude and have it revise the plan.

Commit the plan:

```
/commit
```

---

## Part 6: Implementation with /execute (15 minutes)

This is the "Implement" step. **Start another fresh Claude Code conversation** — another context reset.

### Step 6.1: Execute the plan

Run:

```
/execute .agents/plans/[your-plan-filename].md
```

(Replace `[your-plan-filename]` with the actual filename Claude created — it will be something like `weather-lookup-tool.md`.)

Now sit back and watch. Claude will:
1. Read the entire plan
2. Create each file in order
3. Install dependencies
4. Run validation commands as it goes
5. Create and run tests
6. Give you a summary of everything it did

This is where the planning pays off. Because the plan was thorough, Claude can execute without needing to ask you questions or make assumptions.

### Step 6.2: Try it out!

Once Claude finishes, test the tool yourself:

```bash
uv run python weather.py Portland
```

(Or whatever the entry point is — check Claude's summary or the plan.)

You should see something like:

```
Weather for Portland, Oregon, US (45.52°N, 122.68°W)
Temperature: 58°F (14°C)
Wind Speed: 8 mph
Conditions: Partly cloudy

```

Try a few cities:
- Your hometown
- A city with a common name (Portland, Springfield) — does it handle disambiguation?
- A city that doesn't exist — does it show a helpful error?
- No input at all — does it show usage instructions?

---

## Part 7: Quality Pass and Commit (10 minutes)

### Step 7.1: Run /simplify

Before committing, run the built-in quality check:

```
/simplify
```

This will review your recent changes and may:
- Extract duplicated logic into shared functions
- Improve variable names
- Simplify control flow
- Tighten up verbose patterns

**Read what it changed.** Do the changes make sense? If `/simplify` changed something you disagree with, revert that specific change.

### Step 7.2: Final commit

Once you're happy with the code:

```
/commit
```

Claude will create a standardized commit message with an appropriate tag (probably `feat: implement weather lookup tool`).

---

## Part 8: Reflection (5 minutes)

Take a moment to look back at what you did:

1. **You explored before committing.** The research phase helped you make informed choices about APIs and packages before locking them into a PRD. Changing your mind during research costs nothing — changing it after implementation costs real time.

2. **You planned before you coded.** The research → questions → PRD pipeline ensured you and Claude were aligned before a single line of code was written.

3. **You separated planning from implementation.** The plan was created in one session, the code in another. The context reset kept the implementation session focused.

4. **You validated at multiple levels.** Claude ran its own tests during execution. `/simplify` did an automated quality pass. And you tested the tool manually yourself.

5. **You used skills to make the process repeatable.** Every step had a skill: `/create-prd-simple`, `/create-rules`, `/prime`, `/plan-feature-simple`, `/execute`, `/simplify`, `/commit`. If you were building a second feature (say, adding a multi-day forecast), you'd follow the same sequence starting from `/prime`.

6. **You barely wrote any code yourself.** But you were deeply involved in *researching*, *planning*, and *validating*. That's the core skill of AI-assisted development.

### Questions to Consider

- Where in the process did Claude surprise you (good or bad)?
- Did the PRD question-and-answer phase catch anything you hadn't thought of?
- What would you add to your CLAUDE.md based on this experience?
- If you were building the next feature (multi-day forecast, or saving favorite cities), how would the loop work differently now that you have an existing codebase?

---

## Bonus Challenges

If you finish early or want to continue on your own:

**Add a feature using the loop.** Pick one of these and go through the full cycle — `/prime` → `/plan-feature-simple` → context reset → `/execute` → `/simplify` → `/commit`:

- **Multi-day forecast:** Show the next 3-5 days of weather
- **Favorite cities:** Save a list of cities to a JSON file so you can quickly check weather for all of them
- **Rich formatting:** Use the `rich` library to display weather with colors and icons in the terminal
- **Unit conversion toggle:** Let the user switch between Fahrenheit and Celsius with a flag (`--units metric`)

**Evolve your AI layer.** If anything went wrong during the exercise — maybe Claude used a naming convention you didn't like, or the error handling wasn't what you expected — update your CLAUDE.md to prevent it from happening again. This is the "system evolution mindset" in action.

---

## Reference: Open-Meteo API Endpoints

### Geocoding (city name → coordinates)

```
GET https://geocoding-api.open-meteo.com/v1/search?name={city}&count={max_results}
```

Example response (abbreviated):
```json
{
  "results": [
    {
      "name": "Portland",
      "latitude": 45.5234,
      "longitude": -122.6762,
      "country": "United States",
      "admin1": "Oregon"
    }
  ]
}
```

### Current Weather (coordinates → weather)

```
GET https://api.open-meteo.com/v1/forecast?latitude={lat}&longitude={lon}&current_weather=true&temperature_unit={fahrenheit|celsius}&wind_speed_unit={mph|kmh}
```

Example response (abbreviated):
```json
{
  "current_weather": {
    "temperature": 14.2,
    "windspeed": 12.5,
    "weathercode": 2,
    "time": "2026-03-12T14:00"
  }
}
```

### Weather Codes (for displaying conditions)

| Code | Meaning |
|------|---------|
| 0 | Clear sky |
| 1-3 | Partly cloudy |
| 45, 48 | Fog |
| 51-55 | Drizzle |
| 61-65 | Rain |
| 71-75 | Snow |
| 80-82 | Rain showers |
| 95 | Thunderstorm |

Full documentation: https://open-meteo.com/en/docs

---

## Instructor Note: Skills Assessment

This exercise uses **simplified skills** (`/create-prd-simple` and `/plan-feature-simple`) instead of their full-power counterparts. Here's why:

### Skills used in this exercise (appropriate for beginners)

| Skill | Why it works |
|-------|-------------|
| `/create-prd-simple` | Generates a short, focused PRD with 4 sections. Beginners can read and understand the entire document. |
| `/plan-feature-simple` | Produces a plan that fits on one screen: goal, files, steps, how to test. |
| `/create-rules` | Generates CLAUDE.md with project conventions. Straightforward output. |
| `/prime` | Orients Claude on the codebase. Simple concept, clear output. |
| `/execute` | Runs the plan. Students watch Claude work. |
| `/commit` | Creates a standardized git commit. Simple and useful. |
| `/simplify` | Built-in quality pass. Easy to understand. |

### Skills NOT used (too heavyweight for this project)

| Skill | Why it's too much |
|-------|-------------------|
| `/create-prd` | Generates a 15-section enterprise PRD (Executive Summary, Mission, Security & Configuration, API Specification, Risks & Mitigations, etc.). Overkill for a single-script weather tool. Would overwhelm beginners with ceremony. |
| `/plan-feature` | Has 5 planning phases including external research, technology trends analysis, subagent orchestration, confidence scores, and completion checklists. Generates far more planning documentation than actual code for a project this size. |

**When to graduate to the full skills:** Once students are comfortable with the loop on simple projects, introduce `/create-prd` and `/plan-feature` for multi-file projects with real architectural decisions (e.g., a web app with a database, authentication, and multiple API endpoints)
