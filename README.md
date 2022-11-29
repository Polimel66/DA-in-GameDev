# АНАЛИЗ ДАННЫХ И ИСКУССТВЕННЫЙ ИНТЕЛЛЕКТ [in GameDev]
Отчет по лабораторной работе #5 выполнил(а):
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
Научиться интегрированию экономической системы в проект Unity и обучению ML-Agent.

## Задание 1
### Интегрировать экономическую систему в проект Unity и обучить ML-Agent
 - Создала и активировала виртуальное пространство
![image](https://user-images.githubusercontent.com/57943773/204527671-eb6924ec-62b5-46d9-a6c8-f42b83db2424.png)
![image](https://user-images.githubusercontent.com/57943773/204529485-30a9ab59-e972-4154-b222-091578444c66.png)
 - Установила пакеты из третей лабораторной работы
![image](https://user-images.githubusercontent.com/57943773/204529783-8d3d6ab1-a296-417c-9e28-c7f0875294ea.png)
![image](https://user-images.githubusercontent.com/57943773/204532095-6cb55ff0-ba34-4b20-ae22-2e2901b0af2f.png)
![image](https://user-images.githubusercontent.com/57943773/204561379-a162c5a6-1090-4518-956d-503dd51761f4.png)
 - Произвела обучение нейросети
![image](https://user-images.githubusercontent.com/57943773/204556068-53a1fbb4-4bd8-4570-8741-ea0584e92fe4.png)
![image](https://user-images.githubusercontent.com/57943773/204561616-f43b15ea-32f0-47e9-8fe1-e61a159d231d.png)

## Задание 2
### Измените параметры файла yaml-агента и определить какие параметры и как влияют на обучение модели. Опишите результаты, выведенные в TensorBoard
 - Графики до изменения данных:
![image](https://user-images.githubusercontent.com/57943773/204559806-4f79ecc8-a12f-4f00-9b1d-d213986a9660.png)
 - Изменения: (данные до и после изменения, а так же получившиеся графики)
1) Увеличила параметр epsilon на 0.2:

![image](https://user-images.githubusercontent.com/57943773/204568597-539cff20-1381-496d-b0f1-942a62c53458.png)
![image](https://user-images.githubusercontent.com/57943773/204568719-d60db27f-1ea6-4a95-9c62-141ece03e5fd.png)
![image](https://user-images.githubusercontent.com/57943773/204571081-45e85f1b-b25e-4fa7-b8a2-1f3eb6995296.png)

2) Увеличила batch_size на 512:

![image](https://user-images.githubusercontent.com/57943773/204572340-8bebafe9-e8e2-44ab-9b03-1d5cbcbbdf34.png)
![image](https://user-images.githubusercontent.com/57943773/204572478-19bd329f-17a9-4d15-8030-29a7ba8b9fe4.png)
![image](https://user-images.githubusercontent.com/57943773/204574756-10606236-e41a-46f0-9314-c4a0c83e6a9e.png)

3) Уменьшила lambd на 0.25:

![image](https://user-images.githubusercontent.com/57943773/204577132-cb595815-cee7-41c2-9f74-9ed72f45ded2.png)
![image](https://user-images.githubusercontent.com/57943773/204576791-e615c9df-9d2e-4cf0-8ad7-467c2c7ce796.png)
![image](https://user-images.githubusercontent.com/57943773/204579339-44c0dc0b-ec9e-4836-8765-cad1f7ed3330.png)

Результаты: 
 - При увеличении batch_size (количества производимых опытов на каждой иттерации) графики начали возрастать. 
 - Изменяя параметр lambd график Extrinsic Reward совершил резкий скачок вниз и снова вернулся в нормальное положение, но при изначальных данных график просто увеличивался. Entropy и Extrinsic Value Estimate не изменили своей тенденции. 
 - Увеличив параметр epsilon, графики Entropy и Extrinsic Value Estimate не сильно изменились. При этом Extrinsic Reward начал быстрее увеличивать своё значение. 
 - При каждом из изменений графики Beta, Epsilon и Learning Rate сменили свои значения, и после не меняли их пока обучение не заканчивалось.

## Выводы
Я научилась интегрировать экономическую систему в проект Unity и обучать MLAgent. Также я наблюдала за влиянием параметров файла yaml-агента на обучение модели.

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
