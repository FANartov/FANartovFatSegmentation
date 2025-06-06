# Ultrasound Fat Segmentation with U-Net

Этот репозиторий содержит полный пайплайн для сегментации ультразвуковых (УЗИ) слайсов на основе модели U-Net. В проекте реализована предварительная обработка изображений (билатеральное фильтрование для подавления спекл-шума и CLAHE для улучшения контраста), подготовка датасета, обучение модели с логированием метрик (Loss, Dice, IoU), визуализация изменений метрик по эпохам и оценка модели на тестовой выборке.

---

## Содержание

- [Описание](#описание)
- [Установка](#установка)
- [Использование](#использование)
- [Хранение весов модели](#хранение-весов-модели)
- [Лицензия](#лицензия)

---

## Описание

Проект направлен на автоматизацию бинарной сегментации ультразвуковых изображений с целью выделения жировой ткани для последующей компенсации аберраций при терапии HIFU. Основные этапы:
- **Предобработка изображений:** применение билатерального фильтра для снижения спекл-шума и CLAHE для улучшения контраста.
- **Подготовка датасета:** реализация класса датасета с разделением на обучающую, валидационную и тестовую выборки.
- **Обучение модели:** реализация цикла обучения для U-Net с логированием метрик (Loss, Dice, IoU) и сохранением лучшей модели.
- **Визуализация:** построение графиков изменения метрик по эпохам.
- **Оценка:** вычисление метрик на тестовой выборке.

---

## Установка

1. **Клонируйте репозиторий:**

   ```bash
   git clone https://github.com/FANartov/FANartovFatSegmentation.git
   cd FANartovFatSegmentation

2. **Создайте и активируйте виртуальное окружение (рекомендуется Anaconda):**

   ```bash
   conda create -n segmentation_env python=3.12
   conda activate segmentation_env

3. **Установите зависимости:**

   ```bash
   pip install -r requirements.txt

---

## Использование

### Подготовка данных

- Разместите изображения ультразвуковых слайсов в папке `data/cropped_images`.
- Разместите соответствующие сегментационные маски в папке `data/cropped_masks`.
- Запустите ноутбук `01_Configuration_and_Data_Preparation.ipynb`.

### Обучение модели

- Запустите ноутбук `02_Model_Training_and_Testing.ipynb`.
- Тренировочный цикл реализует обучение модели с логированием метрик (Loss, Dice, IoU) для обучающей и валидационной выборок.
- По окончании обучения сохраняется лучший вариант модели.


### Визуализация результатов

- После завершения обучения запускается ячейка, которая строит графики зависимости Loss, Dice и IoU по эпохам для обучающей и валидационной выборок.

### Оценка на тестовой выборке

- В конце блокнота производится вычисление метрик на тестовой выборке.
- Расчёт метрик (Loss, Dice, IoU) выполняется аналогично обучению, а результаты выводятся в консоль.

---

## Хранение весов модели

Предобученные веса моделей хранятся по ссылке: https://drive.google.com/drive/folders/1YvfRvRBCrxbNrUNyQirZgjkgRVIDKX0u?usp=sharing

---

## Лицензия

Этот проект распространяется под лицензией CC0 1.0 Universal.