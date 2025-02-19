# Лабораторная работа №2. Паттерн «Наблюдатель»

На оценку «удовлетворительно» необходимо набрать 50 баллов.

На оценку «хорошо» необходимо набрать 120 баллов.

На оценку «отлично» необходимо набрать 180 баллов.

## Задание 1 -- Отображение полной статистической информации -- 20 баллов

Текущая реализация программы Weather Station отображает
**статистические** данные только о температуре. Доработайте программу
так, чтобы аналогичная информация отображалась о влажности и давлении.
Приложите усилия для устранения дублирования кода, чтобы при появлении
нового типа датчиков было легче рассчитать и отобразить по ним
статистику.

## Задание 2 -- Безопасное уведомление наблюдателей -- 10 баллов

В приложении Weather Station работа метода NotifyObservers может
привести к неопределенному поведению, если из метода Update наблюдатель
выполнит удаление себя из списка наблюдателей. Придумайте и реализуйте
решение для данной проблемы.

Напишите модульный тест для данного сценария.

## Задание 3 -- Приоритеты наблюдателей -- 30 баллов

В приложении Weather Station порядок оповещения наблюдателей заранее
неизвестен. Доработайте приложение таким образом, чтобы при регистрации
наблюдателя можно было задать его приоритет в виде целого числа.
Наблюдатели с более высоким приоритетом должны получать оповещения от
субъекта раньше, чем наблюдатели с более низким приоритетом.

Напишите модульный тест для данного функционала.

## Задание 4 -- Наблюдение за несколькими субъектами -- 20 баллов

От заказчика поступил запрос на разработку приложения Weather Station
Duo, предназначенного для работы с новейшими устройствами, имеющими 2
метеостанции. Такие устройства позволяют один набор датчиков разместить
внутри помещения, а другой - снаружи. Соответственно, в такой программе
существуют 2 объекта WeatherData.

Индикаторы в программе должны стать продвинутыми -- теперь каждый
индикатор в такой программе отображает показатели сразу с двух станций
(in и out). Придумайте решение, позволяющее наблюдателю узнать, от
какого субъекта было получено уведомление.

Напишите модульный тест для данного функционала.

## Задание 5 -- Слежение за ветром -- 20 баллов

На основе программы Weather Station разработайте приложение Weather
Station Pro, предназначенное для работы с Pro-версией метеостанции,
оснащенной двумя дополнительными датчиками, сообщающими о скорости ветра
(м/с) и его направлении (в градусах, где 0 -- север, 90-восток, 180-юг,
270-запад). Придумайте, какие особенности следует учесть в реализации
статистического индикатора, чтобы обеспечить корректный расчет среднего
направления ветра.

## Задание 6 -- Слежение за ветром (Duo edition) -- 20 баллов

Заказчик не дремлет и захотел программу Weather Station Pro Duo, в
которой метеостанция, следящая за погодой вне помещения, заменена на
Pro-версию. Метеостанция, следящая за погодой внутри, осталась прежней,
т.к. внутри помещений ветра нет, что позволило снизить себестоимость
изделия. Индикаторы Duo-версии также обновились -- сведения о погоде
снаружи помещения включают в себя данные о ветре и направлении.

## Задание 7 -- Подписка лишь на интересующие события -- 40 баллов

От пользователей программы Weather Station Pro, использующих
метеостанцию во время зимней рыбалки, поступил запрос на повышение
энергоэффективности устройства, чтобы их аккумуляторной батареи хватало
на большее время.

В ходе разбора ситуации выяснилось, что пользователям нужен упрощенный
тип индикатора, отображающий лишь текущую температуру и атмосферное
давление, в то время как основной расход аккумулятора происходил из-за
слишком частой обработки уведомлений, связанных с изменениями
направления и силы ветра. Рыбакам зимой не важно, откуда дует ветер,
важно не засидеться на морозе ниже критической отметки, а также следить
за атмосферным давлением, т.к. поведение некоторых рыб зависит[^1] от
данного параметра.

Реализуйте возможность наблюдателю указывать тип интересующего их
изменения. При этом один и тот же наблюдатель должен иметь возможность
подписаться на несколько различных типов событий (например, несколько
раз зарегистрировав себя подписчиком разных типов событий), а также
динамически отписываться от событий, в которых он больше не
заинтересован.

TODO (на будущее): кроме weather station сделать другой набор
observable-observer (например, кот и мышь и собака). Интерфейс и базовая
реализация observable должны быть универсальными для использования как
метеостанцией, так и животными.

## Задание 8 -- Реализация паттерна Observer с использованием сигналов и слотов -- 50 баллов

Ознакомьтесь с возможностями библиотеки boost.signals2.
<http://www.boost.org/doc/libs/1_60_0/doc/html/signals2.html>

Разработайте версию программы Weather Station Pro Duo, с использованием
данной библиотеки. Для класса WeatherData напишите модульные тесты.

[^1]: Автор не является ни биологом, ни рыболовом-любителем, поэтому
    может ошибаться. Предположим, что во Вселенной, в которой есть
    необходимость в программе Weather Station Pro, существуют рыбы,
    чувствительные к изменению атмосферного давления.
