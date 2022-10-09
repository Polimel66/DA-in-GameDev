# АНАЛИЗ ДАННЫХ И ИСКУССТВЕННЫЙ ИНТЕЛЛЕКТ [in GameDev]
Отчет по лабораторной работе #1 выполнил(а):
- Мельникова Полина Эдуардовна
- РИ210949
Отметка о выполнении заданий (заполняется студентом):

| Задание | Выполнение | Баллы |
| ------ | ------ | ------ |
| Задание 1 | * | 60 |
| Задание 2 | * | 20 |
| Задание 3 | * | 20 |

знак "*" - задание выполнено; знак "#" - задание не выполнено;

Работу проверили:
- к.т.н., доцент Денисов Д.В.
- к.э.н., доцент Панов М.А.
- ст. преп., Фадеев В.О.

[![N|Solid](https://cldup.com/dTxpPi9lDf.thumb.png)](https://nodesource.com/products/nsolid)

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)

## Цель работы
Ознакомиться с основными операторами зыка Python на примере реализации линейной регрессии.

## Задание 1
### Реализовать совместную работу и передачу данных в связке Python - Google-Sheets – Unity.
 - Установила Google Drive API и Google Sheets API
![image](https://user-images.githubusercontent.com/57943773/194777467-7dbd6dac-1321-46f5-a83a-a0e0c0f58990.png)
 - Сделала service account
![image](https://user-images.githubusercontent.com/57943773/194777482-d3758630-8539-4614-a248-cc721c633936.png)
 - Сделала UnitySheets и добавила редактора
![image](https://user-images.githubusercontent.com/57943773/194777513-e7db362b-dea9-4117-b568-b8c5e6d80b52.png)
 - Подключила необходимые пакеты. Заполнила таблицу UnitySheets.
![image](https://user-images.githubusercontent.com/57943773/194777921-bc04ce10-08fb-45bc-aada-3382997195c7.png)
![image](https://user-images.githubusercontent.com/57943773/194777930-fb21aa66-6f7a-4866-a682-035b3ece7193.png)
 - Сделала API key. Сделала UnitySheets доступным для редактирования по ссылке.
![image](https://user-images.githubusercontent.com/57943773/194778095-bdc5a9e3-db2b-49e7-b744-3055b8c1c0fd.png)
![image](https://user-images.githubusercontent.com/57943773/194778140-f9fc51a3-9022-4c04-80de-da5f3b597df2.png)
 - Создала проект, импортировала файлы в Unity
![image](https://user-images.githubusercontent.com/57943773/194778628-286491a1-4b93-40dd-8034-e054d14a574b.png)
 - Связала Unity и GoogleSheets
![image](https://user-images.githubusercontent.com/57943773/194779277-85fda8a8-6542-40fc-b733-a921175e1e10.png)
![image](https://user-images.githubusercontent.com/57943773/194779470-3fdc3417-683b-45a7-8cd2-0a722498fc10.png)
 - Подключила музыку
![image](https://user-images.githubusercontent.com/57943773/194779800-301cbc7a-bd64-4ac8-9b11-a8b78283fb02.png)
![image](https://user-images.githubusercontent.com/57943773/194779814-58922327-276b-4710-b3cb-e62ee873d093.png)
 - Услышала звуки про лорда
![image](https://user-images.githubusercontent.com/57943773/194779862-369937c4-a5da-417d-bdcc-1b1cdfe643c3.png)

## Задание 2
### Реализовать запись в Google-таблицу набора данных, полученных с помощью линейной регрессии из лабораторной работы № 1
#### Ход работы:
 - 10 раз с шагом в 100, 200, 300, 400 ... 1000 итераций пройдемся моделью. Посчитаем разницу в ошибок на каждой из 10 итераций.
Далее загружаем значения в Google Spreadsheets.
![image](https://user-images.githubusercontent.com/57943773/194780459-8c131702-81ea-48ce-b49d-6ded0ce9bab3.png)
![image](https://user-images.githubusercontent.com/57943773/194780507-e794e0c1-4828-4ea1-ab93-9955ab756cc6.png)
![image](https://user-images.githubusercontent.com/57943773/194780538-ab1526b1-773a-4196-9863-1348cde9518f.png)


## Задание 3
### Должна ли величина loss стремиться к нулю при изменении исходных данных? Ответьте на вопрос, приведите пример выполнения кода, который подтверждает ваш ответ.
#### Ход работы:


## Выводы
В результате лабораторной работы я узнала, о методе вычилсения "потерь" предсказания и методе оптимизации для минимизации "потерь". Узнала о базовых библиотеках numpy и matplotlib. Узнала о основных операторах языка Python на примере линейной регрессии.

| Plugin | README |
| ------ | ------ |
| Dropbox | [plugins/dropbox/README.md][PlDb] |
| GitHub | [plugins/github/README.md][PlGh] |
| Google Drive | [plugins/googledrive/README.md][PlGd] |
| OneDrive | [plugins/onedrive/README.md][PlOd] |
| Medium | [plugins/medium/README.md][PlMe] |
| Google Analytics | [plugins/googleanalytics/README.md][PlGa] |

## Powered by

**BigDigital Team: Denisov | Fadeev | Panov**
