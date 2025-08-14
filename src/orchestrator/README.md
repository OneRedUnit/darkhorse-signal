# Orchestrator — сборка финального отчёта

Оркестратор агрегирует выходы модулей, применяет Fusion/калибровку и формирует
pre/post‑market отчёты (Markdown/HTML/JSON).

## Функции
- Загрузка промежуточных артефактов модулей (`artifacts/intermediate/*.json`)
- Временная выравнивание по `as_of` и `timezone=Europe/Riga`
- Fusion: взвешивание доменных `score` + калибровка `confidence`
- Фильтрация по порогам (buy/sell/watch)
- Генерация артефактов: `artifacts/premarket_*.{md,html,json}`, `postmarket_*`
- Деградация: пересчёт весов при отсутствии части модулей

## Вход
- `config/config.yaml` (fusion/thresholds/universe/scheduling)
- JSON‑выходы модулей (см. их README)

## Выход
```json
{
  "date": "2025-08-14",
  "timezone": "Europe/Riga",
  "top": {"buy":["AAPL"],"sell":["TSLA"],"watch":["MSFT"]},
  "recommendations": [
    {
      "ticker":"AAPL",
      "score":0.71,
      "confidence":0.79,
      "drivers":["news_sentiment","tech_leaders"],
      "bullets":["Positive flow","Breakout above MA"],
      "levels":{"entry":214,"stop":208,"tp":221}
    }
  ],
  "regime":{"label":"bull","p":0.64}
}
