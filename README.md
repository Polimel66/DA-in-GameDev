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
 - Заполнила поле Input для каждого Elemetn и запустила проект.
1 - Для OR хватило 3 эпохи, с четвертой эпохи вычисления выполнялись корректно: 
![image](https://user-images.githubusercontent.com/57943773/204281044-2aceb0ac-f852-4f07-8947-de1e274e0a6a.png)
![image](https://user-images.githubusercontent.com/57943773/204281198-722d891d-2811-40aa-be1b-9edbf3ceb135.png)
![image](https://user-images.githubusercontent.com/57943773/204281491-e9d27967-8ae9-484f-ad29-b7b9fc8e4e00.png)

2 - Для AND хватило 5 эпох, с шестой эпохи вычисления выполнялись корректно:
![image](https://user-images.githubusercontent.com/57943773/204284924-d3017c17-0ff7-493e-8c64-65cb8e008654.png)
![image](https://user-images.githubusercontent.com/57943773/204285012-37716c24-82c9-4686-98ae-f826a5a6e97e.png)
![image](https://user-images.githubusercontent.com/57943773/204285051-3c0d287f-fb67-499b-8df5-ceca0bb23476.png)
![image](https://user-images.githubusercontent.com/57943773/204285124-c58f8ede-42a0-4d1a-b800-b86b00b37b05.png)

3 - Для NAND хватило 5 эпох, с шестой эпохи вычисления выполнялись корректно:
![image](https://user-images.githubusercontent.com/57943773/204286671-ff4e87e9-7565-4006-9ff4-b313277cb134.png)
![image](https://user-images.githubusercontent.com/57943773/204286731-72dc6a03-0691-442a-896f-8bf05446c71d.png)
![image](https://user-images.githubusercontent.com/57943773/204286766-d5ca6469-6d03-4a2a-a02a-7be00e533d90.png)
![image](https://user-images.githubusercontent.com/57943773/204286420-a1453d14-395a-47c3-b431-73076046ff15.png)

4 - Для XOR перцептрон не смог обучиться за 15000 эпох, вычисления выполнялись некорректно:
![image](https://user-images.githubusercontent.com/57943773/204289372-d078aa56-bbfa-4919-87a4-4837a71728cb.png)
![image](https://user-images.githubusercontent.com/57943773/204289514-fa608e20-e4bf-4259-847d-40a822ea0be5.png)
![image](https://user-images.githubusercontent.com/57943773/204289580-b8d3a577-6963-4298-83f3-38188e78accd.png)

## Задание 2
### Построить графики зависимости количества эпох от ошибки обучения. Указать от чего зависит необходимое количество эпох обучения.
![image](https://user-images.githubusercontent.com/57943773/204293345-546c063d-aa7a-4c3e-a1cf-fc07caadda54.png)

 
## Задание 3
### Доработайте сцену и обучите ML-Agent таким образом, чтобы шар перемещался между двумя кубами разного цвета. Кубы должны, как и впервом задании, случайно изменять кооринаты на плоскости.
 - добавила ещё один куб и отредактировала код
```
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using Unity.MLAgents;
using Unity.MLAgents.Sensors;
using Unity.MLAgents.Actuators;

public class RollerAgent : Agent
{
    Rigidbody rBody;
    void Start()
    {
        rBody = GetComponent<Rigidbody>();
    }
    public GameObject Target1;
    public GameObject Target2;
    private bool target1Collected;
    private bool target2Collected;
    public override void OnEpisodeBegin()
    {
        if (this.transform.localPosition.y < 0)
    {
        this.rBody.angularVelocity = Vector3.zero;
        this.rBody.velocity = Vector3.zero;
        this.transform.localPosition = new Vector3(0, 0.5f, 0);
    }
    Target1.transform.localPosition = new Vector3(Random.value * 8-4, 0.5f, Random.value * 8-4);
    Target2.transform.localPosition = new Vector3(Random.value * 8-4, 0.5f, Random.value * 8-4);
    Target1.SetActive(true);
    Target2.SetActive(true);
    target1Collected = false;
    target2Collected = false;
    }
    public override void CollectObservations(VectorSensor sensor)
    {
    sensor.AddObservation(Target1.transform.localPosition);
    sensor.AddObservation(Target2.transform.localPosition);
    sensor.AddObservation(this.transform.localPosition);
    sensor.AddObservation(target1Collected);
    sensor.AddObservation(target2Collected);
    sensor.AddObservation(rBody.velocity.x);
    sensor.AddObservation(rBody.velocity.z);
    }
    public float forceMultiplier = 10;
    public override void OnActionReceived(ActionBuffers actionBuffers)
    {Vector3 controlSignal = Vector3.zero;
    controlSignal.x = actionBuffers.ContinuousActions[0];
    controlSignal.z = actionBuffers.ContinuousActions[1];
    rBody.AddForce(controlSignal * forceMultiplier);
    float distanceToTarget1 = Vector3.Distance(this.transform.localPosition, Target1.transform.localPosition);
    float distanceToTarget2 = Vector3.Distance(this.transform.localPosition, Target2.transform.localPosition);
    if (!target1Collected & distanceToTarget1 < 1.42f)
    {
        target1Collected = true;
        Target1.SetActive(false);
    }
    if (!target2Collected & distanceToTarget2 < 1.42f)
    {
        target2Collected = true;
        Target2.SetActive(false);
    }
    if(target1Collected & target2Collected)
    {
        SetReward(1.0f);
        EndEpisode();
    }
    else if (this.transform.localPosition.y < 0)
    {
        EndEpisode();
    }
}
}
```
 - Видео работы:

https://user-images.githubusercontent.com/57943773/198063529-c5bfec10-fbce-4daf-b2bc-a2e05a5702be.mp4


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
