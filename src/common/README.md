
---

## `src/common/README.md`
```markdown
# COMMON — утилиты и контракты

Общее для всех доменов: I/O, схемы, скоринг/калибровка, форматтеры.

## Состав
- `io/` — чтение/запись JSON/Parquet, снапшоты, `run_id`.
- `schema/` — JSON‑схемы доменов и итогового отчёта.
- `scoring/` — нормализация/калибровка/взвешивание.
- `formatters/` — markdown/html/json.
- `time/` — Europe/Riga TZ, округления.

## Единый каркас сообщения
```json
{
  "as_of":"2025-08-14T07:30:00+03:00",
  "domain":"<PULSE|PATTERN|VOICE|WAVES|STREAM|NEXUS>",
  "universe":["AAPL","MSFT"],
  "run_id":"<uuid>",
  "data_snapshot":"s3://bucket/dt=2025-08-14",
  "payload":{}
}
