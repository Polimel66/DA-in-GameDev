# АНАЛИЗ ДАННЫХ И ИСКУССТВЕННЫЙ ИНТЕЛЛЕКТ [in GameDev]
Отчет по лабораторной работе #4 выполнил(а):
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


## Задание 1
### Интегрировать экономическую систему в проект Unity и обучить ML-Agent
 - Создала и активировала виртуальное пространство
![image](https://user-images.githubusercontent.com/57943773/204527671-eb6924ec-62b5-46d9-a6c8-f42b83db2424.png)
![image](https://user-images.githubusercontent.com/57943773/204529485-30a9ab59-e972-4154-b222-091578444c66.png)
 - Установила пакеты из третей лабораторной работы
![image](https://user-images.githubusercontent.com/57943773/204529783-8d3d6ab1-a296-417c-9e28-c7f0875294ea.png)
![image](https://user-images.githubusercontent.com/57943773/204532095-6cb55ff0-ba34-4b20-ae22-2e2901b0af2f.png)
 - ![image](https://user-images.githubusercontent.com/57943773/204556068-53a1fbb4-4bd8-4570-8741-ea0584e92fe4.png)
![image](https://user-images.githubusercontent.com/57943773/204561379-a162c5a6-1090-4518-956d-503dd51761f4.png)
![image](https://user-images.githubusercontent.com/57943773/204561616-f43b15ea-32f0-47e9-8fe1-e61a159d231d.png)


## Задание 2
### 
![image](https://user-images.githubusercontent.com/57943773/204559806-4f79ecc8-a12f-4f00-9b1d-d213986a9660.png)

## Задание 3
### Построить визуальную модель работы перцептрона на сцене Unity.
Создала работу функции OR:
 - Белый куб - 0, черный куб - 1
![image](https://user-images.githubusercontent.com/57943773/204305658-a6d69945-9a54-4d62-bddc-c1b16b3dec95.png)
 - Создала скрипт для изменения цвета кубов (при столкновении)
```
using UnityEngine;

public class ColorChanger : MonoBehaviour
{
    private void OnTriggerEnter(Collider other)
    {
        if (gameObject.GetComponent<Renderer>().material.color == Color.white && other.gameObject.GetComponent<Renderer>().material.color == Color.white)
        {
            gameObject.GetComponent<Renderer>().material.color = Color.white;
            other.gameObject.GetComponent<Renderer>().material.color = Color.white;
            
        }
        else
        {
            gameObject.GetComponent<Renderer>().material.color = Color.black;
            other.gameObject.GetComponent<Renderer>().material.color = Color.black;
        }
    }
}
```
 - Запустила проект. Сцена после запуска - результат работы команды OR. Цвета кубиков сменились корректно, в соответствии с функцией.

![lab4](https://user-images.githubusercontent.com/57943773/204309038-8bd7dc8d-8478-4e5e-803a-e9daaa4c152c.gif)


## Выводы
Я познакомилась с работой перцептрона. Также создала перцептрон, который производит вычисления для различных логических функций, визуализировала его работу на сцене Unity и построила график зависимости количества эпох от ошибки обучения.

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
