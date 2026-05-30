---
type: concept
phase: 1
created: '2026-05-13'
---
# Token

> A token is the smallest unit of text a language model actually sees — usually a sub-word fragment, not a full word.

## Why it matters

Every cost, every limit, every weird behavior in LLM products is measured in tokens. "Context window of 200k" means 200k tokens, not words. Billing is per token. When a model produces gibberish, it's because it picked weird tokens. You can't reason about cost, latency, or capability without this unit.

## Mental model

The model has a vocabulary of ~50,000–100,000 tokens it knows. Common words ("the", "and") are one token. Rare words get split — "Magleblik" might be three or four tokens. Whitespace and punctuation also count.

Rule of thumb for English: **1 token ≈ 0.75 words**, or **~4 characters**. A page of text is roughly 500 tokens.

Non-English text is usually less efficient — Danish, Japanese, code, and anything with unusual characters costs more tokens per word.

## Common gotchas

- "Limit is 8000 tokens" does NOT mean 8000 words — closer to 6000.
- Long file paths, UUIDs, base64 blobs are token-monsters. They look small but tokenize terribly.
- The model literally cannot see characters inside a token. That's why models historically struggled with "how many r's are in strawberry" — the word is one token, the r's are invisible inside it.
- Output tokens are usually billed more than input tokens.

## Related

- [[Context Window]] — measured in tokens
- [[Temperature]] — controls which token gets picked

## Sources

- See [[Reading Log]] queue: Simon Willison has good intuition-builders on this.
- OpenAI's tokenizer playground (platform.openai.com/tokenizer) — paste your text in, see the tokens.

---
*Created: 2026-05-13*
