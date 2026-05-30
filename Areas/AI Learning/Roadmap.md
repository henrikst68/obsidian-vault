---
type: roadmap
area: AI Learning
created: '2026-05-13'
---
# AI Roadmap — Hands-on Tinkerer

Six phases. Tick checkboxes as you go. Don't be precious about order — it's a guide, not a contract. The point is to keep building things while the understanding deepens.

---

## Phase 1 — How LLMs actually work

The mental model. No math needed, but you need this scaffolding or everything else is just incantations.

- [ ] [[Concepts/Token]] — what models actually see
- [ ] [[Concepts/Context Window]] — and why it matters for cost and quality
- [ ] [[Concepts/System vs User Prompt]] — the two main inputs
- [ ] [[Concepts/Temperature]] — and top-p, sampling
- [ ] Understand why models hallucinate (it's not lying — it's the architecture)
- [ ] Skim "A Visual Introduction to Transformers" (3Blue1Brown) — just for the picture in your head
- [ ] Be able to explain "tokens in, tokens out" to a non-technical friend

**Milestone:** You can predict whether a given prompt will work well or fail, and explain *why*.

---

## Phase 2 — Prompting as a craft

This is where 80% of the practical leverage lives.

- [ ] Read Anthropic's prompt engineering overview end-to-end (docs.claude.com)
- [ ] [[Concepts/Few-shot Prompting]]
- [ ] [[Concepts/Chain of Thought]]
- [ ] [[Concepts/XML Tags in Prompts]] — Claude-specific but conceptually general
- [ ] Build a small library of your own go-to prompt patterns
- [ ] Practice: take a vague task and write three increasingly-good prompts for it

**Milestone:** You can take any messy task and turn it into a prompt that works on the first or second try. Start an [[Experiments/Prompt Patterns]] note.

---

## Phase 3 — Tool use, MCP, and agents

You're already using MCPs (Hetzner vault, pi-assistant). Now understand them.

- [ ] Read the MCP spec overview (modelcontextprotocol.io)
- [ ] [[Concepts/Tool Use]] — how models actually call tools
- [ ] [[Concepts/MCP]] — what a server is, what a client is, what the wire format looks like
- [ ] [[Concepts/Agent Loop]] — model → tool → result → model, why it works
- [ ] Look at the source of one of your installed MCPs (pi-assistant is yours — perfect)
- [ ] Build your own tiny MCP server — even one tool, even pointless. The smallest possible.
- [ ] [[Concepts/Eval]] — how do you know an agent is working? (this is the hard part)

**Milestone:** Ship a custom MCP server that does one useful thing for your house or workflow.

---

## Phase 4 — RAG and giving models knowledge

When to stuff the context, when to retrieve, when to fine-tune (almost never).

- [ ] [[Concepts/Embeddings]] — vectors, similarity, intuition
- [ ] [[Concepts/Vector Database]]
- [ ] [[Concepts/RAG]] — retrieval-augmented generation, end to end
- [ ] [[Concepts/Chunking]] — the unsexy part that decides whether RAG works
- [ ] Understand when RAG is wrong (small corpus → just dump it in context)
- [ ] Experiment: build a tiny RAG over your own Obsidian vault

**Milestone:** A working Q&A over your own notes — even if it's rough. Document what's good and what's bad in [[Experiments/Vault RAG]].

---

## Phase 5 — Building real things

By now you've got the vocabulary. Time to compound.

- [ ] An MCP server that controls one Home Assistant routine via natural language
- [ ] A weekly briefing automation (you already have Briefings — automate generation)
- [ ] A "writing critic" agent that reads your draft notes and pushes back
- [ ] One thing that genuinely surprises you when it works
- [ ] Write up each as an [[Experiments]] note — what you tried, what failed, what you'd do differently

**Milestone:** Three shipped things that solve real problems in your life. Not demos — things you use.

---

## Phase 6 — Staying current

The field moves fast. You need a habit, not a sprint.

- [ ] Pick 3-5 voices to follow (suggestions in [[Reading Log]])
- [ ] Reading Log discipline: log it, even a one-liner
- [ ] One paper or long-form piece per month, with a written summary
- [ ] Notice when a new technique would solve a problem you already have

**Milestone:** Six months from now, your Reading Log shows continuous activity and your Concepts folder has ~30+ atomic notes. Self-sustaining.

---

## Tracking

| Phase | Status | Started | Finished |
|---|---|---|---|
| 1 — Foundations | Not started | | |
| 2 — Prompting | Not started | | |
| 3 — Tools & MCP | Not started | | |
| 4 — RAG | Not started | | |
| 5 — Building | Not started | | |
| 6 — Staying current | Ongoing | | (never) |
