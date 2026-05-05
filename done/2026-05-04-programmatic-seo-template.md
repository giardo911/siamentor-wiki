---
title: "Programmatic SEO Template — SiaMentor Pilot"
date: 2026-05-04
phase: "999.5"
status: approved
---

# Programmatic SEO Template — SiaMentor Pilot

## Summary

SiaMentor таргетирует студентов, готовящихся к ЕГЭ, через programmatic SEO. Стратегия основана на формуле: один универсальный шаблон страницы + уникальный контент для каждого концепта. Шаблон состоит из четырёх содержательных секций: Summary Block (определение концепта), Concept Table (сравнительная таблица терминов), FAQ Block (реальные вопросы студентов с JSON-LD схемой) и CTA Block (призыв к регистрации).

Пилот включает 45 страниц: 25 по математике ЕГЭ и 20 по русскому языку. URL паттерн: `/ru/ege/{subject}/{slug}`. Технология: Next.js 14 SSG с `generateStaticParams` — все страницы предварительно рендерятся в статический HTML при сборке, что обеспечивает корректную индексацию. Данные хранятся в статических JSON-файлах для пилота, с возможностью перейти на PostgreSQL при масштабировании.

Критическое требование для защиты от Google's "scaled content abuse" penalty (март 2024): каждая страница должна содержать реально уникальный контент — не шаблонный текст с заменой одного слова. Метрика успеха пилота: >200 кликов в месяц и >1,000 показов из поиска через 60 дней после деплоя. PostHog уже подключён для трекинга конверсии через событие `seo_cta_click`.

---

## Page Template Specification

### URL Structure

```
Pattern:  /ru/ege/{subject}/{slug}

Examples:
  /ru/ege/matematika/chto-takoe-proizvodnaya-ege
  /ru/ege/matematika/kak-reshat-logarifmy-ege
  /ru/ege/russkiy/chto-takoe-prichastie-ege

Hub pages:
  /ru/ege/                    — каталог предметов
  /ru/ege/matematika/         — все темы по математике
  /ru/ege/russkiy/            — все темы по русскому

Slug rules:
  - Только строчные латинские буквы, цифры, дефисы
  - Транслитерация кириллицы (ГОСТ 7.79-2000 System B)
  - Всегда заканчивается на "-ege" (сигнал намерения)
  - Максимум 60 символов
```

### HTML Document Head

```
<title>: "{ConceptTitle} — ЕГЭ {SubjectLabel} | SiaMentor"
  Пример: "Что такое производная — ЕГЭ Математика | SiaMentor"
  Максимум: 60 символов до " | SiaMentor"

<meta name="description">: первые 155 символов из summary поля
  Содержит: ключевое слово + ЕГЭ + название предмета
  Пример: "Производная — математический инструмент для измерения скорости изменения функции. Встречается в заданиях 7, 11, 18 ЕГЭ профильной математики."

canonical: https://siamentor.com/ru/ege/{subject}/{slug}
alternates.languages.ru: /ru/ege/{subject}/{slug}
og:title: {concept.title}
og:description: первые 155 символов summary
```

### Section 1: Summary Block

```
Component: SummarySection (Server Component)
Position: Сразу под H1, первый контентный блок

Содержимое:
  - H1 (тег): "{concept.h1}" — keyword-first формулировка
    Пример h1: "Производная: что это такое и как используется на ЕГЭ"
  - Параграф-определение: 200–300 слов уникального объяснения
    Структура параграфа:
      1. Первое предложение = прямой ответ на запрос (ключевое слово в первых 10 словах)
      2. Объяснение концепта своими словами (не Википедия)
      3. Где встречается на ЕГЭ (номера заданий)
      4. Типичные ошибки студентов
      5. Одно конкретное примечание "как запомнить"
  - Тег <time datetime="{lastUpdated}"> — дата обновления (сигнал freshness)

SEO rules:
  - Ключевое слово ("что такое производная ЕГЭ") в первом предложении
  - НЕ копировать определение из учебника или Википедии
  - Минимум 200 слов (thin content protection)
  - Разговорный стиль (студент объясняет студенту)
```

### Section 2: Concept Table

```
Component: ConceptTable (Server Component)
Position: После Summary, перед FAQ

Структура таблицы:
  Колонки: | Понятие | Определение | Пример на ЕГЭ |
  Строк: минимум 3, максимум 6
  Каждая строка = отдельный связанный термин или аспект концепта

Требования к данным (поле tableRows в JSON):
  term: string          — название термина/аспекта (1–4 слова)
  definition: string    — краткое определение (20–40 слов)
  egeContext: string    — где и как встречается ("Задание 7, B-уровень" или "Задания 11–12")

Пример для "производная":
  | Производная f'(x) | Предел отношения прироста функции к приросту аргумента | Задание 7, базовый уровень |
  | Дифференцирование | Процесс нахождения производной по правилам | Задание 11, профильный |
  | Касательная к графику | Прямая, касающаяся кривой в одной точке (угол = производная) | Задание 18, профильный |
  | Производная суммы | (f+g)' = f' + g' | Все задания с производными |

HTML: стандартная <table> с <thead> и <tbody>, Tailwind классы для стилизации
JSON-LD: НЕ добавлять schema для таблицы (только для FAQ)
```

### Section 3: FAQ Block

```
Component: FAQSection (Server Component)
Position: После ConceptTable, перед CTA

Количество вопросов: минимум 3, максимум 5
Формат: <details>/<summary> (нативный HTML, без JS) + JSON-LD FAQPage schema

Требования к вопросам:
  - Каждый вопрос специфичен для данного концепта (не общие вопросы про ЕГЭ)
  - Вопросы начинаются с: "Как...", "Что такое...", "Почему...", "Какие...", "Где..."
  - Вопросы = реальные запросы студентов (long-tail pattern)
  - Ответ: 50–100 слов, конкретный, практичный

Требования к ответам:
  - Прямой ответ в первом предложении
  - Конкретные примеры (числа, номера заданий)
  - НЕ отсылать на другие страницы в ответе (самодостаточность)

JSON-LD структура:
  {
    "@context": "https://schema.org",
    "@type": "FAQPage",
    "mainEntity": [
      {
        "@type": "Question",
        "name": "{question}",
        "acceptedAnswer": { "@type": "Answer", "text": "{answer}" }
      }
    ]
  }

Примеры вопросов для "производная":
  Q: "Как найти производную функции на ЕГЭ?"
  Q: "Какие формулы производных обязательно знать для ЕГЭ?"
  Q: "На каком задании ЕГЭ встречается производная?"
  Q: "Почему производная называется производной?"
  Q: "Как производная связана с касательной к графику?"
```

### Section 4: CTA Block

```
Component: CTASection ('use client' — единственный клиентский компонент)
Position: Последний блок на странице (sticky на мобайл опционально)

Содержимое:
  Заголовок: "Хочешь разобраться с {concept.subjectLabel} перед ЕГЭ?"
    Пример: "Хочешь разобраться с математикой перед ЕГЭ?"
  Подзаголовок: "SiaMentor объяснит непонятное прямо в тексте — задай вопрос AI прямо сейчас"
  Кнопка: "Начать бесплатно →"
    href: "/ru/auth/register?source=seo&subject={subject}&concept={slug}"
  Мелкий текст: "Бесплатно · Без карты · Результат с первого урока"

PostHog tracking (в onClick кнопки):
  posthog.capture('seo_cta_click', {
    concept_slug: '{slug}',
    subject: '{subject}',
    source_page: '/ru/ege/{subject}/{slug}'
  })

Визуальное оформление:
  - Фон: gradient от bg-blue-50 до bg-indigo-50
  - Граница сверху: border-t border-blue-100
  - Padding: py-12 px-6
  - Кнопка: bg-indigo-600 text-white px-8 py-3 rounded-lg hover:bg-indigo-700
```

### Section 5: Internal Links

```
Component: RelatedConcepts (Server Component)
Position: Между FAQ и CTA

Структура:
  Заголовок: "Связанные темы по {subjectLabel}"
  Список: 3–5 ссылок на соседние концепты из relatedSlugs массива
  Формат: <ul> с <li><a href="/ru/ege/{subject}/{relSlug}">{relTitle}</a></li>

Зачем: передаёт PageRank между страницами, сигнал тематической экспертизы

Breadcrumbs (в <header> страницы):
  ЕГЭ → {SubjectLabel} → {ConceptTitle}
  Ссылки: /ru/ege/ → /ru/ege/{subject}/ → (текущая)
```

---

## Pilot Page List (45 Pages)

### Subject: matematika (25 pages)

| # | H1 | URL slug | Query type |
|---|----|----------|------------|
| 1 | Производная: что это и как используется на ЕГЭ | chto-takoe-proizvodnaya-ege | что такое |
| 2 | Интеграл: определение и применение на ЕГЭ | chto-takoe-integral-ege | что такое |
| 3 | Как решать логарифмы на ЕГЭ | kak-reshat-logarifmy-ege | как решать |
| 4 | Арифметическая прогрессия: формулы и задания ЕГЭ | arifmeticheskaya-progressiya-ege | определение + формула |
| 5 | Геометрическая прогрессия: формулы и задания ЕГЭ | geometricheskaya-progressiya-ege | определение + формула |
| 6 | Синус и косинус: формулы для ЕГЭ | sinus-kosinus-formuly-ege | формулы |
| 7 | Тангенс и котангенс: формулы и задания ЕГЭ | tangens-kotangens-ege | формулы |
| 8 | Как решать тригонометрические уравнения на ЕГЭ | trigonometricheskie-uravneniya-ege | как решать |
| 9 | Квадратные уравнения: формулы и дискриминант ЕГЭ | kvadratnye-uravneniya-ege | формулы + дискриминант |
| 10 | Системы уравнений: методы решения на ЕГЭ | sistemy-uravneniy-ege | методы решения |
| 11 | Как решать неравенства на ЕГЭ | neravenstva-ege | как решать |
| 12 | Теория вероятностей: основы и задачи ЕГЭ | veroyatnost-teoriya-ege | теория + задачи |
| 13 | Комбинаторика: перестановки и сочетания ЕГЭ | kombinatorika-ege | определение |
| 14 | Что такое функция: область значений и определения ЕГЭ | chto-takoe-funktsiya-ege | что такое |
| 15 | Степени и корни: правила и формулы ЕГЭ | stepeni-i-korni-ege | правила + формулы |
| 16 | Логарифмические уравнения: методы решения ЕГЭ | logarifmicheskie-uravneniya-ege | методы |
| 17 | Показательные уравнения: методы решения ЕГЭ | pokazatelnye-uravneniya-ege | методы |
| 18 | Формулы площадей фигур: таблица для ЕГЭ | ploshchadi-figur-ege | таблица формул |
| 19 | Формулы объёмов фигур: таблица для ЕГЭ | obemy-figur-ege | таблица формул |
| 20 | Теорема Пифагора: применение на ЕГЭ | teorema-pifagora-ege | применение |
| 21 | Касательная к графику функции на ЕГЭ | kasatelnaya-k-grafiku-ege | производная + применение |
| 22 | Статистика: среднее, медиана и мода в ЕГЭ | statistika-sredneye-mediana-ege | определение + задачи |
| 23 | Планиметрия: типы задач на ЕГЭ | zadachi-planimetriya-ege | типы задач |
| 24 | Стереометрия: типы задач на ЕГЭ | zadachi-stereometriya-ege | типы задач |
| 25 | Натуральные, целые и рациональные числа: ЕГЭ | naturalnye-tselye-ratsionalnye-chisla-ege | систематизация |

### Subject: russkiy (20 pages)

| # | H1 | URL slug | Query type |
|---|----|----------|------------|
| 1 | Что такое причастие: правила и ЕГЭ | chto-takoe-prichastie-ege | что такое |
| 2 | Что такое деепричастие: правила и ЕГЭ | chto-takoe-deeprichastie-ege | что такое |
| 3 | Обособленные определения: запятые на ЕГЭ | obosoblennye-opredeleniya-ege | правила |
| 4 | Однородные члены предложения: запятые ЕГЭ | odnorodnye-chleny-predlozheniya-ege | запятые |
| 5 | Сложносочинённое предложение: запятые ЕГЭ | slozhnosochinennoe-predlozhenie-ege | запятые |
| 6 | Придаточное предложение: виды и запятые ЕГЭ | pridatochnoe-predlozhenie-ege | виды + запятые |
| 7 | НЕ с разными частями речи: правила ЕГЭ | ne-s-razlichnymi-chastyami-rechi-ege | правила |
| 8 | Н и НН в прилагательных: правила ЕГЭ | n-i-nn-v-prilagatelnykh-ege | правила |
| 9 | Н и НН в причастиях: правила ЕГЭ | n-i-nn-v-prichastiyakh-ege | правила |
| 10 | Безударные гласные в корне: чередования ЕГЭ | bezudarnye-glasnye-v-korne-ege | чередования |
| 11 | Правописание приставок на з/с и пре/при ЕГЭ | pravopisanie-pristavok-ege | правила |
| 12 | Паронимы: частые ошибки на ЕГЭ | paronimy-ege | частые ошибки |
| 13 | Синтаксические нормы: согласование на ЕГЭ | sintaksicheskie-normy-ege | согласование |
| 14 | Морфологические нормы: падежи на ЕГЭ | morfologicheskie-normy-ege | падежные ошибки |
| 15 | Типы речи: описание, повествование, рассуждение ЕГЭ | opisanie-povestvovanie-rassuzhdenie-ege | определение + примеры |
| 16 | Изобразительные средства: метафора, эпитет, сравнение ЕГЭ | metafora-epithet-sravnenie-ege | таблица |
| 17 | Как определить позицию автора в тексте ЕГЭ | kak-opredelit-pozitsiyu-avtora-ege | алгоритм |
| 18 | Структура сочинения ЕГЭ: план и шаблон | struktura-sochineniya-ege | план |
| 19 | Запятая в сложном предложении: правила ЕГЭ | zapyataya-v-slozhnom-predlozhenii-ege | правила |
| 20 | Двоеточие и тире: правила постановки ЕГЭ | dvoetochie-i-tire-ege | правила |

### Hub Pages (3 pages)

| URL | Назначение | Контент |
|-----|------------|---------|
| /ru/ege/ | Главный каталог ЕГЭ | Список предметов + краткое intro (200 слов) |
| /ru/ege/matematika/ | Каталог математики | Список всех 25 тем с описаниями |
| /ru/ege/russkiy/ | Каталог русского языка | Список всех 20 тем с описаниями |

---

## JSON Data Structure

```typescript
// apps/web/src/lib/seo-data/types.ts

export interface SeoConcept {
  slug: string            // "chto-takoe-proizvodnaya-ege"
  subject: "matematika" | "russkiy" | "fizika"
  subjectLabel: string    // "Математика"
  title: string           // для <title> тега: "Что такое производная — ЕГЭ Математика | SiaMentor"
  h1: string              // "Производная: что это такое и как используется на ЕГЭ"
  summary: string         // 200–300 слов уникального определения (plain text)
  tableRows: ConceptTableRow[]  // минимум 3, максимум 6
  faqs: FAQ[]                   // минимум 3, максимум 5
  relatedSlugs: string[]        // 3–5 слагов из того же предмета
  lastUpdated: string           // ISO 8601: "2026-05-04"
}

export interface ConceptTableRow {
  term: string           // 1–4 слова
  definition: string     // 20–40 слов
  egeContext: string     // "Задание 7, базовый уровень"
}

export interface FAQ {
  question: string       // вопрос студента, начинается с "Как"/"Что"/"Почему"/"Какие"
  answer: string         // 50–100 слов, прямой ответ
}

// Функции доступа к данным
// apps/web/src/lib/seo-data/index.ts
export async function getAllConcepts(): Promise<SeoConcept[]>
export async function getConcept(subject: string, slug: string): Promise<SeoConcept | null>
export async function getConceptsBySubject(subject: string): Promise<SeoConcept[]>
```

Пример JSON записи для "производная":

```json
{
  "slug": "chto-takoe-proizvodnaya-ege",
  "subject": "matematika",
  "subjectLabel": "Математика",
  "title": "Что такое производная — ЕГЭ Математика | SiaMentor",
  "h1": "Производная: что это такое и как используется на ЕГЭ",
  "summary": "Производная — это математический инструмент, который показывает насколько быстро изменяется функция в данной точке. Если функция описывает положение машины во времени, производная покажет её скорость в конкретный момент. На ЕГЭ по профильной математике производная встречается в трёх типах заданий: задание 7 (базовый уровень, нужно найти производную по формуле), задание 11 (применение в задачах на движение и оптимизацию) и задание 18 (геометрический смысл — касательная к графику). Самая частая ошибка — путать производную функции f(x) с самой функцией: f'(x) ≠ f(x). Производная y=x² равна y'=2x, а не x². Чтобы запомнить: производная показывает 'наклон' графика в каждой точке — если функция растёт, производная положительна.",
  "tableRows": [
    { "term": "Производная f'(x)", "definition": "Предел отношения прироста функции к приросту аргумента при стремлении аргумента к нулю", "egeContext": "Задание 7, базовый уровень" },
    { "term": "Дифференцирование", "definition": "Процесс нахождения производной по таблице производных и правилам дифференцирования", "egeContext": "Задание 11, профильный" },
    { "term": "Касательная к графику", "definition": "Прямая, касающаяся кривой в одной точке; угол наклона касательной равен значению производной в этой точке", "egeContext": "Задание 18, профильный" }
  ],
  "faqs": [
    { "question": "Как найти производную функции на ЕГЭ?", "answer": "По таблице производных: (x^n)' = n·x^(n-1), (sin x)' = cos x, (e^x)' = e^x, (ln x)' = 1/x. Для сложных функций применяй правила: (f+g)' = f'+g', (fg)' = f'g+fg', (f/g)' = (f'g-fg')/g². Выучи таблицу наизусть — на ЕГЭ калькулятор не помогает." },
    { "question": "На каком задании ЕГЭ встречается производная?", "answer": "В трёх заданиях: №7 (базовый — просто найти производную), №11 (применение к задачам на скорость и оптимизацию) и №18 (профильный — геометрический смысл и уравнение касательной). Задание 18 — одно из самых сложных, стоит 4 балла." }
  ],
  "relatedSlugs": ["chto-takoe-integral-ege", "kasatelnaya-k-grafiku-ege", "chto-takoe-funktsiya-ege"],
  "lastUpdated": "2026-05-04"
}
```

---

## Next.js Technical Roadmap

### File Structure to Create

```
apps/web/src/
├── app/
│   ├── [locale]/
│   │   └── ege/
│   │       ├── page.tsx                      # Hub: /ru/ege/
│   │       └── [subject]/
│   │           ├── page.tsx                  # Hub: /ru/ege/matematika/
│   │           └── [slug]/
│   │               └── page.tsx              # Leaf: /ru/ege/matematika/chto-takoe-...
│   ├── sitemap.ts                             # Генерирует sitemap.xml для всех SEO страниц
│   └── robots.ts                             # Allow: /ru/ege/
├── lib/
│   └── seo-data/
│       ├── types.ts                          # SeoConcept, ConceptTableRow, FAQ interfaces
│       ├── index.ts                          # getAllConcepts, getConcept, getConceptsBySubject
│       ├── matematika-concepts.json          # 25 концептов математики
│       └── russkiy-concepts.json             # 20 концептов русского языка
└── components/
    └── seo/
        ├── SummarySection.tsx                # Server Component
        ├── ConceptTable.tsx                  # Server Component
        ├── FAQSection.tsx                    # Server Component + JSON-LD
        ├── CTASection.tsx                    # 'use client' — PostHog tracking
        └── RelatedConcepts.tsx              # Server Component
```

### Key Code Patterns

Pattern 1 — generateStaticParams:

```typescript
// apps/web/src/app/[locale]/ege/[subject]/[slug]/page.tsx
export async function generateStaticParams() {
  const concepts = await getAllConcepts()
  const locales = ['ru', 'en']
  return locales.flatMap((locale) =>
    concepts.map((c) => ({ locale, subject: c.subject, slug: c.slug }))
  )
}
```

Pattern 2 — generateMetadata:

```typescript
export async function generateMetadata({ params }: Props): Promise<Metadata> {
  const { subject, slug } = await params
  const concept = await getConcept(subject, slug)
  if (!concept) return { title: 'Не найдено' }
  return {
    title: concept.title,  // уже содержит "| SiaMentor"
    description: concept.summary.slice(0, 155),
    alternates: {
      canonical: `https://siamentor.com/ru/ege/${subject}/${slug}`,
      languages: { ru: `/ru/ege/${subject}/${slug}` },
    },
    openGraph: {
      title: concept.h1,
      description: concept.summary.slice(0, 155),
    },
  }
}
```

Pattern 3 — sitemap.ts:

```typescript
// apps/web/src/app/sitemap.ts (добавить к существующему или создать)
import { getAllConcepts } from '@/lib/seo-data'
const BASE = 'https://siamentor.com'

const seoConcepts = (await getAllConcepts()).map((c) => ({
  url: `${BASE}/ru/ege/${c.subject}/${c.slug}`,
  lastModified: new Date(c.lastUpdated),
  changeFrequency: 'monthly' as const,
  priority: 0.7,
}))
// Merge с существующими маршрутами приложения
```

### Deployment Steps

```
1. Создать JSON data files (45 концептов вручную или через AI)
   Время: ~2–3 часа для ручного написания качественного контента
   Критерий: каждый концепт имеет summary ≥200 слов, ≥3 tableRows, ≥3 FAQs

2. Создать lib/seo-data/ (types.ts + index.ts)
   Время: ~30 минут (чистый TypeScript)

3. Создать компоненты seo/ (5 компонентов)
   Время: ~2 часа

4. Создать page.tsx routes (leaf + hub)
   Время: ~1 час

5. Обновить sitemap.ts и robots.ts
   Время: ~30 минут

6. Локальная проверка:
   - pnpm dev → открыть http://localhost:4000/ru/ege/matematika/chto-takoe-proizvodnaya-ege
   - pnpm build → убедиться что standalone build работает
   - Проверить view-source что контент есть в HTML (не client-side)

7. Deploy на Railway (стандартный процесс)
   - Убедиться что NEXT_PUBLIC_APP_URL=https://siamentor.com в env vars

8. После деплоя (день 0):
   - Google Search Console → Add property → submit sitemap.xml
   - Яндекс Вебмастер → добавить сайт → submit sitemap

9. Мониторинг (PostHog уже настроен):
   Событие: seo_cta_click — трекает клики на CTA кнопку
```

---

## Success Metrics

Пилот считается успешным если через 60 дней выполнены ≥2 из 3 условий:

| Метрика | Цель | Инструмент |
|---------|------|------------|
| Organic impressions | >1,000/месяц | Google Search Console |
| Organic clicks | >200/месяц | Google Search Console |
| Средняя позиция по целевым запросам | <30 (входим в ТОП-30) | Google Search Console |
| CTA conversion rate | >2% от посетителей | PostHog (событие seo_cta_click) |

Negative signals (pivot triggers):
  - 0 impressions через 30 дней → проверить sitemap.xml, robots.txt, canonical URL
  - Impressions >100 но CTR <0.5% → переписать title и meta description
  - CTR хороший но 0 регистраций → переработать CTA текст и кнопку

Timeline:
  День 0: деплой + submit sitemap
  День 7–14: первые страницы проиндексированы (site:siamentor.com/ru/ege/)
  День 30: промежуточная проверка — есть ли impressions
  День 60: итоговая оценка — решение масштабировать до 200 страниц или пивот

---

## Content Quality Rules

Правило 1 — Scaled Content Abuse Protection:
  Каждая страница должна содержать реально РАЗНЫЙ контент:
  - summary: уникальное объяснение, НЕ шаблонный текст с заменой одного слова
  - tableRows: разные строки, специфичные для данного концепта
  - faqs: вопросы специфичные для концепта (не "что такое ЕГЭ?" на каждой странице)
  Проверка: если заменить название концепта на другое — текст должен стать бессмысленным

Правило 2 — Minimum Content Threshold:
  - summary: минимум 200 слов
  - tableRows: минимум 3 строки
  - faqs: минимум 3 вопроса
  - Итого на странице: минимум 500 слов уникального контента

Правило 3 — Freshness Signal:
  - lastUpdated в JSON: обновлять при изменении контента
  - <time datetime="{lastUpdated}"> в SummarySection

Правило 4 — Mobile-First:
  - Таблица: горизонтальный скролл на мобайл (overflow-x-auto)
  - CTA: достаточный tap target (минимум 44px высота кнопки)
  - FAQ <details>: нативный HTML, не требует JS
