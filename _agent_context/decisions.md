# Decisions

Updated: 2026-07-12

## Product identity

SiaMentor is not a generic AI chat, course platform, or summary app. The current wedge is D2C book-to-habit: turn a known self-development book into daily verified actions.

## Activation

Activation means completed action, not generated plan. `book_habit_day1_completed` is the hard activation event.

## Proof before pay

The paid offer should come after evidence: completed actions, trigger pattern, friction adjustment, and a concrete next plan. Proof copy must be human-readable and must not show debug strings such as raw `verified:` fields.

## Memory policy

Use typed implementation memory:

- book;
- goal;
- trigger;
- completed action;
- friction;
- reflection summary;
- next action hint;
- confidence.

Memory is used to improve the next action, reminder, proof, and paywall copy. Do not store broad psychological guesses without evidence.

## Monetization policy

The business is optimizing for contribution profitability, not novelty revenue. Paid metrics must distinguish real payment or confirmed commitment from a click.

## Scope policy

When choosing between another product feature and better truth about the funnel, choose funnel truth unless the feature directly unblocks activation, retention, payment, or AI cost control.

## Source links

- [[../strategy/annual-product-strategy]]
- [[../strategy/h2-profitability-plan]]
- [[../strategy/habit-agent-memory-and-evals]]

