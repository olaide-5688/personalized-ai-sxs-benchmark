# Gemini Personalization Evaluation — Portfolio

This repository is a demonstration portfolio for evaluating **AI personalization quality** —
the kind of work involved in assessing how well a model like Gemini uses signals from past
conversations, email, search, and video activity to produce more relevant, helpful responses.

It's built to show three things:

1. **Creative prompt engineering** — designing multi-turn prompts that plausibly require
   personal context to answer well (see `/prompts`).
2. **Rigorous side-by-side (SxS) evaluation** — comparing two candidate responses and
   producing a defensible, turn-referenced rationale (see `/evaluations`).
3. **A clear evaluation framework** — explicit criteria for judging Grounding, Integration,
   and Helpfulness, including common failure modes (see `/rubric`).

## Why this matters for personalization QA

Personalization evaluation isn't just "did the model use my data" — it's whether it used
the *right* data, drew *supportable* inferences from it, wove it in *naturally*, and made
the response *more useful* as a result. A model can fail in several distinct ways even when
it "sounds" personalized:

- **Grounding failure** — the model states something about the user that isn't actually
  supported by their data (a hallucinated or overreaching inference).
- **Integration failure** — the personalization is accurate but bolted on awkwardly
  ("overnarrating": the model tells you what it noticed about you instead of just using it).
- **Helpfulness failure** — the personalization is accurate and smoothly integrated, but
  doesn't actually make the response more useful than a generic one would have been.

This repo's rubric and sample evaluation are structured around separating these three
failure modes explicitly, since conflating them is the most common way evaluation
rationales become vague or indefensible.

## Structure

```

prompts/         Sample multi-turn prompts designed to require personal context
evaluations/     A worked side-by-side (SxS) evaluation with rationale
rubric/          Scoring criteria for Grounding, Integration, and Helpfulness
```

## Note on data

All "personal context" used here is fictional/synthetic, created for demonstration
purposes only — no real personal data, accounts, or conversation history is used or
included in this repository.

## What this is (and isn't)

This is a **self-directed practice project**, not paid work experience or output from
an actual Gemini evaluation engagement. I built it to demonstrate how I'd approach the
core tasks of a personalization-QA role: designing context-dependent prompts, applying
a consistent rubric, and writing defensible SxS rationales. The sample model responses
in `/evaluations` are authored by me, not real Gemini outputs, and are labeled as such.
