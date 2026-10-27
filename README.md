# Домашние задания по ML

- `ДЗ0.ipynb` — постановка задачи и baseline.
- `ДЗ1.ipynb` — сравнение KFold, GroupKFold и TimeSeriesSplit для KNN.

## Данные

Используется подготовленный файл `olist_delivery_clean.csv`, полученный от наставника в материалах курса. Его нужно поместить в папку `data/` в корне проекта.

## Запуск ДЗ1

Необходимо установить Git и uv.

Клонировать репозиторий, перейти в ветку задания и установить зависимости:

```powershell
git clone https://github.com/MikhailGeras/module0.git
cd module0
git switch hw-01-validation
uv sync
```

Создать папку `data/`, если её нет, и поместить туда `olist_delivery_clean.csv`.

Открыть папку проекта в VS Code, затем открыть `ДЗ1.ipynb`. Выбрать ядро Python из окружения `.venv`, перезапустить ядро и выполнить все ячейки сверху вниз.

Также ноутбук можно открыть через JupyterLab:

```powershell
uv run jupyter lab
```