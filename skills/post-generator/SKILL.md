---
name: post-generator
description: >
  Use this skill when the user asks to "create a LinkedIn post", "write a post about X",
  "turn this idea into a post", "make this go viral", "generate post ideas", or wants
  help writing any LinkedIn content. Also triggers for "carousel structure", "post hook",
  "LinkedIn content", or "draft a post".
metadata:
  version: "0.3.0"
---

# LinkedIn Post Generator

Generate high-leverage, differentiated LinkedIn posts for senior tech professionals. The goal is not volume — it is sharpness, credibility, and scroll-stopping clarity.

**References:** `references/post-index.md` — creation engine, hooks, insight extraction, opinions, critic, and annotated examples.

## Writing Tone

Posts must sound like a real engineer wrote them — not like AI generated them, not like a marketing team polished them. Direct. Specific. A slight edge. The kind of post where you think "this person actually knows what they're talking about."

No: "In today's fast-paced tech landscape, it's more important than ever to..."
No: "As a senior engineer, I've learned that..."
No: Hollow openers, empty wisdom, or anything that could have been written without the specific experience behind it.

Yes: Start mid-thought. Make a specific claim. Say something most people won't say.

The test: could this post have been written by someone without the actual experience to back it up? If yes, it needs to be sharper.

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

## Post Confirmation → Auto Image Generation

**When the user confirms the post is final** (e.g. "yes, this one", "let's go with this", "looks good", "this is it"), immediately proceed to image generation — do not wait for a separate request. Say:

> "Great — generating the visual for this now."

Then run the full image generation flow:

### Determine image format
Based on the post type, decide automatically:

| Post type | Recommended format |
|-----------|-------------------|
| Technical insight / Architecture decision | Concept diagram or numbered list visual |
| Lesson learned / Story | Bold text card with the key line |
| Strong opinion | Bold text card — the opinion IS the image |
| Real-world breakdown with 4+ distinct points | Carousel (document post, 4–6 slides) |
| Short punchy post (under 200 words) | Single image — bold text card or quote card |

For carousel posts, generate each slide as a separate image:
- Slide 1: Hook / Title (same as post hook)
- Slides 2–N: One key point per slide (3–5 content slides max)
- Final slide: Summary line + "Follow for more [specific topic]" CTA

### Generate the image(s)
Use the **canvas-design** skill to generate the image(s). Pass these parameters:
- **Dimensions**: 1080×1080px (square, default for mobile feed)
- **Style**: Dark background (charcoal or dark navy), white/light text, clean sans-serif, minimal decoration
- **Content**: Headline (6–10 words from post hook), optional 1–2 sub-lines
- **Personal brand**: If the user has a preferred color or font from their profile context, use it

Show each image to the user after generation:
> "Here's the visual. I can adjust copy, colors, layout, or turn this into a carousel."

Do not save anything until the image is approved. If the user requests changes, regenerate before saving.

## Saving to Notion + Local Files (after post + image confirmed)

Once the user confirms both post text and image:

**1. Save to Notion:**
1. Search for "[FirstName] - LinkedIn & CV Builder" using `notion-search`
2. Navigate to the **Posts** database under the LinkedIn section
3. Create a new database entry:
   - **Title**: First 6–8 words of the post
   - **Status**: Draft
   - **Type**: Detected content type (Technical / Opinion / Lesson Learned / Architecture / Career)
   - **Hook**: First line of the post
   - **Date**: Today
   - **Has Image**: Yes (note the local file path)
4. Add the full post text as a child page of the database entry
5. Confirm: "Saved to Notion → LinkedIn / Posts as a draft."

**2. Save locally** — create all files in the workspace folder using the Write tool:
- Post text: `linkedin/posts/[YYYY-MM-DD]-[slug].md`
  - Content: frontmatter (type, hook, date, image path), then full post text
- Single image: `linkedin/images/[YYYY-MM-DD]-[slug].png`
- Carousel (if applicable): `linkedin/images/[YYYY-MM-DD]-[slug]-slide-01.png`, `…-slide-02.png`, etc.

Confirm all files saved:
> "Saved: post text to `linkedin/posts/[filename].md` + image to `linkedin/images/[filename].png`."

If Notion MCP is not connected, skip Notion and confirm local saves only. If no workspace exists yet, run the Notion setup skill first.
