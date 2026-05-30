---
type: concept
phase: 1
created: '2026-05-13'
---
# Temperature

> A number (usually 0 to 1) that controls how *random* the model's next-[[Token|token]] choice is. Low = predictable and conservative. High = creative and surprising.

## Why it matters

The same prompt at temperature 0 and temperature 1 can produce wildly different outputs. Most "the model is inconsistent" frustration is actually a temperature problem. Most "the model is boring" frustration is also a temperature problem — in the other direction.

You don't always get to set it (some products hide it), but knowing what it does explains a lot of weird behavior.

## Mental model

At every step, the model has a probability distribution over what token comes next. Temperature reshapes that distribution:

- **Temperature 0** — always pick the single most probable token. Deterministic-ish. Good for extraction, classification, code, math.
- **Temperature ~0.7** — typical default. Some variety, mostly coherent. Good for general chat and writing.
- **Temperature 1+** — flatten the distribution; unlikely tokens become viable. Good for brainstorming, fiction, unblocking yourself. Risk: incoherence.

Think of it as the model's **willingness to take a risk** on each word it picks.

## Common gotchas

- Temperature 0 is *not* fully deterministic across runs — ties get broken, hardware noise creeps in. Don't bet a system's correctness on identical output.
- High temperature ≠ smarter. It's noisier, not deeper.
- "More creative" prompts at temperature 0 will still feel flat. Tools matter.
- **top_p** is a sibling control (nucleus sampling) — affects similar territory. Usually leave one fixed and only tune the other.

## Related

- [[Token]]
- Sampling, top-p (related concept, not yet noted)

## Sources

- Try it yourself in Anthropic's Workbench or OpenAI's Playground. Set temperature 0 and 1 on the same prompt — you'll feel it immediately.

---
*Created: 2026-05-13*
