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
1) Для OR хватило 4 эпохи, после вычисления выполнялись корректно: 
![image](https://user-images.githubusercontent.com/57943773/204281044-2aceb0ac-f852-4f07-8947-de1e274e0a6a.png)
![image](https://user-images.githubusercontent.com/57943773/204281198-722d891d-2811-40aa-be1b-9edbf3ceb135.png)
![image](https://user-images.githubusercontent.com/57943773/204281491-e9d27967-8ae9-484f-ad29-b7b9fc8e4e00.png)
2) 

## Задание 2
### Подробно описать каждую строку файла конфигурации нейронной сети. Самостоятельно найти информацию о компонентах Decision Requester, Behavior Parameters, добавленных сфере.
 - Behavior Parameters (определяет принятие объектом решений) - в нём указывается тип поведения, который будет использоваться: удалённый процесс обучения, обученная модель.
 - Decision Requester (запрашивает решение через регулярные промежутки времени).
```
behaviors:
RollerBall: # указание id агента
trainer_type: ppo # режим обучения
hyperparameters:
batch_size: 10 # количество опыта на итерациях
buffer_size: 100 # количество опыта, нужное перед обновлением модели
learning_rate: 3.0e-4 # начальная скорость обучения
beta: 5.0e-4 # сила регуляции энтропии (увеличивает случайность действий)
epsilon: 0.2 # порог расхождений между старой политикой при обновлении и новой
lambd: 0.99 # параметр показывающий насколько сильно агент полагается на value estimate
num_epoch: 3 # (при выполнении оптимизации) количество проходов через буфер опыта
learning_rate_schedule: linear # показывает изменение скорости обучения. linear - линейно уменьшает скорость
network_settings:
normalize: false # отключение нормализации входных данных
hidden_units: 128 # количество нейронов в скрытых слоях сети
num_layers: 2 # количество скрытых слоёв в сети
reward_signals:
extrinsic:
gamma: 0.99 # коэффициент скидки для будущих вознаграждений
strength: 1.0 # коэффициент умножения вознаграждения
max_steps: 500000 # количество шагов, которые необходимо выполнить в среде до завершения обучения
time_horizon: 64 # количество опыта, которое нужно собрать для каждого агента, прежде чем добавлять его в буфер
summary_freq: 10000 # количество опыта, которое нужно собрать перед созданием и отображением статистики
```

 
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
