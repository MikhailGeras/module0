# Запуск: 
0. git clone https://github.com/MikhailGeras/module0.git
1. файл olist_delivery_clean.csv поместить в директорию "data/"
2. cd module0
3. uv sync
4. uv run jupyter lab
5. В jupyter lab открыть ДЗ0.ipynb и выбрать Run -> Run All Sells

## ДЗ 2: поиск утечек

### Постановка

Предсказываем late_delivery в момент оформления заказа.
Нужно найти три утечки и сравнить ROC-AUC до и после их удаления.

Модель: HistGradientBoostingClassifier(random_state=42), остальные
параметры по умолчанию. Один stratified split 75/25 с random_state=42.

### Как запустить

1. Переключиться на ветку hw-02-leakage.
2. Выполнить uv sync --locked.
3. Взять olist_delivery_export.csv из материалов.
4. Положить файл в data/olist_delivery_export.csv.
5. Открыть HW2.ipynb в VS Code и выбрать Python из .venv.
6. Перезапустить ядро и выполнить Run All.

CSV в Git не хранится. Это учебная выгрузка;
olist_delivery_clean.csv и исходные файлы Kaggle её не заменяют.

### Результаты

| Вариант | ROC-AUC |
|---|---:|
| Исходная выгрузка | 0.911819 |
| Без handover_lag_days | 0.892328 |
| Без record_id | 0.822342 |
| Без seller_score | 0.897640 |
| Без всех трёх | 0.726764 |

### Решения

Удалены фактическое событие после оформления, технический номер
с зависимым от исхода диапазоном и агрегат таргета по всей выгрузке.

Категории переведены в category. Пропуски сохранены:
модель обрабатывает их самостоятельно. Новые признаки и подбор
гиперпараметров не использовались.
