# Лайфхакер

Лайфхакер — есть контент-сайт с «инструментами и советами, повышающими человеческую продуктивность». 
Его дневная аудитория на март 2014 — **300К**.
Давайте умножим и округлим это число на три — **1М** — именно столько я считаю приходит на сайт в августе 2016: этот вывод я сделал исходя из счётчика популярности материалов, размещённых на сайте.



Обслуживать **миллион** активных пользователей — задача не из лёгких.

Начинать тестирование необходимо с сети. 
Я могу предположить, что сервера находятся где-то в Германии или Нидерландах, потому что пинг в основном стабильный.
Ниже привожу подтверждение:


<img src="https://pp.vk.me/c636227/v636227043/2430b/UCaOdYzn-LE.jpg">



Но проблема не в качестве соединения, а в их количестве.


<img src="https://pp.vk.me/c636227/v636227043/24301/gkvZAu5Fk9c.jpg">



Больше **двадцати** открытых соединений для контент-сайта — много.
Причём *некоторые функции* дублируются: например, на Лайфхакере для аналитики используют одновременно и *Google Analytics* и *Яндекс.Метрику*

#### Про безопастность.

Не секрет, что http работает быстрее, чем https. Моё мнение, что для такого сайта, как Лайфхакер, https — это оверкил, в связи с тем, что на нём не реализовано то количество необходимых функциональностей, которые требуют безопасного протокола соединения. 



*Именно поэтому возвращение на http может дать неплохой буст в производительности ресурса.*

## Поговорим о графике.

*Пользователи мобильных телефонов будут страдать.*



Самый популярный тариф МТС — Smart — даёт **3гб** трафика за **450₽/мес** — с другими операторами тройки всё примерно так же.
МТС, предлагая пользователю 3000 мегабайт, расчитывает на то, что каждый день он будет использовать
3000 / 30 = *100 мегабайт.*

При первой отрисовке браузер скачает **~15мб растра**, гифок и другого ненужного ширпотреба.


То есть 15 / 100 — **шестую часть **дневной нормы пользователя. Это можно оптимизировать. Это нужно оптимизировать.



Графика не адаптивная — грузятся изображения **1600x800**, как для десктопов, так и для мобильных девайсов.  
Мы можем, однако, предположить, что Лайфакеру может быть не выгодно хранить у себя на серверах **.5x** версии картинок.
Чтобы пользователь был рад, Лайфхакеру, в идеале, надо хранить три версии: **.5x**,**1x** & **2x** *(retina devices).*


*У Лайфхакера подключён cdn on.the.io — я не думаю, что для этого сервиса это какая-то большая проблема: они как раз предоставляют услуги хранения картинок под разные DPI.*



## Минификация и обфускация

На странице подключёно **60 скриптов**

<img src="https://pp.vk.me/c636227/v636227043/24343/EgghJ5_Gn1A.jpg">

Образовывается некоторая солянка из кода, потому что что-то из этого минифицировано, как, например, **24 плагина** для jQuery. Что-то просто написано руками и не обфусцировано. 

*Для решения этой задачи есть пециальные инструменты: Webpack & Gulp. Лучше использовать их для сборки проекта, потому что 60 скриптов можно с лёгкостью собрать в один бандл.*



## Шрифты

Разработчики Лайфхакера хотят видеть у себя на сайте два шрифта: Open Sans & Roboto. Ну ладно, но проблема в том, что пока они не загрузились, у пользователя пустой блок и нет этих самых маркетинговых заголовков, за которыми люди заходят на сайт.



<img src="https://pp.vk.me/c636227/v636227043/24354/fEuJsF-EJhQ.jpg">

