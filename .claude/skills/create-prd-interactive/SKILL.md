---
description: Create a Product Requirements Document through an adaptive discovery interview
argument-hint: [output-filename]
---

# Create PRD: Interactive Discovery

## Overview

Generate a comprehensive Product Requirements Document (PRD) by conducting an adaptive, multi-turn discovery interview with the user. Rather than asking all questions upfront, explore the problem space iteratively — using each answer to shape the next question.

## Output File

Write the PRD to: `$ARGUMENTS` (default: `PRD.md`)

## Discovery Interview

Conduct the interview using AskUserQuestion. Ask ONE topic at a time. Use the user's responses to decide what to ask next. Do not front-load all questions — let the conversation flow naturally.

### Round 1: Problem & Vision

Start here. Ask about:
- What problem does this product solve? What's the pain point or opportunity?
- Has the user already described the product in conversation? If so, summarize your understanding and ask them to confirm or correct it.

### Round 2: Users & Context

Based on Round 1, explore:
- Who are the primary users? What is their technical comfort level?
- If the user described multiple user types, ask about priorities and differences between them.
- If the problem described is vague, ask for concrete scenarios — "Can you walk me through a typical use case?"
- If the problem is technical, ask about existing solutions and why they fall short.

### Round 3: Solution Shape

Based on what you've learned:
- Propose 2-3 possible MVP approaches and ask which direction resonates.
- Ask about technology constraints or preferences (languages, frameworks, platforms, hosting).
- If the user has strong opinions, follow their lead. If they're unsure, make a recommendation and explain why.

### Round 4: Features & Scope

Based on the chosen approach:
- Suggest a list of candidate features grouped by category. Ask the user to confirm which are in-scope for MVP and which should be deferred.
- For each in-scope feature, ask one clarifying question if the requirements are ambiguous.
- Ask about integrations, APIs, or third-party services that are needed.

### Round 5: Success & Constraints

- Ask how success will be measured — what does "working" look like?
- Ask about any hard constraints: deadlines, budget, team size, compliance requirements.
- Ask about deployment: where will this run? Who operates it?

### Adaptive Follow-Up Rules

Apply these throughout the interview:
- **Shallow answer?** Probe deeper. ("Can you give me a specific example?", "What happens when that goes wrong?")
- **Rich, detailed answer?** Acknowledge it and move on. Don't re-ask what's already clear.
- **User contradicts an earlier answer?** Surface the contradiction gently and ask which version is correct.
- **User volunteers information ahead of schedule?** Capture it and skip the corresponding future question.
- **User says "I don't know" or "you decide"?** Make a reasonable recommendation, state your reasoning, and ask if they're comfortable with it.

### Stopping Condition

Stop the interview when you are confident you can fill all required PRD sections with specific, actionable content — not vague placeholders. If you're unsure about a section, ask one more targeted question rather than guessing.

### Pre-Generation Summary

Before writing the PRD, present a structured summary of your understanding back to the user:

1. **Problem:** One-sentence summary
2. **Users:** Who they are
3. **MVP approach:** What you'll build
4. **Key features:** Bulleted list of in-scope items
5. **Tech stack:** Proposed technologies
6. **Success criteria:** How we'll know it works

Ask the user to confirm or correct this summary. Do not generate the PRD until they approve.

## PRD Structure

Create a well-structured PRD with the following sections. Adapt depth and detail based on what you learned in the interview:

### Required Sections

**1. Executive Summary**
- Concise product overview (2-3 paragraphs)
- Core value proposition
- MVP goal statement

**2. Mission**
- Product mission statement
- Core principles (3-5 key principles)

**3. Target Users**
- Primary user personas
- Technical comfort level
- Key user needs and pain points

**4. MVP Scope**
- **In Scope:** Core functionality for MVP
- **Out of Scope:** Features deferred to future phases
- Group by categories (Core Functionality, Technical, Integration, Deployment)

**5. User Stories**
- Primary user stories (5-8 stories) in format: "As a [user], I want to [action], so that [benefit]"
- Include concrete examples for each story
- Add technical user stories if relevant

**6. Core Architecture & Patterns**
- High-level architecture approach
- Directory structure (if applicable)
- Key design patterns and principles
- Technology-specific patterns

**7. Tools/Features**
- Detailed feature specifications
- If building an agent: Tool designs with purpose, operations, and key features
- If building an app: Core feature breakdown

**8. Technology Stack**
- Backend/Frontend technologies with versions
- Dependencies and libraries
- Optional dependencies
- Third-party integrations

**9. Security & Configuration**
- Authentication/authorization approach
- Configuration management (environment variables, settings)
- Security scope (in-scope and out-of-scope)
- Deployment considerations

**10. API Specification** (if applicable)
- Endpoint definitions
- Request/response formats
- Authentication requirements
- Example payloads

**11. Success Criteria**
- MVP success definition
- Functional requirements
- Quality indicators
- User experience goals

**12. Implementation Phases**
- Break down into 3-4 phases
- Each phase includes: Goal, Deliverables, Validation criteria

**13. Future Considerations**
- Post-MVP enhancements
- Integration opportunities
- Advanced features for later phases

**14. Risks & Mitigations**
- 3-5 key risks with specific mitigation strategies

**15. Appendix** (if applicable)
- Related documents
- Key dependencies with links
- Repository/project structure

## Instructions

### 1. Extract Requirements
- Draw from the interview conversation AND any prior conversation context
- Identify explicit requirements and implicit needs
- Note technical constraints and preferences
- Capture user goals and success criteria

### 2. Synthesize Information
- Organize requirements into appropriate sections
- Where details are missing despite the interview, state your assumption explicitly
- Maintain consistency across sections
- Ensure technical feasibility

### 3. Write the PRD
- Use clear, professional language
- Include concrete examples and specifics
- Use markdown formatting (headings, lists, code blocks, checkboxes)
- Add code snippets for technical sections where helpful
- Keep Executive Summary concise but comprehensive

### 4. Quality Checks
- All required sections present
- User stories have clear benefits
- MVP scope is realistic and well-defined
- Technology choices are justified
- Implementation phases are actionable
- Success criteria are measurable
- Consistent terminology throughout
- No vague placeholders — every section has specific content from the interview

## Style Guidelines

- **Tone:** Professional, clear, action-oriented
- **Format:** Use markdown extensively (headings, lists, code blocks, tables)
- **Specificity:** Prefer concrete examples over abstract descriptions
- **Assumptions:** Mark any assumptions clearly so the user can spot and correct them
- **Length:** Comprehensive but scannable

## Output Confirmation

After creating the PRD:
1. Confirm the file path where it was written
2. Provide a brief summary of the PRD contents
3. Highlight any assumptions made due to missing information
4. Suggest next steps (e.g., review, refinement, implementation planning)

## Notes

- Adapt section depth based on available details
- For highly technical products, emphasize architecture and technical stack
- For user-facing products, emphasize user stories and experience
- This skill contains the complete PRD template structure — no external references needed
