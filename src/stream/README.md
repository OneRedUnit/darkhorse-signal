
---

## `src/stream/README.md`
```markdown
# STREAM — реальное время

Инжест real‑time ленты, всплески, аномалии, краткоживущие сигналы (TTL).

## Функции
- Источники: тики/лента/новостные вспышки.
- События: объём/импульс/имбэланс → детекторы.
- Агрегаты: 1м/5м окна, стабилизация шума.
- Алерты: вебхуки (Telegram/Slack), TTL‑сигналы.

## Подпакеты
`sources/`, `events/`, `aggregates/`, `alerting/`.

## Выход
```json
{
  "domain":"STREAM","version":"1.0.0","as_of":"2025-08-14T07:30:00+03:00",
  "scores":[{"ticker":"AAPL","score":0.22,"confidence":0.58,"ttl_sec":900,
             "features":{"volume_spike":2.1,"imbalance":0.35}}],
  "explanations":[{"ticker":"AAPL","bullets":["1m volume spike","Tape imbalance"]}]
}
