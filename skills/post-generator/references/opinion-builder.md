# Opinion builder

Posts need a **stance**. Neutrality reads like documentation.

## Objective

Generate strong, defensible opinions readers can agree or disagree with — backed by reasoning, not attitude alone.

## Rules

- Avoid neutral mush ("it depends" without a when/why)
- Take a **clear** stance
- Support with reasoning (trade-offs, context, failure modes)
- Allow **nuance** without indecision — e.g. "Works when X; breaks when Y"

## Example

**Weak:**

> Microfrontends can be useful in some cases.

**Strong:**

> Microfrontends are often overused — and most teams adopt them too early without a real boundary problem. You get deployment independence at the cost of duplicated dependencies, inconsistent UX, and distributed debugging. Worth it when org structure truly matches product boundaries; expensive theater when it doesn't.

## Pairing

- Contrarian hooks ([hook-generator.md](hook-generator.md)) + opinion body = high engagement if earned
- If you cannot defend the opinion from experience, narrow the claim or switch to a **story** post instead

## Connection to frameworks

Fits "Most [role]s misunderstand X" and strong-opinion post types in [post-creation-engine.md](post-creation-engine.md).
