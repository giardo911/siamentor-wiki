# Metrics

Updated: 2026-07-12

## CEO funnel chain

The weekly CEO view should join this chain by source, book, price point, and AI cost bucket:

```text
acquisition_source_seen
onboarding_started
plan_ready_action_required
book_habit_day1_completed
d1_return_from_action_receipt
third_action_completed
habit_paywall_proof_rendered
paid_30_day_plan_started
d7_paid_retained
d30_paid_retained
```

## Revenue-facing contract

`paid_30_day_plan_started` must mean a real payment or a confirmed paid commitment. It must not mean a generic button click, UI state transition, or demo trial click.

Required properties for the next contract:

```text
price_point
acquisition_source
book_key
sales_outcome
habit_plan_id
completed_actions_count
free_action_completed_after_paywall
```

## Current risk

The monetization loop is weaker than the product loop. If `trial_started_from_proof` remains the main paid signal, dashboards can report fake monetization while the business has no payment proof.

## Cost guardrails

Track:

- `llm_calls_per_completed_action`
- `llm_cost_per_completed_action`
- AI cost per activated user
- AI cost per paid user

Day 2-7 should be template-first when verified memory is available. LLM calls are for shrink, clarify, rewrite, or recovery fallback, not for blocking every daily action.

## Source links

- [[../strategy/h2-profitability-plan]]
- [[../strategy/habit-agent-memory-and-evals]]
- [[current-state]]

