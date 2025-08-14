
---

## `src/voice/README.md`
```markdown
# VOICE — анализ анализов (мета‑аналитика)

Автономный домен: ап/даунгрейды, таргеты, сила консенсуса, свежесть.

## Функции
- Нормализация рейтингов (Buy/Hold/Sell → [-1..1]).
- Таргеты: `tp_delta` к spot, устойчивость по времени.
- Консенсус: дисперсия, согласованность.
- Дедуп/анти‑спам заметок.

## Подпакеты
`brokers/`, `ratings/`, `consensus/`, `dedup/`.

## Выход
```json
{
  "domain":"VOICE","version":"1.0.0","as_of":"2025-08-14T07:30:00+03:00",
  "scores":[{"ticker":"AAPL","score":0.44,"confidence":0.70,
             "features":{"upgrades":3,"tp_delta":0.05}}],
  "explanations":[{"ticker":"AAPL","bullets":["Multiple upgrades","TP raised +5%"]}]
}
