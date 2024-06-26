# Домашнее задание к занятию «Базы данных» Шарапат Виктор

### Легенда

Заказчик передал вам [файл в формате Excel](https://github.com/netology-code/sdb-homeworks/blob/main/resources/hw-12-1.xlsx), в котором сформирован отчёт. 

На основе этого отчёта нужно выполнить следующие задания.

### Задание 1

Опишите не менее семи таблиц, из которых состоит база данных:

- какие данные хранятся в этих таблицах;
- какой тип данных у столбцов в этих таблицах, если данные хранятся в PostgreSQL.

Приведите решение к следующему виду:

Сотрудники (

- идентификатор, первичный ключ, serial,
- фамилия varchar(50),
- ...
- идентификатор структурного подразделения, внешний ключ, integer).

### Решение 1
varchar(N) обозначает тип данных в базе данных, который представляет собой переменную длину строки, где N - это максимальное количество символов, которое это поле может содержать. Таким образом, varchar(N) позволяет хранить строку длиной до N символов.
tinyint - это тип данных, который представляет собой маленькое целочисленное значение, обычно с небольшим диапазоном значений. В зависимости от конкретной реализации SQL, tinyint может быть представлен различными способами 
(например, от -128 до 127 или от 0 до 255). tinyint часто используется для экономии памяти, когда вам необходимо хранить небольшие целочисленные значения.
employee_id - это название поля в таблице базы данных, которое, вероятно, идентифицирует уникального сотрудника или сотрудников.
date - это тип данных в SQL, который представляет собой дату в формате ГГГГ-ММ-ДД
numeric(6,2) - это тип данных, представляющий числовое значение с фиксированной точностью и масштабом. Точность указывает общее количество цифр, которые могут быть хранены, а масштаб указывает количество цифр справа от десятичной точки.


Сотрудники (
* employee_id, primary key 
* фамилия, varchar(20)
* имя, varchar(20)
* отчество, varchar(20)
* дата_найма, date
* оклад_id, foreign key, tinyint
* структурное_подразделение_id, foreign key, tinyint
* проект_id, foreign key, tinyint
* должность_id, foreign key, tinyint)
  

Оклады (
* оклад_id, primary key, tinyint
* оклад, numeric(6,2))
  

Должность (
* должность_id, primary key, tinyint
* должность, varchar(40))
  

Тип_подразделения (
* тип_подразделения_id, primary key, tinyint
* тип_подразделения, varchar(15))
  

Структурное_подразделение (
* структурное_подразделение_id, primary key, tinyint
* структурное_подразделение, varchar(50)
* адрес_филиала_id, foreign key, tinyint 
* тип_подразделения_id, foreign key, tinyint)
  

Адрес_филиала (
* адрес_филиала_id, primary key, tinyint
* адрес_филиала, varchar(100)
* город, foreign key, varchar(15))

Город_филиала (
* город_филиала_id, primary key, tinyint
* город, varchar(20))


Проект (
* проект_id, primary key, tinyint
* название_проекта, varchar(100))

## Дополнительные задания (со звёздочкой*)
Эти задания дополнительные, то есть не обязательные к выполнению, и никак не повлияют на получение вами зачёта по этому домашнему заданию. Вы можете их выполнить, если хотите глубже шире разобраться в материале.


### Задание 2*

Перечислите, какие, на ваш взгляд, в этой денормализованной таблице встречаются функциональные зависимости и какие правила вывода нужно применить, чтобы нормализовать данные.
