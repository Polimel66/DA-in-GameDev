# АНАЛИЗ ДАННЫХ И ИСКУССТВЕННЫЙ ИНТЕЛЛЕКТ [in GameDev]
Отчет по лабораторной работе #1 выполнил(а):
- Мельникова Полина Эдуардовна
- РИ210949
Отметка о выполнении заданий (заполняется студентом):

| Задание | Выполнение | Баллы |
| ------ | ------ | ------ |
| Задание 1 | # | 60 |
| Задание 2 | # | 20 |
| Задание 3 | # | 20 |

знак "*" - задание выполнено; знак "#" - задание не выполнено;

Работу проверили:
- к.т.н., доцент Денисов Д.В.
- к.э.н., доцент Панов М.А.
- ст. преп., Фадеев В.О.

[![N|Solid](https://cldup.com/dTxpPi9lDf.thumb.png)](https://nodesource.com/products/nsolid)

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)

Структура отчета

- Данные о работе: название работы, фио, группа, выполненные задания.
- Цель работы.
- Задание 1.
- Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).
- Задание 2.
- Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).
- Задание 3.
- Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).
- Выводы.
- ✨Magic ✨

## Цель работы
Ознакомиться с основными операторами зыка Python на примере реализации линейной регрессии.

## Задание 1
### Написать программу Hello World на Python и Unity
![image](https://user-images.githubusercontent.com/57943773/192320351-383e76b9-7344-48c3-9fa7-736c17d0ba28.png)
![image](https://user-images.githubusercontent.com/57943773/192320505-a61136a7-9418-42a1-b3c9-b80be5c8305d.png)
## Задание 2
### Пошагово выполнить каждый пункт раздела "ход работы" с описанием и примерами реализации задач
Ход работы:
 - Произвести подготовку данных для работы с алгоритмом линейной регрессии. 10 видов данных были установлены случайным образом, и данные находились в линейной зависимости. Данные преобразуются в формат массива, чтобы их можно было вычислить напрямую при использовании умножения и сложения.
![image](https://user-images.githubusercontent.com/57943773/192322048-633ef686-ab86-4a82-ac89-16e68aa6df37.png)
 - Определите связанные функции. Функция модели: определяет модель линейной регрессии wx+b. Функция потерь: функция потерь среднеквадратичной ошибки. Функция оптимизации: метод градиентного спуска для нахождения частных производных w и b.
![image](https://user-images.githubusercontent.com/57943773/192324855-604824ba-4169-4191-9020-9b5eccec30ca.png)
 - Инициализация и модель итеративной оптимизации
![image](https://user-images.githubusercontent.com/57943773/192326144-d6203e8e-56b5-4729-9706-d8db451848a5.png)
 - На 2 итерации отображаются значения параметров, значения потерь и визуализация после итерации
![image](https://user-images.githubusercontent.com/57943773/192326924-455697e7-cd1a-4a08-997d-b3bf857d7a9f.png)
 - На 3 итерации отображаются значения параметров, значения потерь и визуализация после итерации
![image](https://user-images.githubusercontent.com/57943773/192327177-ebb80f7a-85b9-48c4-b846-4180bcfad255.png)
 - На 4 итерации отображаются значения параметров, значения потерь и визуализация после итерации
![image](https://user-images.githubusercontent.com/57943773/192327313-34f999d8-d794-4762-b862-5ad0da8121d0.png)
 - На 5 итерации отображаются значения параметров, значения потерь и визуализация после итерации
![image](https://user-images.githubusercontent.com/57943773/192327416-90f4a09e-3d0a-4c1c-ad34-52e71a8aaba7.png)
 - На 1000-й итерации отображаются значения параметров, значения потерь и визуализация после итерации
![image](https://user-images.githubusercontent.com/57943773/192327578-dbefb4d5-39a6-45c8-a566-7288026701bf.png)
 - 
## Задание 3
### Должна ли величина loss стремиться к нулю при изменении исходных данных? Ответьте на вопрос, приведите пример выполнения кода, который подтверждает ваш ответ.
Должна, потому что решением прошлой задачи является минимизация этой функции. Следовательно, loss стремится к 0. Пример, подтверждающий мой ответ:
 - Новые данные
![image](https://user-images.githubusercontent.com/57943773/192332984-77d8ab3b-d76f-4b12-a5d5-4a41511a0e8e.png)
 - 1 шаг
![image](https://user-images.githubusercontent.com/57943773/192333165-4095ca88-1b1c-4006-ab1d-d7f963401ff2.png)
 - 1000 шаг
![image](https://user-images.githubusercontent.com/57943773/192333325-c5d4e421-bd0c-4a37-b9b7-96f466b68d87.png)
## Задание 3
### Какова роль параметра Lr? Ответьте на вопрос, приведите пример выполнения кода, который подтверждает ваш ответ. В качестве эксперимента можете изменить значение параметра.
Lr - множитель, от которого зависит изменение коэффицентов a и b. Чем больше Lr, тем больше изменение коэффицентов и наоборот. Например, если взять те же данные, что и
в предыдущем примере, но увеличить Lr в 1000 раз.
 - 1 шаг
![image](https://user-images.githubusercontent.com/57943773/192336154-3cc57c9c-0a72-4073-a6a9-a41a9bdd0421.png)
 - 1000 шаг
![image](https://user-images.githubusercontent.com/57943773/192336005-4f26fc5e-8f15-4dd0-ace0-e7fbb8c2858e.png)
 - 
- Перечисленные в этом туториале действия могут быть выполнены запуском на исполнение скрипт-файла, доступного [в репозитории](https://github.com/Den1sovDm1triy/hfss-scripting/blob/main/ScreatingSphereInAEDT.py).
- Для запуска скрипт-файла откройте Ansys Electronics Desktop. Перейдите во вкладку [Automation] - [Run Script] - [Выберите файл с именем ScreatingSphereInAEDT.py из репозитория].

```py

import ScriptEnv
ScriptEnv.Initialize("Ansoft.ElectronicsDesktop")
oDesktop.RestoreWindow()
oProject = oDesktop.NewProject()
oProject.Rename("C:/Users/denisov.dv/Documents/Ansoft/SphereDIffraction.aedt", True)
oProject.InsertDesign("HFSS", "HFSSDesign1", "HFSS Terminal Network", "")
oDesign = oProject.SetActiveDesign("HFSSDesign1")
oEditor = oDesign.SetActiveEditor("3D Modeler")
oEditor.CreateSphere(
	[
		"NAME:SphereParameters",
		"XCenter:="		, "0mm",
		"YCenter:="		, "0mm",
		"ZCenter:="		, "0mm",
		"Radius:="		, "1.0770329614269mm"
	], 
)

```


## Выводы

Абзац умных слов о том, что было сделано и что было узнано.

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
