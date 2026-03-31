---
name: get-user-context
description: >
  Use this skill when onboarding a user, starting a profile or career session, or whenever
  the agent needs a complete picture of the user before CV, LinkedIn, posts, or strategy work.
  Triggers for "set up my profile", "get to know me", "what do you need from me",
  "onboarding", "my background", or before running other plugin skills without prior context.
metadata:
  version: "0.1.0"
---

# Get User Context

Collect everything needed to personalize **software professionals** (any track: frontend, backend, platform/DevOps/SRE, AI/ML, full-stack, etc.). This skill runs **before** deep CV, LinkedIn, or content work when context is missing or stale.

## Required artifacts (ask explicitly)

1. **CV / résumé** — Ask the user to upload a file **or** paste the full text. Do not proceed with profile-specific rewrites until you have at least one of these.
2. **LinkedIn profile URL** — Ask for the public profile link (e.g. `https://www.linkedin.com/in/...`). If they cannot share it, note “declined / not available” and continue with CV + answers.

If the user already provided CV or LinkedIn earlier in the thread, **do not re-ask** — acknowledge what you have and fill gaps only.

## Question flow

1. Request **CV** and **LinkedIn URL** first (see above).
2. Ask which **primary track** best describes them (or infer from CV and confirm): e.g. frontend, backend, DevOps/platform, AI/ML, mobile, data engineering, general backend + frontend, etc.
3. Run through **`references/user-context-questionnaire.md`**: use the **Universal** section for everyone, then the **add-on** section that matches their track (or the closest match). Skip irrelevant questions; do not ask the same thing twice if the CV already answers it.
4. End with a **short summary** of what you captured and ask for corrections.

## Rules

- Stay **generic to software engineering** — avoid assuming frontend-only unless the user says so.
- Prefer **specifics** (years, scale, stack, domain) over adjectives (“passionate”, “senior”).
- If the user is brief, ask **one follow-up** per gap instead of a long form in one message.
- Never invent facts; if something is unknown, mark it as unknown.

## Downstream use

Captured context feeds: CV optimizer, profile optimizer, post generator, trend analyzer, Notion profile seeding. **Positioning** reference examples (by track) live under `references/` — use after context is clear; see [references/positioning-index.md](references/positioning-index.md).

## Saving to Notion

If Notion is available and a workspace exists (see `notion-setup`):

1. Search for `[FirstName] - LinkedIn & CV Builder`.
2. Update the **👤 Profile** page with: LinkedIn URL, link or summary note for CV, answers to key questionnaire fields (role track, years, target roles, stack, audience), and session date.
3. Confirm what was saved.

If no workspace exists, offer Notion setup after context is collected.
