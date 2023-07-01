# 12.1 "Базы данных." - Дрибноход Давид

---
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

---

### Решение

**Сотрудники (employees)**
- `id` 					        int NOT NULL *PK autoincrement*
- `last_name` 			   varchar(200)
- `first_name` 			  varchar(200)
- `middle_name` 			 varchar(200)
- `hr_links_id`     int NOT NULL *FK hr_links.id*


**Должности (positions)**
- `id` 					        smallint NOT NULL *PK autoincrement*
- `description` 			 varchar(200)


**Подразделения (divisions)**
- `id` 					        smallint NOT NULL *PK autoincrement*
- `type` 			        enum('Группа','Отдел','Департамент')
- `description` 			 varchar(200)
 

**Проекты (projects)**
- `id`					         int NOT NULL *PK autoincrement*
- `customer_id` 			 int NOT NULL *FK customers.id*
- `description` 			 varchar(200)


**Клиенты (customers)**
- `id` 					        int NOT NULL *PK autoincrement*
- `company_name` 		 varchar(200)


**Распределение по проектам (teams)**
- `projects_id` 			 int NOT NULL *PK FK projects.id*
- `employees_id`			 int NOT NULL *PK FK employees.id*


**Адреса Филиалов (offices)**
- `id` 					        smallint NOT NULL *PK autoincrement*
- `region_id` 				  smallint NOT NULL *FK region.id*
- `city_id` 				    smallint NOT NULL *FK city.id*
- `address` 				    varchar(200)


**Регионы (region)**
- `id`  					       smallint NOT NULL *PK autoincrement*
- `name` 				       varchar(200)


**Города (city)**
- `id`  					       smallint NOT NULL *PK autoincrement*
- `name` 				       varchar(200)


**Информация о найме (hr_links)**
- `id` 					        int NOT NULL *PK autoincrement*
- `employees_id`			 int NOT NULL *FK employees.id*
- `startwork_date`  date
- `salary_value` 		 decimal
- `offices_id` 			  smallint NOT NULL *FK offices.id*
- `divisions_id` 		 smallint NOT NULL *FK divisions.id*
- `positions_id` 		 smallint NOT NULL *FK positions.id*
