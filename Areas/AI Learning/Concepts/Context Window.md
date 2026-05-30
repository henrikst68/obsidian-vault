---
type: concept
phase: 1
created: '2026-05-13'
---
# Context Window

> The maximum number of [[Token|tokens]] the model can see at once — system prompt, conversation history, attachments, and the response it's currently generating, all combined.

## Why it matters

This is the single hardest constraint in working with LLMs. Everything you put in (instructions, examples, documents, prior turns) competes for the same budget as everything the model outputs. Run out and either earlier turns get dropped or the call fails entirely.

It also turns out **quality degrades long before the limit**. A 200k-token context window doesn't mean 200k tokens of useful attention. Models pay much more attention to the start and end of the context than the middle ("lost in the middle"). Stuffing more in doesn't always help and can hurt.

## Mental model

Imagine the model has a single sheet of paper. Everything it knows about *this specific conversation* has to fit on that sheet. The sheet is big — but not infinite, and the model's eyes drift to the top and bottom edges more than the middle.

Numbers worth knowing:
- Claude Sonnet/Opus: 200k tokens (~150k words, ~300 pages of text)
- GPT-4o: 128k
- Gemini 1.5 Pro: up to 2M (much larger, but the "lost in the middle" problem gets worse)

## Common gotchas

- "Just give it everything" is wasteful and often *worse* than a curated subset.
- Important instructions belong at the top OR the bottom — the middle gets fuzzy.
- Long conversations silently get more expensive every turn, because the whole history travels with each call.
- The output you're waiting for counts against the window too. A 200k-window model writing a 10k response only has 190k for inputs.

## Related

- [[Token]]
- [[RAG]] — the alternative to stuffing the context
- [[System vs User Prompt]]

## Sources

- "Lost in the Middle: How Language Models Use Long Contexts" (Liu et al., 2023) — the paper that named the problem.

---
*Created: 2026-05-13*
