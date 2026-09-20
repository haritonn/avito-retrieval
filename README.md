# Avito Retrieval

Решение задачи поиска релевантных объявлений в рамках тестового задания на Avito Data Science Bootcamp 2026. Итоговая метрика: `Recall@50 = 0.654475`.

## Подход

```text
BM25 по заголовку и параметрам
+ BM25 по описанию
+ multilingual E5 по короткому запросу
+ multilingual E5 по запросу с параметрами
+ подбор четырёх весов RRF через Optuna
+ бонусы за совпадение локации и заголовка
+ top-50 объявлений
+ answer.csv
```

## Запуск

Положить [данные](https://disk.yandex.ru/d/sNhfo0YOjGtufg) в `dataset/`:

```text
dataset/train.parquet
dataset/benchmark_queries.parquet
dataset/benchmark_items.parquet
```

Установить зависимости и открыть notebook:

```bash
git clone https://github.com/haritonn/avito_retrieval ./ && cd avito_retrieval
uv sync
uv run jupyter lab
```

В `avito.ipynb` выполнить **Restart Kernel → Run All**.

Тяжёлые результаты BM25, E5 и FAISS сохраняются в `artifacts/` и загружаются повторно при следующем запуске. Итоговый submission записывается в `answer.csv` с колонками `query_id,answer`.



