
---

## `src/pattern/README.md`
```markdown
# PATTERN — теханализ рынков и акций

Автономный домен: индикаторы, сканеры лидеров, уровни, риск и режим.

## Функции
- Индикаторы: MA/EMA/RSI/ADX/ATR/breadth/вола‑кластеры.
- Сканеры: 52W‑high, пробои баз, объёмные всплески, гэпы.
- Leaders: относительная сила и устойчивость тренда.
- Levels: entry/stop/tp + R/R.
- Regimes: определение режима (bull/bear/range/rotation).
- Risk: вола/кредит/опционы → лимиты позиции (если источники подключены).

## Подпакеты
`indicators/`, `scanners/`, `leaders/`, `levels/`, `regimes/`, `risk/`.

## Выход
```json
{
  "domain":"PATTERN","version":"1.0.0","as_of":"2025-08-14T07:30:00+03:00",
  "scores":[{"ticker":"AAPL","score":0.68,"confidence":0.75,
             "features":{"rs":0.82,"breakout":true,"volume_spike":1.5},
             "levels":{"entry":214,"stop":208,"tp":221}}],
  "explanations":[{"ticker":"AAPL","bullets":["Breakout + RS high","Volume confirmation"]}],
  "regime":{"label":"bull","p":0.61},
  "risk":{"ticker":"AAPL","max_risk_pct":0.6}
}
