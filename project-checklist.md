# Project checklist


## 2026-04-28
- [x] Определить ICP на ближайшие 30 дней (1 сегмент) и сформулировать оффер в 1 предложение *(done 2026-04-29: primary ICP на 14 дней + оффер)*
- [x] Запланировать Phase 4 (Image Generation Pipeline): выписать 5 планов 04-01..04-05 и оценить время *(done 2026-05-03)*
- [x] Добавить guardrails для LLM/агентов: лимит стоимости/итераций + валидация структурированных ответов *(done 2026-05-03)*
- [x] Спроектировать programmatic SEO шаблон: summary-first + FAQ + таблица + CTA (30–50 страниц пилот) *(done 2026-05-04)*

## 2026-04-29
- [x] Выбрать 1 primary student ICP на 14 дней (экзамен/дедлайн/новая профессия) и сформулировать оффер в 1 строку (student-first) *(done 2026-04-29)*
- [x] Определить activation event: что именно считается первой meaningful learning session (логика + событие + метрика) *(done 2026-04-29)*
- [x] Сформулировать «dosage + progress promise» (D2C аналог outcomes-based): сколько сессий/нед и какой измеримый прогресс обещаем/компенсируем *(done 2026-05-10)*
- [ ] Набросать прототип сценария «tutor + 2 peers» для 1 темы (дешевый social learning эффект) и решить, что меряем в A/B
- [ ] Прописать guardrails по unit economics: лимит шагов/токенов/контекста + smart routing моделей по сложности шага

## 2026-04-30
- [ ] Встроить в определение meaningful session Socratic/scaffolded паттерн: студент сначала отвечает/рассуждает, AI не дает готовый ответ сразу
- [ ] Добавить step-level feedback в сценарий первой сессии: после ответа студент получает конкретный следующий шаг, а не просто «верно/неверно»
- [ ] Сформулировать durable-skill guardrail: минимум 1 вопрос на рефлексию «почему это верно?» или «как бы ты решил похожую задачу?»
- [ ] Сформировать простой тарифный черновик: базовая подписка + лимит N meaningful sessions/нед + понятный апгрейд
- [ ] Добавить cost guardrails для AI-сессий: caps по шагам/токенам и routing дешевой/дорогой модели по типу учебного шага

## 2026-05-01
- [ ] Позиционирование (экзамен-ICP): написать 10 личных сообщений в 2–3 сообщества (Telegram/ВК) с оффером «план на каждый день с проверкой» и ссылкой на продукт; собрать 3 ответа/отказа и выписать причины
- [ ] Retention loop: добавить Exam Streak (счетчик дней подряд) + вечерний reminder только если за день не было `meaningful_learning_session_completed`
- [ ] Монетизация (WTP): зафиксировать paywall на 5-й meaningful session и протестировать цену 299 vs 499 ₽ (минимальный copy + кнопка “оплатить”/“позже”)
- [ ] Learning data moat: определить минимальные 3 поля semantic learning memory, которые обновляются после каждой meaningful session (weakest_topic, misconception_tag, next_topic)
- [ ] Метрики: завести простой срез D0-D1 Activation Rate и D1/D7 retention по exam_date (есть/нет) и subject

## 2026-05-06
- [x] Обновить `strategy/annual-product-strategy.md` под новый wedge: **D2C book-to-habit AI companion** (заменить student/exam как primary), пересобрать NSM/activation/retention под 14-дневный MVP *(done 2026-05-06)*
- [x] Выбрать 3 стартовые книги для MVP (Atomic Habits / 7 навыков / 4-часовая рабочая неделя) и сделать быстрый старт без upload (книга→цель→Day 1) *(done 2026-05-06)*
- [ ] Зафиксировать activation event для wedge: `book_habit_day1_completed` и вывести в аналитике D0 start→Day1 completion
- [ ] Переписать задания Day 1–3 в формате implementation intentions (if-then) + выбор триггера пользователем
- [ ] Добавить “grace day” (1 пропуск без обнуления streak) для снижения отвалов после первого пропуска
- [ ] Streak: добавить micro-reward (минимальная анимация/бейдж) на продление серии, особенно Day 1–7
- [ ] Тест монетизации: paywall/lead-capture после 3 выполненных заданий (варианты 299 ₽ за 30-дневный план vs 699 ₽ за месяц доступа)

## 2026-05-07
- [ ] Обновить daily: собрать инсайты по streak/grace day и if-then механикам + связать с метриками MVP

## 2026-05-08
- [ ] Day 1–3: добавить if-then + выбор триггера + (A/B) 30-сек mental rehearsal перед подтверждением выполнения
- [ ] Paywall/lead-capture после 3 выполненных заданий: сравнить 299 ₽ за 30-дневный план vs 699 ₽/мес доступа (минимальный копирайт)
- [ ] Landing/шаринг: сделать публичный артефакт "7-дневный план по Atomic Habits" (без upload) для ручного набора 50–100 пользователей

## 2026-05-09
- [ ] Day 1–3 контент (Atomic Habits): выписать 3 задания в формате if-then (≤10 минут) + 3 варианта триггера (время/место/событие) как baseline для генерации
- [ ] Онбординг: добавить выбор триггера с дефолтом (чтобы не увеличивать drop-off), сохранить как часть плана
- [ ] Retention после Day 7 (черновик): концепт «Day 8: закрепление внедрения» (1 экран) — inspired by Readwise Mastery daily ritual

## 2026-05-31
- [ ] Синхронизировать `/data/workspace/4teacher/.planning/PROJECT.md` и `.planning/STATE.md` с Phase 8 Habit Tracker из `.planning/ROADMAP.md` — зачем: убрать конфликт между lesson-illustrations фокусом и book-to-habit MVP; метрика/риск: снижает solo-founder execution risk и риск строить не тот wedge
- [ ] Создать golden set для генерации Day 1–3 habit actions: 3 книги x 3 дня x 2 пользовательские цели + expected outputs в if-then формате — зачем: зафиксировать качество микро-действий до изменения модели/промптов; метрика/риск: `book_habit_day1_completed`, task_completion_rate, model drift risk
- [ ] Добавить минимальный eval-скрипт/ручной чеклист для habit action generation rubric: ≤10 минут, один trigger, связь с книгой, конкретный check-in question — зачем: не выпускать generic self-help задания под видом персонализации; метрика/риск: activation rate, D1 return, trust risk
- [ ] Спроектировать typed habit memory schema для Phase 8 (`goal`, `trigger`, `completed_action`, `friction_tag`, `confidence`) до реализации LLM-персонализации — зачем: memory должна усиливать следующий action, а не накапливать шумный чат; метрика/риск: D7 retention, memory pollution risk, personalization quality
- [ ] Добавить PostHog events для Phase 8: `habit_action_generated`, `habit_memory_written`, `book_habit_day1_completed`, `daily_habit_checkins_completed`, `habit_paywall_viewed`, `habit_paywall_clicked` — зачем: проверить loop фактами, а не ощущениями; метрика/риск: activation, NSM, paywall CTR, analytics blind spot
- [ ] Подготовить paywall artifact после 3 completed actions: экран “ты внедрил 3 действия из книги” + оффер 30-дневного плана — зачем: монетизация должна идти после value proof; метрика/риск: paywall CTR, cancellation risk, WTP validation

## 2026-06-02
- [ ] Добавить `HabitPlanState`/`HabitCheckinState` как явные state transitions (`goal -> trigger -> action_done/action_missed -> friction -> next_micro_action`) — зачем: Phase 8 должен менять состояние поведения, а не генерировать чат; метрика/риск: `book_habit_day1_completed`, D1 return, generic-chat risk
- [ ] Ввести memory write rubric после check-in: сохранять только факты, которые меняют следующий action (`completed_action`, `friction_tag`, `trigger_viability`, `confidence`) — зачем: task-focused memory снижает шум и ложную персонализацию; метрика/риск: D7 retention, memory pollution, wrong-next-action risk
- [ ] Сделать paywall progress artifact после 3 completed actions с перечислением X/Y/Z и next 30-day promise — зачем: RevenueCat-сигнал показывает, что ранний churn трудно вернуть; метрика/риск: paywall CTR, trial cancellation, perceived value
- [ ] Добавить completion-chain dashboard/query: plan created -> Day1 completed -> D1 return -> Day3 completed -> paywall viewed/clicked -> D7 retained — зачем: AI label сам по себе не удерживает, нужен измеримый loop; метрика/риск: retention blind spot, false-positive activation
- [ ] Привязать golden set к paywall copy: для каждой из 3 книг проверить, что первые 3 actions достаточно конкретны, чтобы стать доказательством прогресса на paywall — зачем: monetization copy должен опираться на реальные completed actions; метрика/риск: WTP validation, low-trust paywall

## 2026-06-03
- [ ] Добавить к habit memory event ссылку на исходный check-in/evidence snippet рядом с derived fields — зачем: снизить риск ложной персонализации и потери ground truth; метрика/риск: memory accuracy, wrong-next-action risk
- [ ] Разделить durable memory на append-only события и derived facts с полем `confidence` — зачем: не переписывать профиль пользователя после каждого check-in; метрика/риск: memory drift, faulty update risk, D7 retention
- [ ] В paywall после 3 completed actions показывать конкретные выполненные действия X/Y/Z и next 30-day promise — зачем: AI subscription retention требует visible recurring value, а не generic AI pitch; метрика/риск: paywall CTR, trial cancellation, WTP validation
- [ ] Добавить событие `habit_paywall_proof_rendered` с количеством completed actions и book slug — зачем: проверить, что monetization происходит после value proof; метрика/риск: activation-to-paywall chain, low-trust paywall
- [ ] В golden set пометить каждый generated action как `fact`, `inference` или `unsupported` относительно книги и user goal — зачем: не продавать hallucinated self-help как персонализацию; метрика/риск: trust risk, action quality score

## 2026-06-04
- [ ] Сделать paywall proof renderer, который подставляет 3 completed actions и next 30-day promise вместо generic AI copy — зачем: RevenueCat/consumer AI signals показывают, что retention требует visible recurring value; метрика/риск: `habit_paywall_proof_rendered`, paywall CTR, low-trust paywall
- [ ] Добавить memory-use eval в golden set: next action должен опираться только на confirmed facts или явно помеченные low-confidence inference — зачем: персональная память без проверки может ухудшить action и доверие; метрика/риск: wrong-next-action rate, memory accuracy, D7 retention
- [ ] Ввести prompt memory budget для check-in generation: максимум N relevant events/facts + fallback без long context — зачем: persistent companion должен быть экономичным и предсказуемым; метрика/риск: cost per check-in, latency, context pollution
- [ ] Добавить stable IDs к habit events (`book_slug`, `goal_id`, `trigger_id`, `action_id`, `checkin_id`) — зачем: habit graph должен быть проверяемым и потенциально переносимым, а не чат-логом; метрика/риск: analytics join quality, memory portability, debugging speed
- [ ] Построить completion-chain query `plan_created -> day1_completed -> d1_return -> day3_completed -> paywall_proof_rendered -> paywall_clicked` — зачем: оптимизировать именно behavior loop до монетизации; метрика/риск: activation-to-paywall conversion, retention blind spot

## 2026-06-05
- [ ] Добавить freshness-aware поля в habit memory (`memory_last_synthesized_at`, `source_checkin_id`, `evidence_snippet`, `confidence`) — зачем: свежий OpenAI memory signal показывает, что long-term companion ломается на stale/incorrect memory; метрика/риск: memory accuracy, wrong-next-action rate, trust risk
- [ ] Сделать stale-memory fallback для генерации next action: если memory устарела или low-confidence, использовать только текущие `goal + trigger + book_slug` — зачем: лучше честная неперсонализированная рекомендация, чем ложная персонализация; метрика/риск: unsupported-memory-use rate, D1/D7 retention
- [ ] Добавить `trigger_matched` в check-in и метрику `same_trigger_completed_days / active_days` — зачем: retention для AI companion должен измерять реальный жизненный слот, а не просто DAU; метрика/риск: trigger consistency, habit formation risk
- [ ] В paywall proof sheet показывать remembered context из последних 3 completed actions: действие, триггер, friction/adjustment — зачем: пользователь платит за видимый прогресс и ощущение continuity; метрика/риск: `habit_paywall_proof_rendered`, paywall CTR, low-trust paywall
- [ ] В Day 1–3 UI добавить короткую строку "что SiaMentor помнит со вчера" перед next action — зачем: memory должна быть ощутимой consumer feature, а не скрытым backend; метрика/риск: D1 return, perceived personalization, hallucinated-memory complaints

## 2026-06-06
- [ ] Добавить memory transparency line в Day 2–7: `Помню из прошлого check-in: <evidence_snippet>` + действие "неверно/забыть" — зачем: свежая волна ChatGPT memory показывает, что continuity нужна вместе с контролем пользователя; метрика/риск: memory correction rate, trust complaints, D1/D7 retention
- [ ] Ограничить MVP memory allowlist полями `goal`, `trigger`, `completed_action`, `friction`, `confidence`, `source_checkin_id` — зачем: consumer backlash вокруг persistent memory делает широкий life profile рискованным; метрика/риск: privacy/trust risk, unsupported-memory-use rate
- [ ] Добавить stale-memory UX state: если последний check-in старше N дней, показывать restart/grace-day flow вместо уверенной персонализации — зачем: устаревшая memory хуже неперсонализированного action; метрика/риск: stale-memory usage, wrong-next-action rate, return-after-gap conversion
- [ ] В paywall proof renderer добавить блок "что мы уже знаем, что у тебя работает" из 3 completed actions и triggers — зачем: продавать observable continuity, а не общий AI pitch; метрика/риск: `habit_paywall_proof_rendered`, paywall CTR, perceived value
- [ ] В golden set добавить privacy/trust rubric: next action не должен раскрывать или использовать memory вне habit domain — зачем: доверие D2C companion зависит от узкой и объяснимой памяти; метрика/риск: trust-risk eval failures, hallucinated-memory complaints

## 2026-06-07
- [ ] Разделить habit memory storage на append-only `HabitCheckinEvent` и derived `HabitMemoryFact` с `source_checkin_id` — зачем: свежий backlash вокруг summarized memory показывает, что синтез без evidence снижает доверие; метрика/риск: memory correction rate, unsupported-memory-use rate, wrong-next-action risk
- [ ] Добавить UI affordance `верно / исправить / забыть` рядом с memory transparency line — зачем: OpenAI Memory FAQ закрепляет expectation пользовательского контроля над memory; метрика/риск: correction usage, trust complaints, D1/D7 retention
- [ ] В golden set проверять, что derived memory не обобщает конкретный habit fact в lifestyle/personality summary — зачем: для book-to-habit важен проверяемый trigger/action, а не широкий personal profile; метрика/риск: generalized-memory eval failures, privacy risk
- [ ] Добавить `same_trigger_completed_days / active_days` в completion-chain dashboard — зачем: companion должен менять реальное поведение в повторяемом жизненном слоте, а не только поднимать DAU; метрика/риск: habit formation signal, false-positive retention
- [ ] Переписать paywall proof copy вокруг 3 evidence-backed actions: `ты уже сделал X/Y/Z; следующий 30-day план усилит trigger N` — зачем: value proof понятнее, чем generic AI subscription; метрика/риск: `habit_paywall_proof_rendered`, paywall CTR, WTP validation

## 2026-06-08
- [ ] Добавить `habit_memory_corrected` event для действий `верно / исправить / забыть` — зачем: свежий рынок memory summaries показывает, что контроль пользователя становится trust primitive; метрика/риск: correction rate, trust complaints, unsupported-memory-use rate
- [ ] Ввести eval failure `overgeneralized_memory` для derived facts — зачем: memory не должна превращать конкретный habit evidence в широкий lifestyle/personality profile; метрика/риск: overgeneralization failures, wrong-next-action risk, privacy risk
- [ ] Обновить Day 1-3 golden set рубрикой scaffolded action: один trigger, действие до 10 минут, check-in question, следующий шаг зависит от ответа — зачем: AI tutoring evidence требует помогать думать/действовать, а не просто выдавать совет; метрика/риск: action quality score, D1 return, generic-advice risk
- [ ] Добавить в completion-chain dashboard `habit_memory_corrected`, `overgeneralized_memory_eval_failed`, `same_trigger_completed_days / active_days` — зачем: retention companion надо мерить через качество памяти и повторяемость trigger, а не только через DAU; метрика/риск: habit formation signal, trust metric blind spot
- [ ] В paywall proof renderer показывать `source_checkin_id`-backed actions X/Y/Z и trigger pattern — зачем: paywall после 3 completed actions должен продавать доказанную continuity; метрика/риск: `habit_paywall_proof_rendered`, paywall CTR, WTP validation
- [ ] Протестировать mobile-first экран Day 2 check-in с memory controls `верно / исправить / забыть` перед today's action — зачем: пользователь должен доверять памяти companion до того, как она влияет на следующий habit-шаг; метрика/риск: correction usage, wrong-next-action complaints, D1 return

## 2026-06-09
- [ ] Переписать paywall proof copy как artifact прогресса: `ты сделал X/Y/Z`, `trigger N сработал`, `30-day plan усилит этот ритм` — зачем: свежий consumer AI сигнал показывает WTP, но retention требует видимого recurring value; метрика/риск: `habit_paywall_proof_rendered`, paywall CTR, trial cancellation
- [ ] Добавить в paywall renderer поле `best_trigger_pattern` на базе completed check-ins — зачем: продавать не "AI", а обнаруженный жизненный слот пользователя; метрика/риск: WTP validation, perceived personalization, low-trust paywall
- [ ] Ввести MVP memory domain boundary: запрещать derived facts шире habit-домена (`goal`, `trigger`, `action`, `friction`, `confidence`) — зачем: companion memory должна быть контролируемой и не превращаться в широкий life profile; метрика/риск: privacy/trust risk, overgeneralized_memory eval failures
- [ ] Добавить stale/grace recovery event `habit_restart_after_gap_started` — зачем: RevenueCat/retention signals напоминают, что churn после пропуска надо обрабатывать отдельным loop, а не обычным Day N; метрика/риск: return-after-gap conversion, D7 retention, streak-break churn
- [ ] Проверить Day 1-3 golden set на scaffolded action rubric: trigger выбран пользователем, действие ≤10 минут, есть check-in question, next action зависит от ответа — зачем: AI tutor evidence переносится в habit companion как "помогает действовать", а не "дает совет"; метрика/риск: action quality score, D1 return, generic-advice risk
- [ ] Протестировать mobile-first paywall proof screen после 3 completed actions: evidence cards X/Y/Z + best trigger pattern + 30-day offer — зачем: paywall должен продавать доказанный прогресс, а не generic AI subscription; метрика/риск: `habit_paywall_proof_rendered`, paywall CTR, low-trust paywall

## 2026-06-11
- [ ] Спроектировать и проверить mobile-first Day 2–7 memory trust gate: memory evidence line + `верно / исправить / забыть` перед next action — зачем: цепочка книга -> действие -> привычка должна быть персонализированной, но контролируемой; метрика/риск: `habit_memory_corrected`, daily check-in completion, wrong-next-action complaints
- [ ] Добавить Day 2–7 memory transparency line с действиями `исправить / забыть` — зачем: consumer AI trust сейчас строится вокруг приватной и контролируемой памяти, а не просто "long-term memory"; метрика/риск: `habit_memory_corrected`, trust complaints, wrong-next-action risk
- [ ] Ввести hard allowlist для `HabitMemoryFact`: `goal`, `trigger`, `completed_action`, `friction`, `confidence`, `source_checkin_id` — зачем: EDPS companion signal показывает, что personalization/memory повышает privacy risk; метрика/риск: `memory_outside_habit_domain`, unsupported-memory-use rate, overgeneralized_memory eval failures
- [ ] Добавить в golden set failure case `generic_advice_without_trigger` — зачем: AI tutoring тренд уходит в guided workflows, а book-to-habit должен помогать действовать, не пересказывать книгу; метрика/риск: action quality score, D1 return, generic-advice risk
- [ ] Пересобрать paywall proof renderer вокруг `completed_actions + best_trigger_pattern + friction_adjustment + 30_day_promise` — зачем: AI apps имеют ранний WTP, но слабую retention, поэтому paywall должен продавать видимый recurring value; метрика/риск: `habit_paywall_proof_rendered`, paywall CTR, trial cancellation
- [ ] Добавить `same_trigger_completed_days / active_days` в completion-chain dashboard — зачем: для habit companion важна повторяемость жизненного слота, а не только DAU или число check-in; метрика/риск: habit formation signal, false-positive retention

## 2026-06-10
- [x] Спроектировать mobile-first `Grace restart` экран для пропуска 24–72 часа: evidence snippet + grace day + микро-действие ≤5 минут + calm restart option — зачем: цепочка книга -> действие -> привычка должна восстанавливать пользователя после паузы; метрика/риск: `grace_day_used`, `habit_restart_after_gap_completed`, return-after-gap conversion *(done 2026-06-10: добавлен HTML-макет `design/mockups/grace-restart-mobile.html`)*
- [ ] Добавить в Phase 8 события `grace_day_used`, `habit_restart_after_gap_started`, `habit_restart_after_gap_completed`, `hours_since_missed_checkin` — зачем: streak должен восстанавливать пользователя после пропуска, а не только показывать серию; метрика/риск: return-after-gap conversion, D7 retention, streak-break churn
- [ ] Сделать recovery flow для пропуска до 72 часов: короткий restart экран + сохранение streak через grace day + новый микро-шаг ≤5 минут — зачем: свежие streak/recovery данные указывают, что окно возврата быстро закрывается; метрика/риск: restart completion rate, D3/D7 retention
- [ ] В paywall proof renderer добавить связку `best_trigger_pattern + friction_adjustment + next_30_day_promise` — зачем: RevenueCat показывает высокий AI WTP, но слабую AI retention; платить должны за доказанную continuity, а не за AI-label; метрика/риск: `habit_paywall_proof_rendered`, paywall CTR, refund/trial cancellation
- [ ] Ввести hard domain boundary для memory writes и eval `memory_outside_habit_domain` — зачем: EDPS AI companions signal поднимает privacy risk вокруг personalization/memory; метрика/риск: privacy/trust risk, unsupported-memory-use rate, overgeneralized_memory failures
- [ ] Переписать Day 2-7 check-in prompt как guided action flow: вспомнить evidence snippet, спросить про trigger, выбрать friction, предложить следующий if-then шаг — зачем: AI tutor evidence переносится в habit MVP как scaffolded behavior change; метрика/риск: action quality score, `daily_habit_checkins_completed`, generic-advice risk

## 2026-06-12
- [ ] Зафиксировать inventory текущих экранов для переезда на новый mobile-first макет: onboarding, Day 1 action, Day 2-7 check-in, memory trust gate, recovery, paywall proof — зачем: переезд должен собрать MVP-flow, а не стать визуальным редизайном ради редизайна; метрика/риск: меньше пропущенных состояний, быстрее реализация первой недели
- [ ] Собрать flow map нового макета `book -> action -> check-in -> memory -> recovery -> paywall proof` с данными `goal`, `trigger`, `completed_action`, `friction`, `confidence`, `source_checkin_id` — зачем: понять, где memory влияет на следующий шаг и где пользователь её контролирует; метрика/риск: wrong-next-action risk, implementation clarity
- [ ] Доработать новый layout shell под ежедневный habit loop: основной action surface, progress area, место для memory evidence и CTA следующего шага — зачем: интерфейс должен ощущаться как companion habit system, а не generic chat; метрика/риск: D1/D7 retention, generic-chat risk
- [ ] Встроить Day 2-7 memory trust gate в новый макет перед today's action: evidence line + `верно / исправить / забыть` — зачем: переезд на новый макет должен сразу нести controllable memory как trust primitive; метрика/риск: `habit_memory_corrected`, trust complaints, wrong-next-action complaints
- [ ] Встроить recovery state 24-72h в новый макет: calm restart + grace day + evidence snippet + микро-действие ≤5 минут — зачем: пользователь должен возвращаться после пропуска внутри того же MVP-flow; метрика/риск: `habit_restart_after_gap_completed`, return-after-gap conversion, D7 retention
- [ ] Встроить paywall proof state после 3 completed actions в новый макет: actions X/Y/Z + cautious trigger pattern + friction adjustment + CTA 30-day plan — зачем: monetization должна появляться после доказанного прогресса в том же интерфейсном пути; метрика/риск: `habit_paywall_proof_rendered`, paywall CTR, trial cancellation
- [ ] Проверить новый mobile-first MVP-flow end-to-end на перегруз, ранний paywall, ложную уверенность memory и понятность следующего шага — зачем: перед implementation надо поймать продуктовые провалы на макете; метрика/риск: usability risk, wrong-pattern complaints, low-trust paywall
- [ ] Собрать mobile-first Day 2–7 memory trust gate: evidence line `Помню: trigger/action/friction` + `верно / исправить / забыть` перед today's action — зачем: consumer AI trust сейчас строится на контролируемой памяти, а не на обещании "AI помнит"; метрика/риск: `habit_memory_corrected`, unsupported-memory-use rate, wrong-next-action complaints
- [ ] Ввести eval failure `memory_outside_habit_domain` для любых derived facts вне `goal`, `trigger`, `completed_action`, `friction`, `confidence`, `source_checkin_id` — зачем: EDPS companion risk показывает, что широкая персонализация превращает MVP в privacy-sensitive profile; метрика/риск: privacy/trust risk, overgeneralized_memory failures
- [ ] Обновить Day 1–3 golden set рубрикой guided action: выбранный trigger, действие ≤10 минут, check-in question, next action зависит от ответа — зачем: AI tutoring сигнал переносится в book-to-habit как scaffolded behavior change, а не пересказ книги; метрика/риск: action quality score, `book_habit_day1_completed`, generic-advice risk
- [ ] Пересобрать paywall proof renderer вокруг `completed_actions + best_trigger_pattern + friction_adjustment + next_30_day_promise` — зачем: RevenueCat 2026 показывает retention risk у AI apps, поэтому paywall должен продавать visible continuity после 3 actions; метрика/риск: `habit_paywall_proof_rendered`, paywall CTR, trial cancellation
- [ ] Добавить recovery-chain events `hours_since_missed_checkin`, `grace_day_used`, `habit_restart_after_gap_completed` и dashboard-срез return-after-gap — зачем: streak без восстановления не удерживает пользователя после первого пропуска; метрика/риск: restart completion rate, D7 retention, streak-break churn
- [ ] Протестировать mobile-first paywall proof после 3 completed actions: completed actions X/Y/Z + осторожный best trigger pattern + friction adjustment + CTA 30-day plan — зачем: paywall должен продавать доказанную цепочку книга -> действие -> привычка, а не generic AI; метрика/риск: `habit_paywall_proof_rendered`, paywall CTR, trial cancellation, wrong-pattern complaints

## 2026-06-13
- [ ] Переформулировать onboarding/paywall copy из broad AI companion в bounded habit companion: "7 дней действий из книги + проверяемая память по привычке" — зачем: свежий Apple/Siri signal усиливает boundaries/privacy, а не эмоциональную зависимость; метрика/риск: trust complaints, low-trust paywall, onboarding conversion
- [ ] Добавить Day 2-7 memory evidence line с тремя действиями `верно / исправить / забыть` перед today's action — зачем: privacy-first consumer AI требует контролируемой памяти, иначе персонализация выглядит как слежка; метрика/риск: `habit_memory_corrected`, unsupported-memory-use rate, wrong-next-action complaints
- [ ] Ввести eval `memory_outside_habit_domain` и hard allowlist для derived facts: `goal`, `trigger`, `completed_action`, `friction`, `confidence`, `source_checkin_id` — зачем: EDPS companion risk показывает опасность continuous profiling; метрика/риск: privacy/trust risk, overgeneralized_memory failures
- [ ] Собрать proof paywall state после 3 completed actions: X/Y/Z actions + cautious trigger pattern + friction adjustment + next 30-day promise — зачем: RevenueCat показывает retention weakness у AI apps, значит paywall должен продавать visible recurring value; метрика/риск: `habit_paywall_proof_rendered`, paywall CTR, trial cancellation
- [ ] Добавить recovery-first streak dashboard: `hours_since_missed_checkin`, `grace_day_used`, `habit_restart_after_gap_completed`, return-after-gap conversion — зачем: streak break может стать quit moment, если нет отдельного восстановления; метрика/риск: D7 retention, streak-break churn, restart completion rate
- [ ] Спроектировать gated paywall state `paywall_blocked` до 3 completed actions и `ready_for_proof` после 3 actions — зачем: monetization должна следовать за доказанной цепочкой книга -> действие -> привычка, а не появляться как generic AI subscription; метрика/риск: `habit_paywall_proof_rendered`, paywall CTR, early-paywall churn

## 2026-06-14
- [ ] Добавить Day 2-7 memory evidence line в основной habit surface: `Помню: <trigger/action/friction>` + `верно / исправить / забыть` — зачем: Apple/Siri mainstream signal усиливает privacy-bounded personal context; метрика/риск: `habit_memory_corrected`, unsupported-memory-use rate, wrong-next-action complaints
- [ ] Собрать cohort funnel dashboard `plan_created -> day1_completed -> d1_return -> day3_completed -> paywall_proof_rendered -> d7_retained` — зачем: Appcues retention guidance напоминает смотреть drop-off по когортам, а не только NSM; метрика/риск: activation-to-paywall conversion, D7 retention, retention blind spot
- [ ] Переписать paywall copy вокруг proof loop: X/Y/Z completed actions, cautious trigger pattern, friction adjustment, next 30-day promise — зачем: RevenueCat показывает, что AI subscription retention слабее non-AI; метрика/риск: `habit_paywall_proof_rendered`, paywall CTR, trial cancellation
- [ ] Встроить recovery restart после 24-72h пропуска: evidence snippet + grace day + микро-действие ≤5 минут + calm CTA — зачем: streak safety valves снижают риск quit moment после первого пропуска; метрика/риск: `grace_day_used`, `habit_restart_after_gap_completed`, return-after-gap conversion
- [ ] Ограничить product copy формулой bounded habit companion, не emotional/life companion — зачем: свежие Apple/Siri boundaries показывают, что consumer trust строится на полезности и ограничениях; метрика/риск: onboarding conversion, trust complaints, low-trust paywall
- [ ] Ввести monetization gate `paywall_blocked` до 3 completed actions и `ready_for_proof` после 3 actions — зачем: paywall должен следовать за доказанной цепочкой книга -> действие -> привычка; метрика/риск: early-paywall churn, `habit_paywall_proof_rendered`, paywall CTR
