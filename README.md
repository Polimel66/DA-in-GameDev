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
### 
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


## Задание 3!

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
