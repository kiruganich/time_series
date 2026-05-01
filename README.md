# Lab 2 - Training a model to predict weather conditions a week in advance

## Реализован полный ML‑пайплайн:

Excel → очистка → EDA → feature engineering → обучение моделей → сравнение стратегий → анализ остатков

## Dataset
- Файл: weather_data.xlsx
- Формат: Excel с несколькими листами
- 6 городов
- Дневная частота
- Период: 2020–2025
- Целевая переменная: temperature_2m

## Основные этапы

### 1. Загрузка данных
- чтение всех листов через openpyxl
- отбор только листов с temperature_2m
- объединение в единый датафрейм

### 2. Очистка данных
- исправление кодировки
- устранение опечаток в названиях городов
- удаление пустых строк
- ресемплинг к дневной частоте
- удаление выбросов (IQR)
- интерполяция пропусков

### 3. EDA
- визуализация временных рядов
- сезонная декомпозиция
- тест Дики–Фуллера
- ACF / PACF

### 4. Feature Engineering
- лаги температуры (1–14, 365)
- лаги погодных параметров
- rolling‑статистики (7 и 30 дней)
- Fourier‑признаки сезонности
- признаки взаимодействия
- One‑Hot Encoding города
- генерация target_h1 … target_h7

### 5. Обучение моделей
- Decision Tree
- Random Forest
- LightGBM (с Optuna)
- Direct стратегия
- Recursive стратегия
- Naive baseline

### 6. Оценка качества
- MAE
- RMSE
- WAPE
- MAPE
- Directional Accuracy
- R²
- анализ остатков

## Используемые технологии

- Python 3
- pandas
- NumPy
- matplotlib
- seaborn
- statsmodels
- scikit-learn
- LightGBM
- Optuna
- openpyxl

```Bash
pip install pandas numpy matplotlib seaborn scikit-learn lightgbm optuna statsmodels openpyxl
```

## Запуск
1. Убедитесь, что weather_data.xlsx находится в корне проекта.
2. Запустите Jupyter:
```Bash
jupyter notebook
```
3. Откройте notebook.ipynb.
4. Выполните ячейки сверху вниз.