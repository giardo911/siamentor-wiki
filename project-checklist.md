# Project checklist


## 2026-04-28
- [x] Определить ICP на ближайшие 30 дней (1 сегмент) и сформулировать оффер в 1 предложение *(done 2026-04-29: primary ICP на 14 дней + оффер)*
- [x] Запланировать Phase 4 (Image Generation Pipeline): выписать 5 планов 04-01..04-05 и оценить время *(done 2026-05-03)*
- [x] Добавить guardrails для LLM/агентов: лимит стоимости/итераций + валидация структурированных ответов *(done 2026-05-03)*
- [x] Спроектировать programmatic SEO шаблон: summary-first + FAQ + таблица + CTA (30–50 страниц пилот) *(done 2026-05-04)*

## 2026-04-29
- [x] Выбрать 1 primary student ICP на 14 дней (экзамен/дедлайн/новая профессия) и сформулировать оффер в 1 строку (student-first) *(done 2026-04-29)*
- [x] Определить activation event: что именно считается первой meaningful learning session (логика + событие + метрика) *(done 2026-04-29)*
- [ ] Сформулировать «dosage + progress promise» (D2C аналог outcomes-based): сколько сессий/нед и какой измеримый прогресс обещаем/компенсируем
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
- [ ] Обновить `strategy/annual-product-strategy.md` под новый wedge: **D2C book-to-habit AI companion** (заменить student/exam как primary), пересобрать NSM/activation/retention под 14-дневный MVP
- [ ] Выбрать 3 стартовые книги для MVP (например: Atomic Habits, Deep Work, The Subtle Art…) и сделать быстрый старт без upload (книга→цель→Day 1)
- [ ] Зафиксировать activation event для wedge: `book_habit_day1_completed` и вывести в аналитике D0 start→Day1 completion
- [ ] Переписать задания Day 1–3 в формате implementation intentions (if-then) + выбор триггера пользователем
- [ ] Добавить “grace day” (1 пропуск без обнуления streak) для снижения отвалов после первого пропуска
- [ ] Тест монетизации: paywall/lead-capture после 3 выполненных заданий (варианты 299 ₽ за 30-дневный план vs 699 ₽ за месяц доступа)

