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
### Реализовать систему машинного обучения в связке Python - Google-Sheets – Unity.
 - Добавила в проект Unity нужные файлы
![image](https://user-images.githubusercontent.com/57943773/197792122-21a2d578-7b1d-425e-9e4c-97421626b141.png)
 - установила mlagents 0.28.0 и torch 1.7.1
![image](https://user-images.githubusercontent.com/57943773/197829714-322f84b8-ad34-4f99-a768-0341cb3cdd0a.png)
![image](https://user-images.githubusercontent.com/57943773/197800426-9bf6fcb6-e68c-4ea1-b484-a1b5b13de9dd.png)
 - Создала на сцене плоскость, куб и сферу, создала и подключила скрипт-файл к сфере 
![image](https://user-images.githubusercontent.com/57943773/197806089-becb568f-c91b-4a93-8965-f845d1a7cff9.png)
 - Код скрипта:
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
    public Transform Target;
    public override void OnEpisodeBegin()
    {
        if (this.transform.localPosition.y < 0)
        {
            this.rBody.angularVelocity = Vector3.zero;
            this.rBody.velocity = Vector3.zero;
            this.transform.localPosition = new Vector3(0, 0.5f, 0);
        }
        Target.localPosition = new Vector3(Random.value * 8-4, 0.5f, Random.value * 8-4);
    }
    public override void CollectObservations(VectorSensor sensor)
    {
        sensor.AddObservation(Target.localPosition);
        sensor.AddObservation(this.transform.localPosition);
        sensor.AddObservation(rBody.velocity.x);
        sensor.AddObservation(rBody.velocity.z);
    }
    public float forceMultiplier = 10;
    public override void OnActionReceived(ActionBuffers actionBuffers)
    {
        Vector3 controlSignal = Vector3.zero;
        controlSignal.x = actionBuffers.ContinuousActions[0];
        controlSignal.z = actionBuffers.ContinuousActions[1];
        rBody.AddForce(controlSignal * forceMultiplier);
        float distanceToTarget = Vector3.Distance(this.transform.localPosition, Target.localPosition);
        if(distanceToTarget < 1.42f)
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
 - Сделала Decision Requester и Behavior Parameters

![image](https://user-images.githubusercontent.com/57943773/197811747-c9c1814a-12c3-42ab-888c-8ebacfca6fa5.png)
 - Добавила файл конфигурации нейронной сети в проект, запустила работу ml-агена
![image](https://user-images.githubusercontent.com/57943773/197838002-6f59a7e3-7816-465a-a17f-31339012bae7.png)
 - Видео работы:
https://youtu.be/1BgSfBcaaPY

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
