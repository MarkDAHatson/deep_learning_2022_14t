# Проект "Распознавание номеров машин" 

## Описание
Проект выполнен как учебный в рамках курса "Глубокое обучение на практике" ИТМО командой №14. Состав команды:
1. Аржиловский Данил Андреевич
2. Васильева Диана Васильевна
3. Ромадановская Дарья Павловна

Схематично наше решение поставленной задачи выглядит следующим образом:
## ![Baseline](https://github.com/MarkDAHatson/deep_learning_2022_14t/blob/main/baseline.PNG)

## Датасет

Датасет состоял из 433 изображений машин с иностранными номерами. Для распознавания мы посчитали не важным, что эти номера не российские. В датасете присутствуют фотографии номеров машин с различных ракурсов, при этом в кадре может быть и более, чем 1 номер.

Ссылка на датасет:
https://www.kaggle.com/datasets/andrewmvd/car-plate-detection

## Результат работы
![Пикча](https://github.com/MarkDAHatson/deep_learning_2022_14t/blob/main/detection_number.PNG)

![Пикча2](https://github.com/MarkDAHatson/deep_learning_2022_14t/blob/main/number_car.PNG)

Т777ВМ177

## Эксперименты с моделями
Изначально мы проверили эксперимент, демонстрирующий вариант решения данного кейса без нейронных сетей. С помощью библиотеки cv-2 удалось добиться точности распознавания номеров приблизительно в 19% (эксперимент в папке), в результате было необходимо тестировать нейронные сети. Далее было проведено несколько экспериментов с различными моделями (результаты в таблице ниже, код - в папке) для выявления наиболее оптимальной как по метрикам качества, так и времени:

| Модель    | Size  | Epochs  | P     | R     | mAP50  |  mAP50-95  |
| --------- | ----  | ------- | ----- | ----- | -----  | --------   | 
| yolov5    | 400   | 65      | 0.824 | 0.721 | 0.761  | 0.581      |
| yolov5m6  | 400   | 65      | 0.985 | 0.909 | 0.987  | 0.687      |
| yolov7    | tbdl  | tbdl    | tbdl  | tbdl  | tbdl   | tbdl       |

Пример работы одной из моделей yolov5 (код - в папке):

![Пикча3](https://github.com/MarkDAHatson/deep_learning_2022_14t/blob/main/yolov5_ex.PNG)

Наиболее оптимальное соотношение метрик качества и времени удалось получить при помощи yolov7, которая и является окончательным решением нашего проекта.

## Эксперименты с OCR
Pytesseract

Для экспериментов с OCR было решено применить 2 наиболее популярных способа: pytesseract и easyocr. Результаты экспериментов с точностью для pytesseract можно увидеть в следующей таблице:

| PSM       | 7 | 9 | 10 | 11 | 13 |  
| --------- | ----  | ------- | ----- | ----- | ---- |
| Accuracy  | 0.46 | 0.49 | 0.57 | 0.43 | 0.42 |

Результаты Easyocr доступны в следующей таблице:

| TBDL |
| ---- |

Таким образом, финальным решением проекта для OCR выбран pytesseract, однако видно, что на данный момент метрика не достигла высоких показателей, поэтому этот этап проект будет дорабатываться.

## Статус проекта
В данный момент проект находится в стадии доработок до вечера 10.10.2022.
Коллеги-ревьюеры, если вы читаете это, пожалуйста, простите нас за задержку. Мы уверены, что проект удастся проверить достаточно быстро, даже за небольшое время вечера вторника
