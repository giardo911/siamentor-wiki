# Done: Добавить guardrails для LLM/агентов: лимит стоимости/итераций + валидация структурированных ответов

**Date:** 2026-05-03
**Source:** management/project-checklist.md (section: 2026-04-28)
**GSD Phase:** 999.4

## Summary

Создан Decision Record v1.0 по guardrails для LLM/агентов SiaMentor. Документ охватывает 9 разделов: типологию AI-вызовов (6 типов: plan_generation, diagnosis, explanation, answer_check, memory_update, session_summary), лимиты токенов per request, cost guardrails ($0.15 hard limit/сессия, $1.00/пользователь/день), iteration guardrails (макс. 12 вызовов/сессия, 2 ретрая, таймаут 30s/вызов), smart model routing (Haiku для answer_check/memory_update, Sonnet для diagnosis/plan_generation), JSON schema validation с 3-attempt retry и fallback для memory_update/answer_check/plan_generation, политику graceful degradation, мониторинг (PostHog + Telegram alerts) и приоритет реализации P0 (~6 часов для критичных guardrails). Целевой AI-cost: ≤ $0.05/meaningful session при WTP 299–499 ₽/мес.

## Deliverable

Полный документ: `.planning/phases/999.4-llm-agent-guardrails-cost-validation/999.4-GUARDRAILS.md`

### Ключевые решения из документа

**P0 (критично, ~6 ч реализации):**
1. Max tokens per request (plan: 6k, diagnosis: 4k, explanation: 3.5k, answer_check: 2k, memory_update: 2.3k)
2. JSON schema validation + 3-attempt retry + fallback (memory_update/answer_check/plan_generation)
3. Hard cost limit $0.15/сессия → принудительный session_summary

**Smart routing:**
- Haiku: answer_check, memory_update, explanation/basic, session_summary ≤10 turns
- Sonnet: diagnosis, plan_generation, explanation/intermediate+advanced, session_summary >10 turns

**Целевые параметры:**
- AI cost/meaningful session: ≤ $0.02–0.05
- AI cost/пользователь/мес: ≤ $1.50 (≤30% от WTP $3–5)
- JSON validation failure alert threshold: >5%/день

## Links

- GSD Phase: `.planning/phases/999.4-llm-agent-guardrails-cost-validation/`
- Decision document: `.planning/phases/999.4-llm-agent-guardrails-cost-validation/999.4-GUARDRAILS.md`
