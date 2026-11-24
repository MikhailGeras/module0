# Запуск: 
0. git clone https://github.com/MikhailGeras/module0.git
1. файл olist_delivery_clean.csv поместить в директорию "data/"
2. cd module0
3. uv sync
4. uv run jupyter lab
5. В jupyter lab открыть ДЗ0.ipynb и выбрать Run -> Run All Sells

## ДЗ3: метрики, порог и калибровка

### Постановка

Предсказываю опоздание заказа. Сравниваю модель
HistGradientBoostingClassifier с обычными и сбалансированными весами
классов, выбираю порог и исследую калибровку.

### Как запустить

1. Получить `olist_delivery_clean.csv` из материалов и положить в `data/`.
2. Выполнить `uv sync --locked`.
3. Открыть `ДЗ3.ipynb`, выбрать Python из `.venv` и запустить все ячейки.

### Результаты

- ROC-AUC модели A: 0.7235.
- Average Precision модели A: 0.2125.
- При пороге с ограничением модель A отметила на test примерно 10% заказов;
  precision — 0.2514, recall — 0.3099.
- У модели B после калибровки Платта Brier score снизился
  с 0.1925 до 0.0700.

### Решения

Данные разделены на train, validation и test в пропорции 60/20/20
со стратификацией и `random_state=42`. Пороги и калибровку выбираю
на validation, итоговые метрики показываю на test. CSV в Git не хранится.