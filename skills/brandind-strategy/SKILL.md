---
name: branding-strategy
description: >
  Use this skill when the user asks for a "full strategy", "personal branding plan",
  "content strategy", "how should I position myself", "what should I be known for",
  "define my content pillars", "build my brand", or any request that involves
  defining their overall professional positioning across LinkedIn and CV. Also triggers
  for "career strategy", "how do I stand out", or "what makes me different".
metadata:
  version: "0.1.0"
---

# Personal Branding Strategy Engine

Define and build a coherent, differentiated personal brand for senior tech professionals. This is the strategy layer — it informs what goes into posts, CVs, and the LinkedIn profile. Run this first when working with a new user.

## What Good Positioning Is

Positioning is the answer to: **"What is this person the go-to for?"**

It's not a job title. It's not a list of skills. It's the specific intersection of:
- What they're genuinely good at
- What the market actually needs
- What they have credible experience to talk about

The narrower and more specific the positioning, the stronger it is.

## Phase 1: Build the User Profile

Before generating any strategy, establish:

| Field | Questions to ask |
|-------|-----------------|
| Experience | Years, roles, tech stack, industries touched |
| Strongest work | What's the most complex thing they've shipped? |
| Opinions | What do they believe that most engineers don't? |
| Career goal | What type of role, company, or seniority are they targeting? |
| Audience | Who should be finding their profile: recruiters, engineers, founders? |
| Current presence | What does their LinkedIn/CV say about them today? |

If the user has already provided this — use it. Don't re-ask.

## Phase 2: Define the Positioning Statement

Draft a 1–2 sentence positioning statement:

**Format:**
> [Name] is a [seniority + role] who specializes in [specific technical domain]. Known for [differentiating strength], they've [real proof point from experience].

**Example:**
> Guilherme is a Senior Frontend Engineer who specializes in real-time, AI-integrated product interfaces. Known for frontend architecture decisions and performance under complexity, he's shipped systems at companies across creator economy, PropTech, and HR tech.

This statement should drive everything else: the LinkedIn headline, the About section, the CV summary, and the content angles.

## Phase 3: Define Content Pillars

Identify 3–4 content pillars max. Each pillar should be:
- Grounded in real experience (not aspiration)
- Relevant to the target audience
- Specific enough to generate 10+ post ideas

**Pillar structure:**
```
Pillar name: [short label]
What it covers: [2–3 lines]
Example posts: [2–3 specific titles]
Target audience: [who engages with this]
```

**Track-specific examples:** Use `references/positioning-index.md` to open the right file for the user’s track — `frontend-positioning-examples.md`, `backend-positioning-examples.md`, `devops-positioning-examples.md`, or `ai-engineer-positioning-examples.md`. Use `references/positioning-common.md` for shared anti-patterns and the opinion test.

## Phase 4: Consistency Audit

Check that positioning is consistent across surfaces:
- CV headline ↔ LinkedIn headline: same seniority signal, compatible angles
- CV summary ↔ LinkedIn About: different tone, same positioning
- Post content ↔ experience bullets: posts should feel like commentary from someone who actually shipped that
- Skills listed ↔ posts written: no disconnect between claimed expertise and content credibility

## Phase 5: Deliver the Strategy

Output format:
1. **Positioning statement** (1–2 sentences)
2. **LinkedIn headline** (2–3 options, ranked)
3. **Content pillars** (3–4, with example post titles for each)
4. **Immediate actions** (3–5 specific changes to make today — headline, summary, one weak bullet, missing links)
5. **First post recommendation** (the highest-leverage post to write first based on current experience)

See `references/positioning-index.md` and the track files above; use `references/positioning-common.md` for rules that apply to every track.

## Phase 6: Save to Notion

After delivering the strategy, save the output to Notion:

1. Look up the user's workspace using `notion-search` — search for "[FirstName] - LinkedIn & CV Builder"
2. If no workspace exists, trigger the `notion-setup` skill first
3. Update the **👤 Profile** page with:
   - Positioning statement (callout block)
   - Content pillars (bulleted list)
   - LinkedIn headline options (numbered list)
   - Target roles / market context
   - Session date
4. Confirm to the user: "Strategy saved to your Notion workspace under 👤 Profile."

This ensures positioning decisions persist across sessions and can be referenced by the post-generator and cv-optimizer skills.