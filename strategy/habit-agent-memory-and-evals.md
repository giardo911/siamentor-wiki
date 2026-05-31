# Habit Agent Memory and Evals

Обновлено: 2026-05-31

## Назначение

Этот документ уточняет, как SiaMentor должен строить agentic personalization для D2C book-to-habit wedge. Главный принцип: **память нужна не для "умного чата", а для повышения completion и retention в 7-дневном habit loop**.

## Evidence

- В roadmap 4teacher уже есть Phase 8 Habit Tracker: preset books, 7-day habit plan, daily check-ins, streak, grace day, paywall после 3 completed tasks.
- Исследования по education agents и memory agents показывают, что long-horizon агентам нужны state transitions, typed memory и evals, иначе memory summaries деградируют и создают semantic noise.
- Consumer subscription data показывает, что early churn трудно вернуть; значит paywall должен идти после value proof, а не до первого результата.

## Product inference

SiaMentor должен хранить не общий разговор, а **implementation memory**:

- какую книгу пользователь выбрал;
- какую цель сформулировал;
- какой if-then trigger выбрал;
- какие micro-actions выполнил;
- где сорвался;
- какой friction tag повторяется;
- какой следующий micro-action вероятнее всего будет выполнен.

Это ближе к state machine + typed notes, чем к классическому RAG по чату.

## Minimal typed memory schema

MVP memory facts после check-in:

```text
user_id
habit_plan_id
book_key
goal_text
current_day
selected_trigger
completed_action_text
completion_status: completed | skipped | partial
friction_tag: time | unclear | too_hard | forgot | low_motivation | other
reflection_summary
next_action_hint
confidence: high | medium | low
created_at
```

Правило записи:
- писать только факты, которые влияют на следующий Day action, reminder или paywall copy;
- не писать психологические предположения без evidence из check-in;
- low-confidence memory не использовать как сильную персонализацию.

## Minimal eval suite

Golden set для Phase 8:

- 3 книги: Atomic Habits, 7 Habits, 4-Hour Workweek;
- 3 дня: Day 1-3;
- минимум 2 цели на книгу;
- expected rubric:
  - action связан с книгой;
  - action занимает <=10 минут;
  - есть if-then trigger;
  - действие одно, конкретное и проверяемое;
  - нет generic self-help без связи с выбранной книгой;
  - есть понятный check-in question;
  - action не требует покупки, сложного инструмента или долгой подготовки.

Рекомендуемые eval events:

```text
habit_action_generated
habit_action_eval_passed
habit_action_eval_failed
habit_memory_written
habit_memory_low_confidence
book_habit_day1_completed
daily_habit_checkins_completed
grace_day_used
habit_paywall_viewed
habit_paywall_clicked
```

## Anti-scope

Не делать до доказанного MVP:

- multi-agent peers/social learning как core loop;
- upload "любой книги";
- long-term vector memory без typed write policy;
- enterprise/workspace controls;
- сложные RL memory policies;
- большой retention dashboard до первых когорт Day 1-7.

## Why this matters

Unicorn-потенциал SiaMentor не в том, что он "умеет читать книги". Это commodity. Потенциал в data moat: продукт знает, какие идеи из книг реально превращаются в действия, какие триггеры работают у каких людей, где люди срываются и как вернуть их к следующему маленькому действию.
