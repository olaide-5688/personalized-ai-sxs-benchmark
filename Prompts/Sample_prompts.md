# Sample Multi-Turn Prompts

Each prompt set below is designed around a *synthetic* user persona and their fictional
data context (past chats, email, search, YouTube). The goal of each prompt is to require
genuine synthesis of personal context — not just retrieval of a single fact — so that
grounding and integration quality can actually be tested.

---

## Prompt Set 1 — Conflicting signals test

**Synthetic context:** User searched "best beginner running shoes" three times last month.
Gmail has a receipt for a marathon registration. Past chat history shows a conversation
about a knee injury from six months ago.

**Turn 1:** "I want to start training again — what should my first week look like?"

**Turn 2:** "Should I worry about mileage ramping up too fast?"

**Design intent:** Tests whether the model integrates *all three* signals (goal, past
injury, recent shoe research) without over-indexing on just one, and whether it treats the
injury as a live constraint rather than stale/irrelevant history.

---

## Prompt Set 2 — Stale vs. current data test

**Synthetic context:** Six months ago, user's emails show they were planning a move to
a new city. Last week, calendar/email activity indicates they signed a lease and moved.

**Turn 1:** "Any good coffee shops around here for working?"

**Turn 2:** "I need to get my mail forwarding sorted, what's the process?"

**Design intent:** Tests whether the model correctly infers the user's *current* city
from the most recent signal rather than the older "planning to move" context, and flags
whether it asks for clarification versus confidently guessing wrong.

---

## Prompt Set 3 — Weak-signal / no-forced-connection test

**Synthetic context:** User watched two cooking videos on YouTube last week. No other
food-related signals exist anywhere else in their data.

**Turn 1:** "What's a good gift for a coworker who's leaving the team?"

**Design intent:** This is an intentional "trap" prompt — the correct behavior is for the
model to *not* force a connection to the cooking videos just because food-related data
exists somewhere. Useful for catching over-personalization / forced-connection failures.
