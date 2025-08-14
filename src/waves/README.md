
---

## `src/waves/README.md`
```markdown
# WAVES — волны/циклы (долгие интервалы)

Автономный домен: сходство с историческими паттернами и их исходами.

## Функции
- Фичи: свинги, фрактальные признаки, multi‑TF компрессия.
- Сходство: DTW/shape‑similarity, top‑аналоги с датами.
- Оценка: вероятность паттерна, когда работал/ломался.

## Подпакеты
`features/`, `similarity/`, `analogs/`, `backtests/`.

## Выход
```json
{
  "domain":"WAVES","version":"1.0.0","as_of":"2025-08-14T07:30:00+03:00",
  "scores":[{"ticker":"AAPL","score":0.31,"confidence":0.60,
             "features":{"best_match":"AAPL_2019-10..2020-02","similarity":0.73},
             "analogs":[{"ticker":"AAPL","period":"2019-10/2020-02","outcome":"up"}]}],
  "explanations":[{"ticker":"AAPL","bullets":["Similar to 2019Q4","Historically bullish"]}]
}
