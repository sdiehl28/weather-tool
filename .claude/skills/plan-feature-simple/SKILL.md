---
description: Create a simple implementation plan for a feature
---

# Plan a Feature (Simple)

## Feature: $ARGUMENTS

## Objective

Create a short, actionable implementation plan. No code is written in this step — just the plan.

## Process

### 1. Understand the Feature

- Read the PRD (if one exists)
- Read CLAUDE.md (if one exists)
- Understand what needs to be built

### 2. Ask Clarifying Questions

If anything is unclear, use AskUserQuestion to clarify before planning. For example:
- How should errors be handled?
- Any preferences on code structure?
- What should the output look like?

### 3. Create the Plan

Write a plan file to `.agents/plans/{feature-name}.md` using this structure:

```markdown
# Plan: {Feature Name}

## Goal

{1-2 sentences: what we're building and why}

## Files to Create

- `{filename}` — {what this file does}
- `{filename}` — {what this file does}

## Steps

1. {First thing to do — e.g., "Create main script with argument parsing"}
2. {Second thing — e.g., "Add geocoding function to look up city coordinates"}
3. {Third thing — e.g., "Add weather fetch function"}
4. {Fourth thing — e.g., "Add output formatting"}
5. {Fifth thing — e.g., "Add error handling for missing city / API failures"}
6. {Sixth thing — e.g., "Create tests"}

## Dependencies

- {library}: {what it's used for}

## How to Test

- `{command to run the tool}` — expected: {what should happen}
- `{command with bad input}` — expected: {graceful error message}
- `{command to run tests}` — expected: {all tests pass}
```

### 4. Create the plans directory if needed

Run: `mkdir -p .agents/plans`

## Output

- Confirm the plan file path
- Give a brief summary of the plan
- Suggest running `/execute .agents/plans/{filename}.md` next

## Keep It Simple

- The plan should fit on one screen
- Each step should be one clear action
- Don't overthink it — this is a small project
