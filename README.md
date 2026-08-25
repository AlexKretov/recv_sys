# 🛍️ RecSys — Система рекомендаций на отзывах Amazon

![Python](https://img.shields.io/badge/Python-3.8%2B-blue?style=for-the-badge&logo=python)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?style=for-the-badge&logo=jupyter)
![Pandas](https://img.shields.io/badge/pandas-%23150458.svg?style=for-the-badge&logo=pandas&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-%23F7931E.svg?style=for-the-badge&logo=scikit-learn&logoColor=white)

**Рекомендательная система** на основе отзывов пользователей Amazon (категория **Patio, Lawn and Garden**).  
Проект содержит полный пайплайн: **EDA → предобработка → несколько моделей → оценка → визуализация**.

## ✨ Основные возможности

- **Полный EDA** с анализом разреженности, распределения рейтингов и активности пользователей
- **Leave-One-Out** сплит по времени (последний отзыв пользователя — в тест)
- **5 моделей**:
  - Popularity (бейзлайн)
  - ALS (implicit library)
  - Item-Item Collaborative Filtering
  - SVD (матричная факторизация)
  - Hybrid (взвешенная комбинация)
- **Метрики**: HR@10, MRR@10, NDCG@10, Coverage
- Красивые визуализации с `matplotlib` + `seaborn`
- Подробные комментарии и таблицы сравнения

## 📊 Ключевые характеристики датасета

**Источник**: [Amazon Reviews 2018 — Patio_Lawn_and_Garden_5.json.gz](https://jmcauley.ucsd.edu/data/amazon/) (798 415 отзывов)

| Параметр                  | Значение      | Комментарий                     |
|---------------------------|---------------|---------------------------------|
| Кол-во отзывов            | 798 415       | —                               |
| Уникальных пользователей  | 103 431       | —                               |
| Уникальных товаров (ASIN) | 32 918        | —                               |
| Разреженность матрицы     | ~99.98%       | Очень сложная задача            |
| Средний рейтинг           | 4.32          | Сильный bias к 5 звёздам       |
| Период данных             | 2000–2018     | —                               |

**Графики EDA** (см. папку `images/` после запуска ноутбука):

1. **Распределение рейтингов** (`sns.barplot`) — преобладают оценки `5.0` (~533k).
2. **Активность пользователей** (`sns.histplot`, log-scale) — большинство оставляет 1–10 отзывов (правый скос).
3. **Активность товаров** — аналогично, несколько хитов с тысячами отзывов.

## 🏗️ Структура проекта

```bash
recv_sys/
├── rec_sys.ipynb              # Основной ноутбук (исходник)
├── requirements.txt           # Зависимости (см. выше)
├── README.md                  # Этот файл
├── data/                      # ← скачайте сюда Patio_Lawn_and_Garden_5.json.gz
├── images/                    # Графики (создайте папку и сохраните из ноутбука)
├── src/                       # (рекомендуется) — модули моделей, utils, evaluation
│   ├── models.py
│   ├── evaluation.py
│   └── data_utils.py
└── .gitignore
