# MoskowRegion
Russian Regional Championship (Moscow Region) October 2022

В состав репозитория включены файлы кода и входные данные для решения в два этапа.

1-й этап - предобработка и основная модель. Все данные находятся в директории "Первый этап Основная модель". Файл "Московская область Первый этап.lgp" - модуль lgp аналитической платформы Логином в бесплатной общедоступной версии Community Edition v.6.5.1 (дистрибутив можно свободно получить по адресу https://loginom.ru/download). Входные данные - приложенные в условиях задачи, без каких-либо добавлений (в последней версии исходных наборов задачи). Выходные данные предобработки - трейн (файл "train_net.csv"), тест (файл "test_net.csv"), в готовом виде для обработки основной моделью.
Основная модель - ноутбук Jupyter "catboost_MR_united.ipynb", целиком воспроизводимый код, дающий наилучший результат по действиям игрока (на публичном лидерборде 0.347489). Приложен итог работы модели - сабмиссия в файле "submission_best_347489.csv".

2-й этап - корректировка итога результата основной модели. Все данные находятся в директории "Второй этап Корректировка".
Файл "Московская область Второй этап.lgp" - предобработка данных для корректировки, включение в новый трейновый и тестовый наборы прогнозов лучшей основной модели (в качестве метафичи), а также данных агрегаций по действиям команды игрока - а именно средней оценки по каждой из шести категорий, среднего стандартного отклонения по ценке, а также среднего, медианы и стд по местам, занятым в каждой из шести категорий командной оценки.
Приложены также модели корректировки, улучшившие общий результат, в следующей последовательности (полученный на ЛБ результат - в названии выходных файлов и откорректированных сабмиссий):

Улучшение по переменной Systemic thinking. Ноутбук "catboost_MR_2ep_по Systemic thinking.ipynb", выход модели "прогноз по Systemic thinking предварительный второй этап и текст_349383.csv", итоговая сабмиссия модели "проба второго этапа по Systemic thinking_349383.csv"

Улучшение по переменной Adaptability. Ноутбук "catboost_MR_2ep_по Adaptability.ipynb", выход модели "прогноз по Adaptability предварительный второй этап и текст_351445.csv", итоговая сабмисссия "проба второго этапа по Adaptability_351445.csv" 

Модирование значения 3. Поскольку статанализ предварительной сабмиссии показало завышение значения "3" в трех целевых переменных выше распределения в трейне, по лучшим сабмиссям целевых переменных (основной, лучшей и 4-м близким по прогнозу) были выбраны лишь те значения "3", которые присутствуют по всем 5-и прогнозам. Остальные заменяются на наиболее вероятное значение 4.
Модирование позволило улучшить результат по двум переменным - "Analytical thinking" и "Adaptability".
Приложены таблицы модирования по лучшим сабмиссиям прогноза этих двух переменных - файлы "Таблица для модирования Adaptability_361729.csv", "Таблица для модирования Analytical thinking.csv", модуль "catboost_MR_2ep по Analytical thinking.ipynb" - формирующий прогнозы для "Analytical thinking", модуль "Модирование Adaptability 3.ipynb" - показывающий алгоритм модирования по таблицам, итог модирования по "Analytical thinking" (файл "модирование Analytical thinking_356890.csv", с лучшим промежуточным результатом), последний этап корректировки и модирования - файл "проба модирования Adaptability_361729.csv", в качестве итогового результата решения по чемпионату представлен файл "итоговый прогноз_361729.csv" (он же продублирован в корне репозитория)

Таким образом на 2-м этапе открректированы результаты по 3-м целевым переменным. По целевой переменной "Focus" лучший результат был достигнут на основном этапе, он не корректировался.

Итоговый результат - 0.361729 на публичном лидерборде.
