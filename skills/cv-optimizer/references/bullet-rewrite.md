# Rewrite a single bullet

Prerequisites: [bullet-analyze.md](bullet-analyze.md), [bullet-patterns.md](bullet-patterns.md). More examples: [bullet-rewrites.md](bullet-rewrites.md).

## Objective

Transform a weak bullet into a strong, senior-level bullet.

## Rules

- Start with a strong action verb
- Focus on outcome over activity
- Include metrics when possible
- Add context (problem being solved)
- Show technical reasoning when relevant

## Enhancements

**Add metrics**

- Use approximations if needed (`~`, `+`, `-`)
- Never invent unrealistic numbers

**Add context**

- What problem was being solved?

**Add decision-making**

- Why this approach?

**Add scale**

- Users, data, complexity

## Tone

- Direct
- Concise
- Technical when needed
- No fluff

## Output (rewrite phase)

- Final rewritten bullet
- Optional: short explanation of improvement

---

## Final output format (deliver to user)

Structure each bullet rewrite like this:

**Original:**

> {original bullet}

**Analysis:**

- {issues}
- {missing elements}

**Pattern applied:**

- {pattern(s)}

**Rewritten:**

> {final improved bullet}

### Rules

- Keep it concise
- No unnecessary explanations
- Focus on clarity and impact

---

## Reference library (mini examples)

### Trade-off

**Before:**

> Implemented SSR using Next.js

**After:**

> Introduced SSR for SEO-critical pages while avoiding full app SSR to prevent unnecessary server load, balancing crawlability and performance

### Constraint

**Before:**

> Built a design system

**After:**

> Built a design system enabling incremental adoption without blocking legacy components, avoiding a full rewrite under tight delivery constraints

### Debugging / diagnosis

**Before:**

> Fixed performance issues

**After:**

> Diagnosed and resolved performance bottlenecks caused by excessive re-renders, reducing UI latency under high-frequency updates

### System thinking

**Before:**

> Built notification system

**After:**

> Designed a scalable notification system supporting real-time and async delivery with retry and failure handling mechanisms
