# Evaluation Rubric: Grounding, Integration, Helpfulness

## 1. Grounding
*Is every personalized claim about the user actually supported by their data?*

| Score | Description |
|---|---|
| Strong | All personalized claims trace directly to verifiable data; no unsupported inference. |
| Moderate | Claims are plausible but rely on a stretch — a reasonable but unconfirmed inference. |
| Weak | The model states something about the user that isn't supported, or generalizes a single data point into a stable trait. |
| Failing | Hallucinated personal detail, or a claim that contradicts the user's actual data. |

**Common failure modes to flag:**
- Treating one-off events as ongoing patterns ("you always...")
- Using stale data when more recent, contradicting data exists
- Inventing specifics (names, dates, preferences) not present in any source

## 2. Integration
*Is the personal context woven in naturally, or does it feel bolted on?*

| Score | Description |
|---|---|
| Strong | Personalization shapes the substance of the response; the user wouldn't notice a "seam." |
| Moderate | Personalization is accurate and used, but the phrasing calls attention to itself. |
| Weak | "Overnarrating" — the model explains what it noticed about the user rather than just using it (e.g., "Since I know you searched for running shoes recently and also registered for a marathon, and I recall you mentioned a knee injury, I think...") |
| Failing | Personalization is present but disconnected from the actual answer — decorative, not functional. |

**Test:** Would the response be meaningfully worse (not just less personal) if the
personalized detail were removed? If not, integration hasn't actually changed the
substance — it's decoration.

## 3. Helpfulness
*Did the personalization make the response more useful, not just more personal?*

| Score | Description |
|---|---|
| Strong | The personalized version clearly outperforms a generic answer for this user's actual situation. |
| Moderate | Personalization is fine but roughly neutral in value-add. |
| Weak | Personalization narrows or distracts from what the user actually needed. |
| Failing | Personalization actively misleads the user or produces a worse outcome than a generic response would have. |

## Side-by-side (SxS) ranking process

1. Identify user intent from the opening turn(s), independent of either response.
2. Score both responses independently on all three dimensions above.
3. Only after independent scoring, compare directly and rank.
4. Write the rationale referencing **specific turn numbers** and quoting the exact
   phrase or claim being evaluated — never a general impression.
5. Note any "forced connection" — personalization applied where no real signal existed.
