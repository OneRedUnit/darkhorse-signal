# NEXUS — центральный аналитик/оркестратор

Сводит домены (PULSE/PATTERN/VOICE/WAVES/STREAM) в финальные pre/post‑market отчёты.

## Назначение
- Сбор выходов доменов → выравнивание по `as_of`.
- Fusion: веса, калибровка уверенности, учёт рыночного режима/риска.
- Пост‑процесс: фильтры порогов, формирование списков Buy/Sell/Watch.
- Генерация артефактов: `artifacts/premarket_*` и `postmarket_*` (md/html/json).

## Подпакеты
- `fusion/` — взвешивание, изотоническая калибровка.
- `reporting/` — формат отчёта, markdown + json‑summary.
- `scheduler/` — pre/post прогоны, Cron/Actions интеграция.
- `contracts/` — JSON‑схема итогового отчёта.

## Вход
- `artifacts/intermediate/<domain>_<run_id>.json` от доменов.
- `config/config.yaml` (weights/thresholds/timezone).

## Выход (пример)
```json
{
  "date":"2025-08-14",
  "timezone":"Europe/Riga",
  "top":{"buy":["AAPL"],"sell":["TSLA"],"watch":["MSFT"]},
  "recommendations":[
    {"ticker":"AAPL","score":0.71,"confidence":0.79,"drivers":["PULSE","PATTERN"],
     "bullets":["Positive news density","Breakout confirmation"],
     "levels":{"entry":214,"stop":208,"tp":221}}
  ],
  "regime":{"label":"bull","p":0.64}
}
