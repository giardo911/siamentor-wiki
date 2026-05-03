# Done: Запланировать Phase 4 (Image Generation Pipeline): выписать 5 планов 04-01..04-05 и оценить время

**Date:** 2026-05-03
**Source:** management/project-checklist.md (section: 2026-04-28)
**GSD Phase:** 999.3

## Summary

Phase 4 (Image Generation Pipeline) полностью реализована до момента анализа. Все 5 планов выполнены: 04-01 (TDD-заглушки, ~2 мин), 04-02 (модель + конфиг, ~3 мин), 04-03 (WaveSpeedClient, 8 мин), 04-04 (IllustrationService + async, 7 мин), 04-05 (handler + route, 8 мин). Суммарное машинное время ~28 минут. Верификация: 4/5 must-haves автоматически; 3 пункта — ручная проверка в prod (живой WaveSpeed API + Railway Volume). Ключевые решения: горутина с context.Background() + 90s таймаут, атомарная запись CreateTemp→Rename, defer recover() для гарантии перехода в статус failed. Задача из чеклиста 2026-04-28 закрывается ретроспективно: Phase 4 спроектирована с нуля, выполнена и верифицирована за 1 рабочий день (2026-04-19).

## Deliverable

### Декомпозиция планов Phase 4

| # | Название плана | Wave | Описание | Факт. время |
|---|----------------|------|----------|-------------|
| 04-01 | Wave 0: TDD Stubs | 0 | Заглушки тестов для models, handlers, services — намеренные RED-gate | ~2 мин |
| 04-02 | Wave 1: Model + Config | 1 | `LessonIllustration` struct, AutoMigrate, конфиг-поля WaveSpeed | ~3 мин |
| 04-03 | Wave 1: WaveSpeedClient | 1 | HTTP-клиент submit+poll (2s ticker, 90s бюджет), интерфейс | **8 мин** |
| 04-04 | Wave 2: IllustrationService | 2 | Async-горутина, атомарная запись, startup cleanup | **7 мин** |
| 04-05 | Wave 3: Handler + Route | 3 | GenerateIllustration handler, enum-валидация, POST route | **8 мин** |

**Итого:** ~28 мин машинного времени. Phase 4 завершена 2026-04-19.

### Статус верификации

- **4/5 must-haves** — подтверждены программно
- **3 пункта** требуют ручной проверки при первом prod-деплое:
  1. POST + ожидание 90s → строка в БД `status=ready`, PNG на Railway Volume
  2. WaveSpeed недоступен → `status=failed`, нет зависших горутин
  3. Рестарт backend с `.tmp` файлами >1h → файлы удалены

### Зависимости в milestone

Phase 3 → **Phase 4** → Phase 5 (Image Serving, выполнена) → Phase 6 (Frontend, выполнена) → Phase 7 (n8n, не начата)

## Links

- GSD Phase: `.planning/phases/999.3-plan-phase-4-image-generation-pipeline/`
- Analysis document: `.planning/phases/999.3-plan-phase-4-image-generation-pipeline/999.3-ANALYSIS.md`
- Original Phase 4: `.planning/phases/04-image-generation-pipeline/`
