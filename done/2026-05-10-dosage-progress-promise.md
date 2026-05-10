# Done: Сформулировать «dosage + progress promise» (D2C аналог outcomes-based): сколько сессий/нед и какой измеримый прогресс обещаем/компенсируем

**Date:** 2026-05-10
**Source:** management/project-checklist.md (section: 2026-04-29)
**GSD Phase:** 999.8

## Summary

Создан продуктово-стратегический документ DELIVERABLE.md (340 строк, 8 секций) для book-to-habit продукта SiaMentor. Зафиксированы 7 locked decisions: дозаж — 1 micro-action ≤10 мин ежедневно с grace day (D1–D2); честные горизонты обещания — 7 дней = 3–7 действий, 30 дней = 20–30 действий (D3); primary метрики — streak_count + actions_completed_count (D4); paywall после 3 completed actions, не по времени (D5); конкретные формулировки для каждого экрана (D6); if-then формат обязателен для Days 1–3 (D7). Написаны 5 value promise формулировок с A/B-стратегией: Вариант 2 (pain-led лендинг), Вариант 4 (персонализированный paywall), Вариант 3 (identity reinforcement Day 1). Задокументированы 7 PostHog events и 3 feature flags для Phase 8 (HAB-05). Документ служит источником истины для разработчиков, маркетологов и UX-дизайнеров.

## Deliverable

### Locked Decisions D1–D7

| ID | Решение |
|----|---------|
| D1 | 1 micro-action/день, ≤10 мин (≤5 мин Day 1–3), if-then формат |
| D2 | Grace day: 1 auto-skip per 7-дневный цикл; второй пропуск → мягкий сброс |
| D3 | 7 дней: «3–7 выполненных действий»; 30 дней: «20–30 действий + ритуал» |
| D4 | Primary: streak_count + actions_completed_count; secondary: days_active, plan_progress_pct |
| D5 | paywall_trigger = после 3 completed actions (не через 3 дня) |
| D6 | Лендинг: Вариант 2 (pain-led); Paywall: Вариант 4 (персонализированный); Day 1: Вариант 3 (identity) |
| D7 | If-then формат обязателен для Days 1–3; пользователь выбирает триггер при онбординге |

### Value Promise формулировки (5 вариантов)

| Вариант | Экран | Headline | A/B статус |
|---------|-------|----------|-----------|
| 1 | Paywall | «Внедри [книга] за 30 дней — по одному действию в день» | Контроль paywall A/B |
| 2 | Лендинг / онбординг | «Прочитал — но не внедрил? Исправим за 7 дней.» | Контроль лендинг A/B |
| 3 | Day 1 completion | «Сегодня ты сделал первый шаг внедрения [книга]. День 1 из 7.» | Дефолт (не тестировать) |
| 4 | Paywall персонализированный | «Ты уже внедрил 3 идеи из [книга]. Продолжи 30-дневный план — 299 ₽.» | Challenger paywall A/B |
| 5 | Лендинг минималистичный | «7 дней. 1 действие в день. Наконец-то внедришь [книгу].» | Challenger лендинг A/B |

### PostHog Events для Phase 8

7 событий: `book_selected`, `habit_plan_created`, `book_habit_day1_completed`, `habit_checkin_completed`, `streak_extended`, `paywall_shown`, `paywall_cta_clicked`.
3 feature flags: `book-to-habit-paywall-variant`, `book-to-habit-landing-variant`, `book-to-habit-if-then-enabled`.

## Links

- GSD Phase: `.planning/phases/999.8-dosage-progress-promise-book-to-habit/`
- DELIVERABLE: `.planning/phases/999.8-dosage-progress-promise-book-to-habit/999.8-DELIVERABLE.md`
