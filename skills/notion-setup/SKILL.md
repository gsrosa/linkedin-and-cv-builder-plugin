---
name: notion-setup
description: >
  Use this skill when the user asks to "set up Notion", "create my Notion workspace",
  "initialize my knowledge base", "connect to Notion", or when any other skill needs
  to save data and no workspace has been found yet. Also triggers at the start of a
  get-user-context or profile session to check if a workspace exists. Requires Notion
  via MCP (configured during the chat if missing).
metadata:
  version: "0.1.0"
---

# Notion Workspace Setup

Create and maintain the user's personal LinkedIn & CV Builder workspace in Notion. This is the persistent knowledge base that all other skills read from and write to.

## Prerequisites check (Notion MCP — required)

This plugin **requires** Notion as the knowledge base. The repo ships `.mcp.json` with Notion’s hosted MCP (`https://mcp.notion.com/mcp`). The user must complete setup **during the chat** if tools are not available yet.

1. **Try** a Notion tool (e.g. search) to verify MCP is connected.
2. **If it fails or tools are missing**, stop and walk the user through configuration — do **not** pretend saves will work:

   - Ask them to open **`/mcp`** in Claude Code (or run: `claude mcp add --transport http notion https://mcp.notion.com/mcp` if they prefer CLI).
   - Tell them to **add** the Notion server if it is not listed, then complete **OAuth** and grant workspace access when prompted.
   - Say clearly: persistence for CV, posts, and profile drafts **depends** on this step.

3. **After** they confirm OAuth is done, **retry** the Notion call. If it still fails, troubleshoot (wrong account, blocked pop-up, missing Notion workspace permission) before continuing.

4. Only when Notion tools work: proceed to Step 1 (workspace search / create).

If the user refuses to connect Notion, explain that this plugin is designed around a shared Notion workspace and they should connect it to continue; do not claim data was saved to Notion without a successful API/tool response.

## Step 1: Check for Existing Workspace

Search Notion for a page matching the pattern `[FirstName] - LinkedIn & CV Builder`.

Use: `notion-search` with the query "[FirstName] - LinkedIn & CV Builder"

- **If found**: Return the page ID and structure map. Do not recreate. Announce: "Found your existing workspace — ready to use."
- **If not found**: Proceed to Step 2.

To determine the user's first name:
- Check conversation context (they may have introduced themselves or shared a CV)
- If unclear, ask: "What name should I use for your Notion workspace?"

## Step 2: Create Root Page

Create the main workspace page:

```
Title: [FirstName] - LinkedIn & CV Builder
Icon: 🗂️
```

Use `notion-create-pages` with a parent of the user's default workspace root.

Store the returned page ID as `ROOT_PAGE_ID`.

## Step 3: Create Section Pages

Create three child pages under ROOT_PAGE_ID:

### 👤 Profile
```
Title: 👤 Profile
Parent: ROOT_PAGE_ID
```
This page stores: positioning statement, content pillars, tech stack, career goals, target roles, and any data extracted from the user's CV or LinkedIn profile.

### 💼 LinkedIn
```
Title: 💼 LinkedIn
Parent: ROOT_PAGE_ID
```
Parent page for all LinkedIn-related databases.

### 📄 CV
```
Title: 📄 CV
Parent: ROOT_PAGE_ID
```
Parent page for all CV-related databases and versions.

Store each returned page ID: `PROFILE_PAGE_ID`, `LINKEDIN_PAGE_ID`, `CV_PAGE_ID`.

## Step 4: Create Databases

### Posts Database (under LinkedIn page)

Create with `notion-create-database`, parent: `LINKEDIN_PAGE_ID`

```
Title: Posts
Properties:
  - Title (title) — post title or hook
  - Status (select): Draft | Ready | Published | Archived
  - Type (select): Technical | Opinion | Lesson Learned | Architecture | Career
  - Date (date)
  - Hook (rich_text) — first line of the post
  - Notes (rich_text) — context, inspiration, or performance notes
```

### Profile Versions Database (under LinkedIn page)

Create with `notion-create-database`, parent: `LINKEDIN_PAGE_ID`

```
Title: Profile Versions
Properties:
  - Title (title) — version label, e.g. "v2 — AI focus"
  - Date (date)
  - Headline (rich_text)
  - Summary Snippet (rich_text) — first 2 lines of About section
  - Target Role (rich_text)
  - Notes (rich_text)
```

### CV Versions Database (under CV page)

Create with `notion-create-database`, parent: `CV_PAGE_ID`

```
Title: CV Versions
Properties:
  - Title (title) — version label, e.g. "v3 — Senior remote, US-focused"
  - Date (date)
  - Target Role (rich_text)
  - Key Changes (rich_text) — what changed from previous version
  - Notes (rich_text)
```

## Step 5: Create Current CV Page

Under `CV_PAGE_ID`, create a child page:

```
Title: 📌 Current CV
```

If CV content is available in context (user uploaded a CV earlier in the session), populate this page with the extracted content structured as:
- Summary section
- Experience entries (company, role, dates, bullets)
- Skills
- Education

## Step 6: Populate Profile Page

If any of the following data is available in the conversation context, write it to the Profile page:

- **Name** — from CV or introduction
- **Current title** — from CV headline or conversation
- **Years of experience** — from CV
- **Tech stack** — from CV skills section
- **Current positioning** — from CV summary or earlier strategy work
- **Content pillars** — if already defined in conversation or earlier sessions
- **Target market / roles** — from conversation
- **Career goals** — from conversation

Format the Profile page as a structured document, not a flat dump. Use Notion headings and sections.

## Step 7: Confirm and Report

After setup, report back with a clean summary:

```
✅ Notion workspace created: [FirstName] - LinkedIn & CV Builder

📁 Structure:
  👤 Profile — your positioning and profile data
  💼 LinkedIn/
      Posts — post drafts and published content
      Profile Versions — headline and summary iterations
  📄 CV/
      Current CV — your latest CV content
      CV Versions — version history by target role
```

## Workspace Lookup (for other skills)

When any other skill needs to save to Notion, use this lookup flow:

1. Search for `[FirstName] - LinkedIn & CV Builder` using `notion-search`
2. If found, navigate to the relevant child page/database
3. If not found, trigger the setup flow first, then save

Never hardcode page IDs across sessions — always resolve them via search.

See `references/notion-data-map.md` for the full mapping of what each skill saves and where.