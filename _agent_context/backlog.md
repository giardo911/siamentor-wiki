# Backlog

Updated: 2026-07-12

## Active priority

1. `paid_offer_event_contract`
   - Replace demo click `trial_started_from_proof`.
   - Add typed event contract for `paid_30_day_plan_started`.
   - Capture `price_point`, `acquisition_source`, `sales_outcome`, and free continuation after paywall.
   - Add UI capture and e2e assertion.

2. `weekly_profitability_dashboard_v0`
   - Build the CEO funnel view from onboarding to paid and retained.
   - Include source, book, price, weekly decision field, and AI cost.

3. `paid_30_day_plan_price_test`
   - Test 499 / 999 / 1490 RUB.
   - Treat paid start as payment or confirmed paid commitment.

4. `20_manual_sales_interviews`
   - One channel.
   - Offer: "7 дней внедряю книгу в действия."
   - Outcomes: `paid`, `strong_intent`, `first_action_start`, rejection reason.

5. `llm_cost_per_completed_action_guardrail`
   - Count LLM cost per completed action, activated user, and paid user.

## Useful but secondary

- Offline verified-memory action fallback.
- Grace day and streak polish.
- Better recovery after free continuation.

These are useful only when they support the paid loop, retention, or cost truth.

## Non-goals for the current sprint

- Generic AI companion expansion.
- Upload any book as a broad platform promise.
- New memory abstractions that do not improve action completion, proof, payment, or cost.
- More visual polish before event truth.

## Source links

- [[../project-checklist]]
- [[metrics]]
- [[current-state]]

