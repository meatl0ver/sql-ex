# sql-ex
Решение задач https://www.sql-ex.ru/

### Краткая информация о базе данных "Компьютерная фирма" 

(задачи 1-13,15-28,35,40,41,58,65) 

Схема БД состоит из четырех таблиц: 
* Product(maker, model, type) 
* PC(code, model, speed, ram, hd, cd, price) 
* Laptop(code, model, speed, ram, hd, price, screen) 
* Printer(code, model, color, type, price) 

Таблица **Product** представляет производителя (maker), номер модели (model) и тип ('PC' - ПК, 'Laptop' - ПК-блокнот или 'Printer' - принтер). Предполагается, что номера моделей в таблице Product уникальны для всех производителей и типов продуктов. 

В таблице **PC** для каждого ПК, однозначно определяемого уникальным кодом – code, указаны модель – model (внешний ключ к таблице Product), скорость - speed (процессора в мегагерцах), объем памяти - ram (в мегабайтах), размер диска - hd (в гигабайтах), скорость считывающего устройства - cd (например, '4x') и цена - price (в долларах).

Таблица **Laptop** аналогична таблице РС за исключением того, что вместо скорости CD содержит размер экрана -screen (в дюймах). 

В таблице **Printer** для каждой модели принтера указывается, является ли он цветным - color ('y', если цветной), тип принтера - type (лазерный – 'Laser', струйный – 'Jet' или матричный – 'Matrix') и цена - price.
***
### Краткая информация о базе данных "Корабли" 

(задачи 14,31-34,36-39,42-57)

Рассматривается БД кораблей, участвовавших во второй мировой войне. Имеются следующие отношения:
* Classes (class, type, country, numGuns, bore, displacement)
* Ships (name, class, launched)
* Battles (name, date)
* Outcomes (ship, battle, result)


Корабли в «классах» построены по одному и тому же проекту, и классу присваивается либо имя первого корабля, построенного по данному проекту, либо названию класса дается имя проекта, которое не совпадает ни с одним из кораблей в БД. Корабль, давший название классу, называется головным.

Отношение **Classes** содержит имя класса, тип (bb для боевого (линейного) корабля или bc для боевого крейсера), страну, в которой построен корабль, число главных орудий, калибр орудий (диаметр ствола орудия в дюймах) и водоизмещение ( вес в тоннах). 

В отношении **Ships** записаны название корабля, имя его класса и год спуска на воду. 

В отношение **Battles** включены название и дата битвы, в которой участвовали корабли, а в отношении **Outcomes** – результат участия данного корабля в битве (потоплен-sunk, поврежден - damaged или невредим - OK).

###### Замечания. 

1) В отношение Outcomes могут входить корабли, отсутствующие в отношении Ships.
2) Потопленный корабль в последующих битвах участия не принимает.


***
### Краткая информация о базе данных "Фирма вторсырья" 

(задачи 29,30,59-62,64) 

Фирма имеет несколько пунктов приема вторсырья. Каждый пункт получает деньги для их выдачи сдатчикам вторсырья. Сведения о получении денег на пунктах приема записываются в таблицу: **Income_o(point, date, inc)**

Первичным ключом является (point, date). При этом в столбец date записывается только дата (без времени), т.е. прием денег (inc) на каждом пункте производится не чаще одного раза в день. 

Сведения о выдаче денег сдатчикам вторсырья записываются в таблицу:
**Outcome_o(point, date, out)**

В этой таблице также первичный ключ (point, date) гарантирует отчетность каждого пункта о выданных деньгах (out) не чаще одного раза в день.


В случае, когда приход и расход денег может фиксироваться несколько раз в день, используется другая схема с таблицами, имеющими первичный ключ code:

**Income(code, point, date, inc)**

**Outcome(code, point, date, out)**

Здесь также значения столбца date не содержат времени.


***
### Краткая информация о базе данных "Аэрофлот"

(задачи 63,65-68)

Схема БД состоит из четырех отношений:
* Company (ID_comp, name)
* Trip(trip_no, ID_comp, plane, town_from, town_to, time_out, time_in)
* Passenger(ID_psg, name)
* Pass_in_trip(trip_no, date, ID_psg, place)

Таблица **Company** содержит идентификатор и название компании, осуществляющей перевозку пассажиров.

Таблица **Trip** содержит информацию о рейсах: номер рейса, идентификатор компании, тип самолета, город отправления, город прибытия, время отправления и время прибытия. Таблица Passenger содержит идентификатор и имя пассажира. 

Таблица **Pass_in_trip** содержит информацию о полетах: номер рейса, дата вылета (день), идентификатор пассажира и место, на котором он сидел во время полета. 

При этом следует иметь в виду, что
- рейсы выполняются ежедневно, а длительность полета любого рейса менее суток; town_from <> town_to;
- время и дата учитывается относительно одного часового пояса;
- время отправления и прибытия указывается с точностью до минуты;
- среди пассажиров могут быть однофамильцы (одинаковые значения поля name, например, Bruce Willis);
- номер места в салоне – это число с буквой; число определяет номер ряда, буква (a – d) – место в ряду слева направо в алфавитном порядке;
- связи и ограничения показаны на схеме данных.


***
