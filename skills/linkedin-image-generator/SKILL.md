---
name: linkedin-image-generator
description: >
  Use this skill when the user asks to "create an image for my LinkedIn post", "generate a
  visual for this post", "make a cover image", "design a post graphic", or any request to
  produce a visual asset to accompany a LinkedIn post. Also triggers for "post thumbnail",
  "LinkedIn banner for post", or "visual for my content".
metadata:
  version: "0.1.0"
---

# LinkedIn Image Generator

Create clean, professional visual assets to accompany LinkedIn posts for senior tech professionals. The goal is an image that reinforces the post's message and earns attention in the feed — not a generic stock photo or a cluttered infographic.

## When to use this skill

- The user has a post (drafted or finalized) and wants a visual to pair with it
- The user wants a branded quote card, diagram summary, or concept visual
- The user wants a simple visual that elevates a text post without distracting from it

## Design Principles

LinkedIn feed visuals are consumed at small size, then expanded. Design for both:
- **Thumb-stop clarity**: readable headline or concept at a glance
- **Expanded value**: enough content that expanding it feels worthwhile

### What works on LinkedIn

| Image type | When to use |
|------------|-------------|
| Bold text card | Strong opinion or contrarian take — the text IS the content |
| Concept diagram | Architecture decision, system comparison, or technical breakdown |
| Quote card | Memorable single sentence from the post — not a full paragraph |
| Before/After | Showing a transformation: bad bullet → good bullet, bad code → good code |
| Numbered list visual | 3–5 key points that map to a structured post |

### What to avoid
- Stock photos — generic, adds nothing, signals low effort
- Overly designed infographics — hard to read, looks like marketing material
- Text-heavy images that duplicate the post verbatim
- Bright gradients or clashing colors that look unprofessional

## Image Specs for LinkedIn

- **Standard post image**: 1200 × 627px (1.91:1 ratio)
- **Square post image**: 1080 × 1080px (cleaner in mobile feed)
- **Carousel slide** (document post): 1080 × 1080px or 1920 × 1080px per slide

Use square (1080×1080) as the default unless the user specifies otherwise.

## Generation Process

### Step 1: Understand the post
Read the post content from context (or ask the user to paste it). Identify:
- The core message in one sentence
- The post type (opinion, lesson, technical breakdown, story)
- The tone (confident, reflective, analytical)

### Step 2: Choose the image type
Select the most appropriate format from the table above based on post type.

### Step 3: Define content for the image
Extract or write:
- **Headline**: 6–10 words max — the core claim or hook
- **Sub-text** (optional): 1–2 supporting lines
- **Visual element** (optional): a simple diagram, icon, or structural element

### Step 4: Generate the image
Use the canvas-design skill to produce the image. Follow these parameters:

**Color palette**: Professional, muted — dark backgrounds with light text work well on LinkedIn. Avoid neon or overly vibrant colors. Default to a dark navy or charcoal background with white/light text unless the user has a preference.

**Typography**: Clean sans-serif. Large headline. Hierarchy matters more than decoration.

**Branding** (optional): If the user has a personal brand color or font preference noted in their profile context, use it.

**Format**: PNG, square (1080×1080) by default.

After generating, show the image and ask:
> "Does this work? I can adjust the copy, colors, layout, or style."

### Step 5: Save locally

Save the generated image to the workspace folder:
- File path: `linkedin/images/[YYYY-MM-DD]-[slug].png`
- Use the Write or Bash tool to move/copy the generated file to this path

## Carousel Posts (Document format)

For carousel-style posts, generate slides as a set:
- Slide 1: Hook / Title
- Slides 2–N: One key point per slide (max 5–7 slides)
- Final slide: Summary + call to action / follow prompt

Keep each slide to one idea. Less text per slide = more clarity.

## Saving to Notion

After the user approves an image, offer to link it to the associated post draft in Notion:

> "Want me to note this image in your post draft in Notion?"

If yes:
1. Search for "[FirstName] - LinkedIn & CV Builder"
2. Find the relevant post entry in the **Posts** database
3. Add a **Notes** entry: "Image saved locally at `linkedin/images/[filename]`"
4. Confirm the update

If Notion MCP is not connected, skip Notion and confirm the local save only.
