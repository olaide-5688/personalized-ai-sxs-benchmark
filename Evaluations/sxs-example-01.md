# SxS Evaluation Example 01

**Prompt set used:** Prompt Set 1 — Conflicting signals test (see `/prompts/sample-prompts.md`)

**Synthetic context:** Recent searches for "beginner running shoes" (x3), a marathon
registration email, and a chat from 6 months ago mentioning a knee injury.

**Turn 1 (user):** "I want to start training again — what should my first week look like?"

> **Note:** Responses A and B below are authored by me to illustrate the evaluation
> method — they are not real Gemini outputs.

---

### Response A
> "Great goal! Here's a solid first week: 3 easy runs of 20-30 minutes, alternating with
> rest days, plus one longer walk. Since you mentioned looking into running shoes recently,
> make sure you're in a supportive pair before you start. Also, I noticed from a past
> conversation that you had a knee injury — you might want to keep that in mind and go
> easy at first."

### Response B
> "Here's a first week built around easing back in safely, given the knee injury from
> a few months ago: three short runs (20 min) at an easy, conversational pace, with a
> rest or cross-training day between each. Skip hills and hard surfaces for now if you
> can. Since you've registered for a marathon, we can build toward higher mileage after
> a few injury-free weeks — want me to sketch that longer ramp-up too?"

---

### Independent scoring

**Response A**
- Grounding: Moderate — references are accurate but knee injury is mentioned almost as
  an afterthought ("you might want to keep that in mind"), undervaluing how directly
  relevant it is to a *training plan specifically*.
- Integration: Weak — visibly overnarrates ("I noticed from a past conversation that...").
  The personalization is announced rather than used.
- Helpfulness: Moderate — plan is generic and doesn't actually adjust for the injury
  (no surface/incline guidance, no cross-training substitution).

**Response B**
- Grounding: Strong — all three signals (injury, shoe research implied via safe-start
  framing, marathon goal) are used, and the injury is treated as the primary constraint
  shaping the plan, not a footnote.
- Integration: Strong — no "I noticed..." framing; the injury and marathon goal directly
  determine the structure of the plan itself.
- Helpfulness: Strong — concrete, injury-aware guidance (surface, incline, cross-training)
  and a natural next-step offer tied to the actual goal (marathon ramp-up).

### Ranking: **B > A**

### Rationale

Response B is meaningfully better on all three dimensions, most clearly on Integration and
Helpfulness. In Turn 1, Response A surfaces the user's data explicitly ("I noticed from a
past conversation that you had a knee injury") — a textbook overnarrating pattern per the
rubric: the model is explaining its own retrieval instead of just acting on it. Response B
never announces its sources; it simply builds a plan where the injury constraint and the
marathon goal are load-bearing (e.g., "given the knee injury," "skip hills... for now").

On Helpfulness, Response A's plan doesn't actually change based on the injury — it's the
same generic beginner plan with a caveat appended. Response B's plan changes in substance
(surface/incline guidance, cross-training days) because of the injury, which is the real
test of whether personalization added value versus just being mentioned.

Neither response shows a forced connection or an ungrounded claim; the gap here is
Integration and downstream Helpfulness, not Grounding.
