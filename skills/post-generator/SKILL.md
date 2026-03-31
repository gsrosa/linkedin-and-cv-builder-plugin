---
name: post-generator
description: >
  Use this skill when the user asks to "create a LinkedIn post", "write a post about X",
  "turn this idea into a post", "make this go viral", "generate post ideas", or wants
  help writing any LinkedIn content. Also triggers for "carousel structure", "post hook",
  "LinkedIn content", or "draft a post".
metadata:
  version: "0.1.0"
---

# LinkedIn Post Generator

Generate high-leverage, differentiated LinkedIn posts for senior tech professionals. The goal is not volume — it is sharpness, credibility, and scroll-stopping clarity.

**References:** `references/post-index.md` — creation engine, hooks, insight extraction, opinions, critic, and annotated examples.

## Post types and when to use them

| Type | Trigger | Example topic |
|------|---------|---------------|
| Technical insight | Specific engineering lesson | "Why we stopped using X for Y" |
| Lesson learned | Mistake or changed mind | "I refactored our monorepo. I was wrong about monorepos." |
| Strong opinion | Contrarian take | "TypeScript doesn't make your code safer. Your discipline does." |
| Real-world breakdown | Shipped something complex | "We built a real-time canvas editor. Here's what broke first." |
| Architecture decision | Trade-off worth explaining | "We chose X for our dashboard. Not for the reasons you'd expect." |

## Input handling

**Topic only** → Apply the best-fit framework from `post-creation-engine.md`, generate 2 options, let them choose.

**Rough draft** → Strengthen hook, cut fluff, sharpen close — do not only polish.

**Vague idea** → Ask one targeted question: "What is the specific thing you learned or want to challenge?"

**Post ideas only** → 3–5 strong options — each with topic + angle + why it works now — not 20 weak titles.

## Tone

Direct. Confident. Slightly opinionated. Never corporate. Senior engineer talking to peers, not HR writing a press release.

## Saving to Notion

After generating a post the user is happy with, offer to save it:

> "Want me to save this to your Notion drafts?"

If yes:

1. Search for "[FirstName] - LinkedIn & CV Builder" using `notion-search`
2. Navigate to the **Posts** database under the LinkedIn section
3. Create a new database entry:
   - **Title**: First 6–8 words of the post
   - **Status**: Draft
   - **Type**: Detected content type (Technical / Opinion / Lesson Learned / Architecture / Career)
   - **Hook**: First line of the post
   - **Date**: Today
4. Add the full post text as a child page of the database entry
5. Confirm: "Saved to Notion → LinkedIn / Posts as a draft."

If no workspace exists yet, suggest running the Notion setup first.
