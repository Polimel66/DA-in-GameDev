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
Познакомиться с работой перцептрона.

## Задание 1
### В проекте Unity реализовать перцептрон, который умеет производить вычисления:
Ход работы:
 - Создала пустой 3D проект на Unity, добавила пустой GameObject, скачала и навесила на этот объект скрипт Perceptron.
![image](https://user-images.githubusercontent.com/57943773/204277683-f43783bf-8fd5-44ba-a097-2e879b178e7c.png)

Заполнила поле Input для каждого Elemetn и запустила проект.
 -- Для OR хватило 3 эпохи, с четвертой эпохи вычисления выполнялись корректно: 
![image](https://user-images.githubusercontent.com/57943773/204281044-2aceb0ac-f852-4f07-8947-de1e274e0a6a.png)
![image](https://user-images.githubusercontent.com/57943773/204281198-722d891d-2811-40aa-be1b-9edbf3ceb135.png)
![image](https://user-images.githubusercontent.com/57943773/204281491-e9d27967-8ae9-484f-ad29-b7b9fc8e4e00.png)

 - Для AND хватило 5 эпох, с шестой эпохи вычисления выполнялись корректно:
![image](https://user-images.githubusercontent.com/57943773/204284924-d3017c17-0ff7-493e-8c64-65cb8e008654.png)
![image](https://user-images.githubusercontent.com/57943773/204285012-37716c24-82c9-4686-98ae-f826a5a6e97e.png)
![image](https://user-images.githubusercontent.com/57943773/204285051-3c0d287f-fb67-499b-8df5-ceca0bb23476.png)
![image](https://user-images.githubusercontent.com/57943773/204285124-c58f8ede-42a0-4d1a-b800-b86b00b37b05.png)

 - Для NAND хватило 5 эпох, с шестой эпохи вычисления выполнялись корректно:
![image](https://user-images.githubusercontent.com/57943773/204286671-ff4e87e9-7565-4006-9ff4-b313277cb134.png)
![image](https://user-images.githubusercontent.com/57943773/204286731-72dc6a03-0691-442a-896f-8bf05446c71d.png)
![image](https://user-images.githubusercontent.com/57943773/204286766-d5ca6469-6d03-4a2a-a02a-7be00e533d90.png)
![image](https://user-images.githubusercontent.com/57943773/204286420-a1453d14-395a-47c3-b431-73076046ff15.png)

 - Для XOR перцептрон не смог обучиться за 15000 эпох, вычисления выполнялись некорректно:
![image](https://user-images.githubusercontent.com/57943773/204289372-d078aa56-bbfa-4919-87a4-4837a71728cb.png)
![image](https://user-images.githubusercontent.com/57943773/204289514-fa608e20-e4bf-4259-847d-40a822ea0be5.png)
![image](https://user-images.githubusercontent.com/57943773/204289580-b8d3a577-6963-4298-83f3-38188e78accd.png)

## Задание 2
### Построить графики зависимости количества эпох от ошибки обучения. Указать от чего зависит необходимое количество эпох обучения.
![image](https://user-images.githubusercontent.com/57943773/204294651-8e1867bd-5596-4dab-8e72-092a0a1b07d5.png)
![image](https://user-images.githubusercontent.com/57943773/204294516-039ecc56-867d-41f7-acc2-6d962703c7e0.png)

Нужное количество эпох обучения завистит от weights и bias.
```
double DotProductBias(double[] v1, double[] v2)
	{
		if (v1 == null || v2 == null)
			return -1;

		if (v1.Length != v2.Length)
			return -1;

		double d = 0;
		for (int x = 0; x < v1.Length; x++)
		{
			d += v1[x] * v2[x];
		}

		d += bias;

		return d;
	}

double CalcOutput(int i)
	{
		double dp = DotProductBias(weights, ts[i].input);
		if (dp > 0) return (1);
		return (0);
	}
 ```
 
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
 - Запустила проект. Сцена после запуска - результат работы команды OR. Цвета кубиков сменились корректно, в соответствии с операцией OR.

![lab4](https://user-images.githubusercontent.com/57943773/204309038-8bd7dc8d-8478-4e5e-803a-e9daaa4c152c.gif)


## Выводы
Я научилась работать с ML-агентом, узнала как его обучать. Поняла, что увеличение количества копий позволяет модели обучиться быстрее.
Игровой баланс — равновесие между персонажами, командами, тактиками игры и другими игровыми объектами. В играх очень важно всё рассичтать, чтобы игроку было интересно.
Характеристики персонажа и окружающих его объектов должны подстраиваться друг под друга во время игрового процесса. В этом нейросети могут нам помочь, вовремя повышая или понижая характеристики различных объектов и персонажей, создавая баланс между ними.

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
