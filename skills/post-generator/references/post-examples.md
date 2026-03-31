# Post examples — annotated

Full workflow and principles: [post-index.md](post-index.md).

---

## Type: Strong Opinion

```
Most frontend engineers treat TypeScript as a spell-checker.

It's not. It's a design tool.

The type system doesn't protect you at runtime.
It forces you to think about contracts before you write logic.

When your types are loose, it's not a TypeScript problem.
It's a thinking problem.

What's the hardest thing you've modeled in TypeScript?
```

**Why it works:**
- Hook creates immediate tension ("treat X as Y") — it implies the reader might be doing it wrong
- Short, punchy contrast in the second line
- Ends with a question that only someone technical would answer — filters for quality engagement

---

## Type: Lesson Learned

```
I spent 3 months building the wrong thing.

We had a beautiful component library. Storybook. Design tokens. The works.

Nobody used it.

Not because the components were bad.
Because we built it in isolation, without the people who would have to ship with it.

The lesson wasn't technical.

Build alongside, not for.
```

**Why it works:**
- Opens with a clean failure — no hedging
- Tells a real story in minimal words
- The insight is specific, not a generic "communicate more"
- Ends with a punchline that's quotable

---

## Type: Real-World Breakdown

```
We built a real-time multiplayer canvas editor.

Here's what broke first: state synchronization.

Not network. Not rendering. State.

When 3 users are dragging elements simultaneously, your mental model of "current state" stops being valid.

We rebuilt it around event sourcing + optimistic UI.
Every action is a patch. Every client reconstructs truth from the log.

Hard problem. Elegant solution. Took 6 weeks to unlearn the obvious approach.
```

**Why it works:**
- Specific product, specific problem — not abstract
- Subverts expectations ("not network, not rendering")
- Shows architectural thinking, not just code
- "Unlearn the obvious approach" is a strong close

---

## Type: Contrarian Take

```
SSR doesn't make your app faster.

It makes your *first paint* faster.

These are not the same thing.

If you have a heavily interactive dashboard, SSR adds complexity, increases server cost, and can make interactions feel slower if you're not hydrating carefully.

Know what you're optimizing for before choosing your rendering strategy.

Most apps don't need SSR. They need better caching.
```

**Why it works:**
- Opens by challenging a widely held belief
- Immediately qualifies it with precision (first paint vs. overall performance)
- Gives a real trade-off, not just "it depends"
- Ends with an actionable redirect

---

## Hooks — Swipe File

Strong opening lines you can adapt:

- "We deleted 40% of our frontend codebase. Performance improved."
- "I've reviewed 200+ PRs this year. Most fail for the same reason."
- "Stop blaming JavaScript for your app's performance issues."
- "The best architecture decision I ever made was not an architecture decision."
- "TypeScript won't save you. Here's what will."
- "Real-time UIs are not hard because of the real-time part."
- "Nobody tells you that 80% of a senior engineer's job is managing complexity they didn't create."