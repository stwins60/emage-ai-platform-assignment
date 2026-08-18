# Week 2 Cost Table — Corrected (Lab A4)

Source repo: [`emage-tech/ai-platform-engineering-run-track`](https://github.com/emage-tech/ai-platform-engineering-run-track), `week-02-developing-code-with-ai/README.md`, Part 3 — "The model landscape."

The README's own table is dated "as of August 2026" and flags itself with:

> Verify all of these before you quote them — this table ages like milk, on purpose. The exercise of re-verifying it is Lab A4.

This document is that re-verification, done **2026-08-18**.

## Original table (as it appears in the repo today)

| Model | Input | Output | Context | The niche |
|---|---:|---:|---:|---|
| Claude Fable 5 | $10 | $50 | 1M | Frontier reasoning, long autonomous work |
| Claude Opus 5 | $5 | $25 | 1M | The default for serious agentic coding |
| Claude Sonnet 5 | $2 | $10* | 1M | Speed/intelligence balance, the workhorse |
| Claude Haiku 4.5 | $1 | $5 | 200k | Fast, cheap, near-frontier — subagents, classification |
| GPT-5.5 | $5 | $30 | 1M | OpenAI flagship |
| Gemini 3.1 Pro | $2 | $12 | 2M | Largest context window on the market |
| DeepSeek V4, Llama 4, Qwen 3 | — | — | varies | Open weights: no per-token bill, your GPUs instead |

## What's actually correct vs. wrong, per row

| Model | Verdict | Detail |
|---|---|---|
| Claude Fable 5 | ✅ Correct | $10 / $50 per MTok, 1M context — confirmed against Anthropic's current model catalog. |
| Claude Opus 5 | ✅ Correct | $5 / $25 per MTok, 1M context — confirmed. |
| Claude Sonnet 5 | ✅ Correct | $2 / $10 is genuine introductory pricing, active through **2026-08-31** (i.e. still in effect on today's date, 2026-08-18) — reverts to $3 / $15 after. The table's footnote is accurate, not stale. |
| Claude Haiku 4.5 | ✅ Correct | $1 / $5 per MTok, 200K context — confirmed. |
| GPT-5.5 | ⚠️ **Context wrong** | Price ($5 / $30) is correct, confirmed against OpenAI's own pricing docs. But the context window is **not 1M** — it's **<272K tokens**. The table borrowed the 1M figure from the Claude/Gemini rows above it. |
| Gemini 3.1 Pro | ⚠️ **Context wrong** | Price ($2 / $12 for prompts ≤200K tokens) is correct, confirmed against Google's own pricing docs. But the context window is **1M, not 2M** — 2M belongs to a different model, Gemini 3.1 **Ultra**. There's also a long-context pricing tier the table omits: **>200K tokens jumps to $4 / $18**. And with GPT-5.5 correctly at <272K, "largest context window on the market" for Gemini 3.1 Pro no longer holds up cleanly at 1M when Claude's models are also 1M — the honest claim is "tied for largest among these, at 1M." |
| Open-weight row | ⚠️ **One model name stale** | Structurally still correct — no per-token bill, self-hosted. But **Qwen 3 has been superseded by Qwen 3.5** as the current flagship in that family as of mid-2026 (Apache 2.0, strongest open reasoner). DeepSeek V4 and Llama 4 are still accurate as the current flagships in their families. |

## Corrected table

| Model | Input | Output | Context | The niche |
|---|---:|---:|---:|---|
| Claude Fable 5 | $10 | $50 | 1M | Frontier reasoning, long autonomous work |
| Claude Opus 5 | $5 | $25 | 1M | The default for serious agentic coding |
| Claude Sonnet 5 | $2 | $10* | 1M | Speed/intelligence balance, the workhorse |
| Claude Haiku 4.5 | $1 | $5 | 200K | Fast, cheap, near-frontier — subagents, classification |
| GPT-5.5 | $5 | $30 | <272K | OpenAI flagship |
| Gemini 3.1 Pro | $2† | $12† | 1M | Tied for largest context window here; long-context tier costs more |
| DeepSeek V4, Qwen 3.5, Llama 4 | — | — | varies | Open weights: no per-token bill, your GPUs instead |

\* Introductory pricing through 2026-08-31; then $3 / $15.
† For prompts ≤200K tokens. Above 200K: $4 input / $18 output per MTok.

## Sources

- [Anthropic — Pricing](https://platform.claude.com/docs/en/pricing) (Claude Fable 5, Opus 5, Sonnet 5, Haiku 4.5)
- [OpenAI — API Pricing](https://developers.openai.com/api/docs/pricing) (GPT-5.5: $5/$30 per MTok, <272K context)
- [Google AI — Gemini API Pricing](https://ai.google.dev/gemini-api/docs/pricing) (Gemini 3.1 Pro: $2/$12 ≤200K, $4/$18 >200K)
- Model context window cross-check: [MarkTechPost — Gemini 3.1 Pro launch coverage](https://www.marktechpost.com/2026/02/19/google-ai-releases-gemini-3-1-pro-with-1-million-token-context-and-77-1-percent-arc-agi-2-reasoning-for-ai-agents/) (1M context, confirms Ultra is the separate 2M-context model)
- Open-weight landscape: [Digital Applied — Open-Weight Models H1 2026 Retrospective](https://www.digitalapplied.com/blog/open-weight-models-h1-2026-retrospective-deepseek-qwen-llama) (DeepSeek V4, Qwen 3.5, Llama 4 as current flagships)

## Suggested fix for the repo

In `week-02-developing-code-with-ai/README.md`, Part 3:

1. Change GPT-5.5's context column from `1M` to `<272K`.
2. Change Gemini 3.1 Pro's context column from `2M` to `1M`, and either drop the "largest context window on the market" niche claim or qualify it (tied with Claude's 1M models; Gemini 3.1 *Ultra*, not Pro, is the 2M model).
3. Add a footnote on the Gemini row noting the >200K long-context pricing jump to $4/$18, mirroring the existing Sonnet 5 intro-pricing footnote style.
4. Swap `Qwen 3` → `Qwen 3.5` in the open-weights row.
