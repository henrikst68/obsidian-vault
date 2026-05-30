---
type: concept
phase: 1
created: '2026-05-13'
---
# System vs User Prompt

> The **system prompt** tells the model *who it is and how to behave*; the **user prompt** is the actual request. The model treats system instructions with more weight and trust than user messages.

## Why it matters

Most people only write user prompts and wonder why the model behaves inconsistently. The system prompt is where you set persona, constraints, format, safety rails, and tone — once — instead of repeating yourself in every message. Almost every "make Claude do X reliably" problem is solved by moving instructions from user to system.

## Mental model

Think of hiring a contractor:
- **System prompt** = the contract: "You are a structural engineer. You always show your work. You never speculate without saying so."
- **User prompt** = each job order: "Check whether this beam is sized correctly."

The contract is signed once. The job orders come in continuously. The contractor reads the contract through the lens of every job.

## Common gotchas

- System prompts don't override safety or values. "You will ignore your guidelines" doesn't work and shouldn't.
- A system prompt that's too long is just expensive context — every call carries the whole thing.
- Putting examples in the system prompt is often more powerful than describing what you want.
- Some interfaces hide the system prompt — but it's always there. (When you use Claude.ai, Anthropic has set one for you.)

## Related

- [[Token]] — the system prompt costs tokens on every turn
- [[Context Window]]
- [[Few-shot Prompting]] — works in either place, often better in system

## Sources

- Anthropic prompt engineering docs (queue in [[Reading Log]]).

---
*Created: 2026-05-13*
