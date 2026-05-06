# SiaMentor: 12-месячная стратегия развития продукта

Обновлено: 2026-05-06

## 1. Главная гипотеза

SiaMentor развивается как **D2C book-to-habit AI companion**: не EdTech-платформа и не AI-чат, а персональный AI-компаньон, который превращает self-development книгу в 7-дневный план конкретных действий/привычек и ежедневно доводит пользователя до выполнения через check-in и рефлексию.

**ICP (primary wedge):** Люди 25–40 лет, читающие self-development / business / psychology / productivity книги, испытывающие боль: *«прочитал, вдохновился — через неделю ничего не изменилось»*. Это читатели, а не студенты. Покупают книги, не курсы.

**Positioning statement:** «Не просто читай. Внедряй. SiaMentor превращает любую книгу в 7-дневный план действий — и доводит до результата каждый день.»

**Главная бизнес-гипотеза:** Пользователь готов платить не за «AI-чат» и не за «пересказ книги», а за структуру внедрения + ежедневное сопровождение + ощущение измеримого прогресса. Willingness-to-pay выше, чем у EdTech: покупатель книг за 500–2000 ₽ психологически готов платить за «практический результат от книги».

**Чем отличаемся:**
- От ChatGPT: не «чат», а план + ритуал + трек прогресса + память внедрения
- От Blinkist/summary apps: не «узнать», а «сделать»
- От трекеров привычек: не пустой трекер, а привычки, выведенные из конкретной книги под цель пользователя
- От Mentorist/ReadAct: глубина персонализации (книга→цель→план) + метрики прогресса + retention mechanics

**Статус student/exam wedge:** Deferred — не abandoned. EdTech ICP (экзамен-готовка) остаётся потенциальным расширением в Phase 4 после доказанного book-to-habit core. Programmatic SEO под ЕГЭ-темы (спроектирован 2026-05-04) сохраняется как low-cost acquisition asset.

## 2. North Star Metric

**`daily_habit_checkins_completed` — ежедневные выполненные check-in + micro-action за день.**

Определение единицы: пользователь считается активным за день, если выполнил ≥1 micro-action из своего 7-дневного плана И отметил check-in в приложении.

Почему этот NSM:
- Отражает *completed behaviour*, не visit (visit = vanity metric)
- Напрямую предсказывает D7/D30 retention и paywall conversion
- Соответствует Reforge-типологии: Engagement/Habit-продукт (не Productivity, не Attention)
- Streak по этой метрике мотивирует сильнее, чем weekly goal (Scientific American, 2024)

**Input-метрики (управляемые рычаги):**

| Метрика | Влияет на NSM через |
|---------|---------------------|
| `book_habit_day1_completed` (activation) | Первый check-in → запускает streak |
| task_completion_rate (daily micro-actions) | Количество completed check-ins |
| streak_continuation_rate | Удержание привычки check-in |
| grace_day_usage_rate | Снижение churn после первого пропуска |
| D7 retention | Масштаб NSM за неделю |

## 3. Годовая цель

К концу 12 месяцев SiaMentor должен доказать одну узкую, платежеспособную book-to-habit нишу, в которой продукт:

- даёт пользователю ощутимый результат внедрения (≥3 выполненных микро-действия из книги за 7 дней)
- удерживает пользователей минимум D30 > 8% (benchmark Health&Fitness category)
- имеет повторяемый канал привлечения без большого бюджета (organic-first)
- имеет первичную монетизацию: paywall после 3 completed actions → 299 ₽/30-дней
- накапливает habit implementation memory: книги, цели, выполненные действия, streak history

**Стартовые книги для MVP (без upload):**
1. Atomic Habits (James Clear) — самая популярная книга о привычках, огромный органический спрос
2. «7 навыков высокоэффективных людей» (Stephen Covey) — business audience, высокий WTP
3. «4-часовая рабочая неделя» (Tim Ferriss) — productivity/entrepreneur audience

Выбор: максимальная узнаваемость + разные аудитории + проверяемый спрос через SEO-инструменты.

**Не цель первого года:**
- Строить универсальную платформу «для любой книги» (сначала 3 фиксированные)
- EdTech/student positioning как primary
- Enterprise или B2B продажи
- Upload собственных книг (friction → позже)

## 4. Стратегические фокусы

### 4.1. Book-to-habit позиционирование

Главный риск — размытость: «ещё один AI-чат» или «ещё один саммари-сервис». Нужен чёткий отказ от обоих.

**Формула онбординга (2 минуты до первого плана):**
1. Выбор книги из 3 (без upload)
2. Ввод цели пользователя одной строкой («хочу вставать в 5 утра», «хочу читать 30 мин/день»)
3. AI генерирует 7-дневный план: 7 микро-действий в формате if-then
4. Пользователь видит Day 1 → выполняет → отмечает check-in → activation event `book_habit_day1_completed`

Финансовая логика: чем конкретнее обещание (книга→результат за 7 дней), тем выше WTP и ниже CAC.

### 4.2. Habit loop mechanics (retention before scale)

Три retention-механики, встроенных в продукт:

**Streak по ежедневному check-in:**
- Streak = выполнил micro-action + отметил check-in сегодня
- 7-day streak → 2.4x выше вероятность возврата завтра (Duolingo engineering data)
- Визуализация прогресса: «День 3 из 7 — ты внедряешь Atomic Habits»

**Grace day (Streak Freeze):**
- 1 пропуск в 7-дневном цикле без обнуления streak
- Снижение churn на ~21% у at-risk пользователей (Duolingo data)
- Активируется автоматически при первом пропуске в цикле

**Implementation intentions (if-then format):**
- Каждое задание дня = «Если [триггер], то [микро-действие] (≤10 минут)»
- Пользователь выбирает свой триггер (время/место/событие) при онбординге
- NIH-backed: повышает task completion rate vs просто «сделать X сегодня»

### 4.3. Productized habit loop

Ядро продукта:

1. Пользователь выбирает книгу + формулирует цель
2. AI строит 7-дневный план (7 micro-actions в if-then формате)
3. Day N: пользователь видит задание дня
4. Выполняет микро-действие (≤10 минут)
5. Отмечает check-in → streak обновляется → `daily_habit_checkins_completed` +1
6. AI даёт краткую рефлексию («что получилось?»)
7. Пользователь видит прогресс (3/7 дней, streak) → возвращается завтра

После 3 completed actions → paywall: «Продолжи 30-дневный план — 299 ₽»

Все фичи, не усиливающие этот loop, вторичны.

### 4.4. Solo-founder GTM (Tier-структура)

**Tier 1 — Бесплатно, высокий leverage (сейчас):**
- Telegram-каналы по self-improvement и книгам (аудитории 10k–500k): 10 личных сообщений в 2–3 канала с конкретным оффером «7-дневный план по Atomic Habits»
- BookTok / Reels под запросы «[Book Name] action plan» — органический охват без бюджета
- Programmatic SEO: «[Book Name] план действий», «как внедрить [книгу]» (расширение SEO-паттерна из 999.5)

**Tier 2 — После D7 retention > 20%:**
- Публичные case studies «книга→результат за 7 дней»
- Referral: «поделись своим планом» → invite-flow
- Короткие демонстрации habit loop (screen recording Day 1–3)

**Tier 3 — После первых платящих пользователей:**
- Paid acquisition (Telegram Ads / VK)
- Partnership с book bloggers / каналами о self-improvement

Не приоритет на первом этапе: широкий бренд-маркетинг, дорогая реклама, enterprise, школьные партнёрства.

## 5. Дорожная карта на 12 месяцев

### Фаза 1: MVP validation — 14 дней (текущая)

Цель: доказать, что пользователь доходит до `book_habit_day1_completed` и возвращается на Day 2.

**Три параллельных эксперимента:**

**Эксперимент A: «7-дневный план за 2 минуты» (без upload)**
- Гипотеза: быстрый старт (выбор книги из 3) повышает start → first plan → Day 1 completion
- Действие: онбординг = выбор книги + цель + немедленная выдача Day 1 задания
- Метрика успеха: activation rate `book_habit_day1_completed` ≥ 30% от начавших онбординг

**Эксперимент B: If-Then формат заданий Day 1–3**
- Гипотеза: формат «Если [триггер], то [действие]» снижает трение выполнения
- Действие: переписать Day 1 задания всех 3 книг в if-then + поле выбора триггера
- Метрика успеха: task_completion_rate ≥ 50% на Day 1

**Эксперимент C: Grace day для streak**
- Гипотеза: 1 бесплатный «skip» в 7-дневном цикле уменьшает отвал после первого пропуска
- Действие: автоматическая активация grace day при первом пропуске в цикле
- Метрика успеха: D7 retention пользователей с ≥1 пропуском на 5+ п.п. выше контрольной группы

**Главный результат Фазы 1:**
- Доказан activation path (≥30% доходят до Day 1)
- Понятно, почему пользователь возвращается на Day 2
- Есть сигнал willingness-to-pay после paywall (≥5% click-through на 299 ₽)

### Фаза 2: Retention loop и первая монетизация

Цель: превратить продукт из «попробовал раз» в регулярный ритуал с первыми платежами.

Ключевые задачи:
- Habit memory: книги, цели, выполненные действия, streak history
- 30-дневный план как продукт-результат (расширение после 7-дневного)
- Paywall оптимизация: A/B 299 ₽/30 дней vs 699 ₽/месяц доступа
- Push/Telegram reminder только если за день нет completed check-in
- Progress dashboard: «ты внедрил X действий из книги Y»
- Первые платящие пользователи

**Главный результат:** D30 > 8%, первые платежи, понятный paid package.

### Фаза 3: Scalable acquisition и content engine

Цель: построить повторяемый low-cost канал привлечения.

Ключевые задачи:
- SEO под «[Book Name] план действий / action plan / как внедрить»
- Programmatic pages: одна страница на книгу (15–20 книг)
- Public habit plans: «7-дневный план по Atomic Habits» как shareable artifact
- BookTok / Reels: short-form контент из реальных habit loops
- Referral: «поделись своим планом» → invite-flow
- A/B тесты onboarding copy и CTA

**Главный результат:** 1–2 органических канала, CAC близок к нулю, activation rate растёт.

### Фаза 4: Defensibility и expansion

Цель: укрепить habit memory как moat, расширить на соседние ICP.

Ключевые задачи:
- Глубокая habit implementation memory (история всех книг, целей, паттернов пользователя)
- Персонализация: AI рекомендует следующую книгу на основе истории
- Upload собственных книг (устранение friction для power users)
- Расширение на EdTech ICP (student/exam) — проверенный паттерн из основного wedge
- Когортная аналитика retention по книгам и целям
- Упаковка traction narrative для грантов / акселераторов

## 6. Метрики

### Activation

| Метрика | Минимальный порог | Benchmark |
|---------|-------------------|-----------|
| `book_habit_day1_completed` rate | ≥ 30% от начавших онбординг | Health&Fitness apps: 25–40% |
| Time to first plan | ≤ 2 минуты | — |
| Task completion rate Day 1 | ≥ 50% | — |

### Retention

| Метрика | Цель MVP | Цель Phase 2 | Benchmark |
|---------|----------|--------------|-----------|
| D1 retention | ≥ 40% | ≥ 50% | H&F: ~20% (наш if-then должен быть выше) |
| D7 retention | ≥ 20% | ≥ 30% | H&F: ~8–10% |
| D30 retention | — | ≥ 8% | H&F: ~3–4% |
| streak_continuation_rate | ≥ 60% | ≥ 70% | Duolingo: 50–65% |
| `daily_habit_checkins_completed` per active user | ≥ 5/7 дней | ≥ 6/7 дней | — |

### Monetization

| Метрика | Цель |
|---------|------|
| Paywall CTR (после 3 completed actions) | ≥ 5% |
| Trial-to-paid conversion | ≥ 15% |
| ARPU (первый месяц) | 299–699 ₽ |
| Refund rate | < 10% |

### North Star

`daily_habit_checkins_completed` — абсолютное число completed check-ins за день (активные пользователи).

## 7. Что не делать в первый год

- Не строить универсальный «загрузи любую книгу» — сначала 3 фиксированные книги без upload
- Не соревноваться с ChatGPT как «ещё один AI-чат» — позиционирование строго как habit companion
- Не делать student/exam positioning primary до доказанного book-to-habit core
- Не масштабировать рекламу до D7 retention > 20%
- Не добавлять фичи, не усиливающие habit loop (summary, quiz, social feed, marketplace)
- Не уходить в enterprise/B2B до доказанного D2C traction
- Не строить сложную социальную сеть до доказанного core value

## 8. Правило для всех будущих действий

Каждое действие должно явно отвечать минимум на один вопрос:

- усиливает ли это habit loop (streak / check-in / micro-action completion)?
- повышает ли `book_habit_day1_completed` activation rate?
- увеличивает ли `daily_habit_checkins_completed` NSM?
- приближает ли к первому платежу (paywall conversion)?
- создаёт ли organic acquisition asset (SEO / BookTok / referral)?
- снижает ли solo-founder execution risk?

Если действие не отвечает ни на один из этих вопросов — не делать.

## 9. Формат ежедневных советов

Каждый Telegram daily update строится так:

1. Стратегическая тема дня (связь с book-to-habit wedge)
2. Как она связана с текущей фазой (MVP validation / retention / acquisition)
3. 3–5 действий максимум
4. Для каждого действия:
   - фаза стратегии
   - зачем делать (habit loop / activation / NSM / paywall / acquisition / solo-risk)
   - финансовый эффект
   - метрика, которую должно улучшить
   - effort (часы/дни)
   - минимальный следующий шаг
5. Ссылка на обновлённую wiki и checklist

## 10. Первый фокус на ближайшие 14 дней

Тема: MVP validation — доказать book-to-habit activation и ранний сигнал retention.

**Три эксперимента (параллельно):**

**A. «7-дневный план за 2 минуты»**
- Действие: сделать онбординг = выбор из 3 книг (Atomic Habits / 7 навыков / 4ЧРН) + цель + немедленная выдача Day 1 задания в if-then формате
- Метрика: activation rate `book_habit_day1_completed` ≥ 30%

**B. If-then задания Day 1–3**
- Действие: переписать все задания Day 1–3 в формат «Если [триггер выбранный пользователем], то [микро-действие] (≤10 минут)»
- Метрика: task_completion_rate ≥ 50% на Day 1

**C. Grace day**
- Действие: при первом пропуске в 7-дневном цикле — автоматически активировать 1 grace day без обнуления streak; показать пользователю уведомление «Мы сохранили твой streak — вернись завтра»
- Метрика: D7 retention у пользователей с ≥1 пропуском на ≥5 п.п. выше контрольной группы

**Финансовая цель 14 дней:** доказать, что ≥5% пользователей кликают на paywall 299 ₽ после 3 completed actions — это минимальный сигнал willingness-to-pay до масштабирования.
