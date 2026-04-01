---
name: get-user-context
description: >
  Use this skill when onboarding a user, starting a profile or career session, or whenever
  the agent needs a complete picture of the user before CV, LinkedIn, posts, or strategy work.
  Triggers for "set up my profile", "get to know me", "what do you need from me",
  "onboarding", "my background", or before running other plugin skills without prior context.
  Notion MCP is required for persistence; guide the user to configure `/mcp` in chat when needed.
metadata:
  version: "0.3.0"
---

# Get User Context

Collect everything needed to personalize **software professionals** (any track: frontend, backend, platform/DevOps/SRE, AI/ML, full-stack, etc.). This skill runs **before** deep CV, LinkedIn, or content work when context is missing or stale.

## Step 0: Verify Notion MCP + Check Existing Context (mandatory gate)

**This must run before anything else in this skill.**

### 0a — Verify Notion MCP connection

1. Attempt a `notion-search` call with a generic query (e.g. "LinkedIn & CV Builder") to test if the connector is live.
2. **If the call succeeds**: Notion is connected. Record this as an active connector in the session context — all subsequent saves in this session will use it. Proceed to Step 0b.
3. **If the call fails or tools are unavailable**: **Stop here. Do not ask any profile questions.** Tell the user:

> "Before we get started, I need Notion connected — this plugin uses it to keep your CV versions, profile drafts, and posts between sessions so nothing gets lost.
>
> Here's how to set it up:
> - **In the chat**: run `/mcp`, find **Notion** in the list, and complete OAuth when prompted.
> - **Or in your terminal**: `claude mcp add --transport http notion https://mcp.notion.com/mcp`
>
> Once you've done that, just let me know and we'll continue from here."

Do not proceed until the user confirms and a `notion-search` call actually succeeds. If it still fails after their confirmation, troubleshoot — wrong account, pop-up blocked, missing workspace permission — before moving on. Never assume it worked.

### 0b — Check for existing profile context in Notion

Once Notion is confirmed connected, **before asking a single question**, check if a profile already exists:

1. Fetch the **👤 Profile** page (`334dd4dd-5a6e-818f-b458-d15454554d89`) directly. If it returns valid content with Identity, Career Snapshot, and Tech Stack sections, context already exists.
2. **If context exists**: Read the page and summarise what you found:
   > "I already have your profile saved — here's a quick summary: [name, current role, years exp, track, target roles, last updated date]. Anything to update since then? Or shall I use this and move on?"
   - If the user says nothing has changed: load the profile data into session context and skip to Step 1 (ask for CV/LinkedIn if needed for the specific downstream task).
   - If the user wants to update specific fields: only ask about the changed parts, then patch the Notion Profile page.
3. **If context is missing or empty**: Run the full questionnaire flow below.

> This step is fast — one fetch call. Never skip it; it prevents re-asking the user for information they've already provided.

---

## Required artifacts (ask explicitly)

1. **CV / résumé** — Ask the user to upload a file **or** paste the full text. Do not proceed with profile-specific rewrites until you have at least one of these.
2. **LinkedIn profile URL** — Ask for the public profile link (e.g. `https://www.linkedin.com/in/...`). If they cannot share it, note "declined / not available" and continue with CV + answers.

If the user already provided CV or LinkedIn earlier in the thread, **do not re-ask** — acknowledge what you have and fill gaps only.

## Question flow

1. Notion MCP verified (Step 0), then request **CV** and **LinkedIn URL** (see above).
2. Ask which **primary track** best describes them (or infer from CV and confirm): e.g. frontend, backend, DevOps/platform, AI/ML, mobile, data engineering, general backend + frontend, etc.
3. Run through **`references/user-context-questionnaire.md`**: use the **Universal** section for everyone, then the **add-on** section that matches their track (or the closest match). Skip irrelevant questions; do not ask the same thing twice if the CV already answers it.
4. End with a **short summary** of what you captured and ask for corrections.

## Writing Tone

When writing anything on behalf of the user — summaries, profile notes, positioning — keep it professional but grounded. Write the way a sharp, experienced engineer would actually talk: specific, direct, no filler. Avoid anything that sounds like it came from a template — no "results-driven professional", no "passionate about technology", no hollow superlatives.

## Rules

- Stay **generic to software engineering** — avoid assuming frontend-only unless the user says so.
- Prefer **specifics** (years, scale, stack, domain) over adjectives ("passionate", "senior").
- If the user is brief, ask **one follow-up** per gap instead of a long form in one message.
- Never invent facts; if something is unknown, mark it as unknown.

## Downstream use

Captured context feeds: CV optimizer, profile optimizer, post generator, trend analyzer, cover letter generator, Notion profile seeding. **Positioning** reference examples (by track) live under `references/` — use after context is clear; see [references/positioning-index.md](references/positioning-index.md).

## Saving to Notion + Local Backup

Notion MCP must already be working (confirmed in Step 0). If the workspace does not exist yet, run **`notion-setup`** first.

1. Search for `[FirstName] - LinkedIn & CV Builder`.
2. Update the **👤 Profile** page with: LinkedIn URL, link or summary note for CV, answers to key questionnaire fields (role track, years, target roles, stack, audience), and session date.
3. Confirm what was saved.

Also save a local `.md` backup to the workspace folder:
- File path: `profile/user-context-[YYYY-MM-DD].md`
- Structure: Name, Track, Years of experience, Stack, Target roles, Positioning notes, Session date.
- Use the Write tool to create this file.

If Notion tools fail, return to Step 0 — do not claim success without a successful tool response.
