# Done: Определить activation event — первая meaningful learning session

**Date:** 2026-04-29
**Source:** management/project-checklist.md (section: 2026-04-29)
**GSD Phase:** 999.2

## Summary

Определена первая meaningful learning session как полный цикл: диагностический вопрос → объяснение (≥100 токенов, ≥20 сек чтения) → правильный ответ на проверку → обновление learning memory — всё в одной непрерывной сессии ≥4 минут, привязанной к теме из учебного плана. Техническое событие `meaningful_learning_session_completed` с 6 критериями. Метрика: Activation Rate = активированные за D0-D1 / зарегистрированные. Цель: 30% на старте. Описаны 8 anti-patterns, SQL-запрос для дашборда, 4 шага валидации.

## Deliverable

# Activation Event: Первая Meaningful Learning Session

## 1. Определение первой meaningful learning session

**Meaningful learning session** — это сессия, в которой студент:

1. Осознал конкретный учебный пробел (через диагностику или ответы на вопросы)
2. Получил персонализированное объяснение именно под этот пробел
3. Подтвердил понимание через проверку (ответил правильно хотя бы на 1 вопрос после объяснения)
4. Получил явный сигнал о прогрессе («ты разобрался с X»)

**Формулировка:**

> Студент завершил хотя бы один полный цикл: диагностический вопрос → объяснение → проверочный вопрос с правильным ответом — в рамках одной непрерывной сессии, привязанной к конкретной теме учебного плана.

---

## 2. Логика засчёта (6 критериев, все AND)

| Условие | Pass | Fail |
|---|---|---|
| topic_id из плана | есть | null или вне плана |
| diagnostic_answers | ≥ 1 | 0 |
| explanation_read | ≥ 20 сек, ≥ 100 токенов | меньше |
| post_check_correct | ≥ 1 | 0 |
| duration | ≥ 240 сек | < 240 |
| learning_memory_updated | true | false |

---

## 3. Anti-patterns (что НЕ считается)

1. Регистрация + онбординг без учёбы
2. Диагностический вопрос без объяснения
3. Чтение объяснения без проверки
4. Все ответы на проверке неправильные
5. Сессия по теме вне учебного плана
6. Сессия < 4 минут
7. Learning memory не обновилась (баг/оффлайн)
8. Повторение уже mastered топика

---

## 4. Техническое событие

**Название:** `meaningful_learning_session_completed`

**JSON-схема (ключевые поля):**
```json
{
  "event": "meaningful_learning_session_completed",
  "timestamp": "ISO8601",
  "properties": {
    "user_id": "uuid",
    "session_id": "uuid",
    "is_first_meaningful_session": true,
    "topic_id": "uuid",
    "topic_name": "string",
    "subject": "string",
    "exam_type": "ege_math | ege_russian | ...",
    "session_duration_sec": 312,
    "diagnostic_questions_count": 2,
    "post_check_correct_count": 2,
    "post_check_accuracy": 0.67,
    "topic_status_before": "pending | in_progress",
    "topic_status_after": "in_progress | mastered",
    "activation_criteria_met": {
      "topic_in_plan": true,
      "diagnostic_answered": true,
      "explanation_read": true,
      "post_check_passed": true,
      "min_duration_met": true,
      "memory_updated": true
    },
    "days_since_registration": 0
  }
}
```

**Триггер в Go:** отправляется после `tx.Commit()` в `SessionService.CompleteSession()` — снаружи транзакции, чтобы баг аналитики не откатил учебные данные.

---

## 5. Метрика Activation Rate

**Формула:**
```
Activation Rate = Пользователи с ≥1 meaningful session за D0-D1
                  ──────────────────────────────────────────────
                  Все зарегистрировавшиеся в тот же период
```

**Окно:** 48 часов (D0+D1)

| Период | Цель |
|---|---|
| Старт (сейчас) | **30%** за D0-D1 |
| После оптимизации онбординга | **45%** |
| Зрелый продукт | **50%** |

Референс: Duolingo activation (first lesson) ~40–50% D1.

---

## 6. Связь с D1/D7 Retention

| Тип первой сессии | Ожидаемый D1 | Ожидаемый D7 |
|---|---|---|
| Только регистрация | 5–10% | 2–4% |
| Первое сообщение боту | 15–20% | 5–8% |
| **Meaningful session (наше)** | **35–45%** | **20–30%** |

Механизм связи: прогресс-сигнал снижает тревогу → незавершённые топики (эффект Зейгарник) → персонализированный следующий шаг → психологический якорь.

---

## 7. Валидация

1. **Корреляционный анализ** — criteria_met vs D1/D7 retention (порог: 2.5x разница)
2. **A/B тест порогов** — строже/мягче критерии, победитель по корреляции с D7 retention
3. **Survival analysis** — Kaplan-Meier кривые activated vs non-activated
4. **Качественные интервью** — 5–7 edge cases (false activation + missed activation)

**Критерий:** activated users D1 ≥ 2.5x выше non-activated, D7 ≥ 3x выше.

---

## Links

- GSD Phase: `.planning/phases/999.2-activation-event-meaningful-learning-session/`
