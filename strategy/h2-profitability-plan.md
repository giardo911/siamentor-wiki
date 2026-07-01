# SiaMentor H2 Profitability Plan

Дата: 2026-07-01

## CEO objective

Выйти на прибыль до 2026-12-31.

Практическое определение прибыли для H2: SiaMentor должен стать contribution-profitable на продуктовой воронке, то есть платёжная выручка месяца покрывает AI/infrastructure/payment costs и прямые acquisition costs этого месяца. Founder salary и крупные R&D вложения пока считаются отдельно, но weekly review должен показывать путь к полной операционной прибыли.

## Strategy

Не строить широкий AI companion. Сфокусироваться на одном paid wedge:

**"7 дней действий из книги с проверяемой памятью, затем paid 30-day habit plan."**

Пользователь платит не за AI, не за summary и не за чат. Он платит после доказанного прогресса: сделал 3 действия из книги, увидел свой trigger pattern и получил предложение продолжить 30 дней.

## Business model assumptions

| Параметр | Base case | CEO guardrail |
| --- | ---: | --- |
| Primary offer | 30-day habit plan | Продавать после 3 completed actions |
| Price test | 499 / 999 / 1490 RUB | Убрать цену, если ломает D7 retention |
| Default target price | 999 RUB | Ниже 499 RUB не оптимизировать без причины |
| AI cost per activated user | <= 50 RUB | Дешёвые модели для routine steps |
| AI cost per paid 30-day user | <= 150 RUB | Gross margin должен оставаться 80%+ |
| Payment conversion after proof paywall | 5% minimum | Ниже 5% — менять offer/channel/copy |
| First action completion | 20% minimum July | Ниже 20% — activation path не готов |

## Profit target ladder

Цель до конца года не "идеальная подписочная машина", а доказанная платная воронка с положительной contribution margin.

| Milestone | Deadline | Required result |
| --- | --- | --- |
| July decision gate | 2026-07-31 | 20%+ новых пользователей дошли до first action, 5%+ proof paywall viewers оплатили |
| First revenue loop | 2026-08-31 | 10+ paid users, подтверждённый AI cost per paid user, weekly funnel dashboard |
| Repeatable wedge | 2026-09-30 | 50+ paid users cumulative, один канал даёт predictable starts weekly |
| Contribution-profit month | 2026-10-31 | Выручка месяца покрывает variable costs и прямой acquisition spend |
| Scale or narrow | 2026-11-30 | 150+ active/recent paid users или осознанное сужение ICP/offer |
| Year-end profitability | 2026-12-31 | Положительная monthly contribution profit и понятный план полной operating profit |

## North-star and funnel

CEO north-star на H2:

`paid_habit_users_with_3_completed_actions`

Это платящие пользователи, которые до оплаты сделали минимум 3 действия из книги. Метрика защищает от fake revenue на novelty и от fake activation на красивом плане.

Обязательная воронка:

1. `acquisition_source_seen`
2. `onboarding_started`
3. `plan_ready_action_required`
4. `book_habit_day1_completed`
5. `d1_return_from_action_receipt`
6. `third_action_completed`
7. `habit_paywall_proof_rendered`
8. `paid_30_day_plan_started`
9. `d7_paid_retained`
10. `d30_paid_retained`

Unit economics dashboard должен показывать эту воронку по source, book, price point и AI cost bucket.

## July execution plan

### Product

1. Сделать hard activation gate production-ready: onboarding success только после `book_habit_day1_completed` или явного `do_later_recovery_hook`.
2. Запустить proof paywall после 3 completed actions: completed actions X/Y/Z, cautious trigger pattern, friction adjustment, 30-day offer.
3. Добавить free continuation guardrail после paywall, чтобы монетизация не ломала habit loop.

### Analytics

1. Собрать event chain от source до paid.
2. Разделить cohorts `plan_created_without_action` и `book_habit_day1_completed`.
3. Считать AI cost per activated user и AI cost per paid user.
4. Каждую неделю фиксировать funnel, revenue, cost, decision.

### GTM

Выбрать один канал на июль: ручные Telegram/личная сеть/interview-led sales.

Причина: до product-channel fit нельзя размазывать внимание на SEO, paid ads, influencers и broad content. Нужны разговоры, быстрый feedback и первые оплаты.

Июльская цель GTM:

- 20 ручных интервью/продаж
- 10+ onboarding starts
- 3+ пользователей с first action
- 1+ paid commitment или понятная причина отказа платить

## Weekly CEO review

Каждую неделю отвечать письменно:

1. Сколько новых пользователей пришло по каждому source?
2. Сколько дошло до `book_habit_day1_completed`?
3. Сколько дошло до 3 completed actions?
4. Сколько увидело proof paywall?
5. Сколько оплатило и по какой цене?
6. Сколько стоил AI на activated user и paid user?
7. Что режем, что усиливаем, какой один bottleneck у следующей недели?

## Kill / scale criteria for 2026-07-31

Scale current wedge, если:

- 20%+ новых пользователей доходят до first action
- 5%+ proof paywall viewers оплачивают
- AI cost per paid user удерживается в guardrail
- минимум один acquisition source даёт starts без ручного объяснения продукта каждому пользователю

Cut or pivot, если:

- пользователи хотят summary/chat, но не делают action
- first action completion ниже 20%
- proof paywall не конвертит даже после 3 actions
- цена воспринимается как плата за "AI toy", а не за внедрение книги

В pivot сначала менять offer/channel/copy, а не строить новые функции.

## CEO stance

Главный запрет H2: не путать прогресс продукта с прогрессом бизнеса.

Полезный дизайн, память, recovery и paywall имеют смысл только если ведут к платной цепочке:

`book -> action -> repeat -> proof -> paid -> retained`

Всё остальное ниже линии.
