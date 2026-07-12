# Current State

Updated: 2026-07-12

## Product wedge

SiaMentor is focused on one paid wedge:

`book -> action -> repeat -> proof -> paid -> retained`

The user chooses a self-development book, gets a 7-day action plan, completes concrete micro-actions, sees proof after 3 completed actions, then gets a paid 30-day habit plan offer.

Primary positioning: "7 дней внедряю книгу в действия."

## Current product loop

1. User lands on `/ru/habits` or another habit entrypoint.
2. User selects a starter book and goal.
3. Product gives a Day 1 action in if-then format.
4. User completes Day 1 and receives a verified memory receipt.
5. Product drives Day 2 and Day 3 through receipt-based continuity.
6. Proof paywall shows completed actions, best trigger, friction adjustment, price, and free continuation.
7. Next critical step is making paid events revenue-facing, not demo-click-facing.

## Current strategy

H2 objective: reach contribution profitability by 2026-12-31.

July operating focus is not more companion breadth. It is truth about the paid funnel:

- dashboard first;
- payment second;
- manual sales third;
- AI cost guardrail fourth.

## Current implementation posture

Recent completed work:

- mobile landing and book-card density for the book-to-habit offer;
- Day 1 -> Day 2 continuation from receipt;
- human proof copy instead of debug evidence strings;
- mobile proof paywall with price and paid/free CTAs above the fold;
- design note for offline verified-memory action fallback.

Current next product item:

`paid_offer_event_contract` - replace demo click semantics with a revenue-facing event contract.

## Source links

- [[../strategy/annual-product-strategy]]
- [[../strategy/h2-profitability-plan]]
- [[../strategy/habit-agent-memory-and-evals]]
- [[../project-checklist]]
- [[../design/2026-07-12]]
- [[../daily/2026-07-12]]

