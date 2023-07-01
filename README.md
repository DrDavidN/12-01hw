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
 - `id` 					int NOT NULL *PK autoincrement*
 - `fullname` 			varchar(200)
 - `hr_links_id`    int NOT NULL *FK hr_links.id*


**Должности (positions)**
 - `id` 					smallint NOT NULL *PK autoincrement*
 - `description` 				varchar(200)


**Подразделения (divisions)**
 - `id` 					smallint NOT NULL *PK autoincrement*
 - `type` 			enum('Группа','Отдел','Департамент')
 - `description` 				varchar(200)
 

**Проекты (projects)**
 - `id`					int NOT NULL *PK autoincrement*
 - `customer_id` 			int NOT NULL *FK customers.id*
 - `description` 				varchar(200)


**Клиенты (customers)**
 - `id` 					int NOT NULL *PK autoincrement*
 - `company_name` 			varchar(200)


**Распределение по проектам (teams)**
 - `id` 					int NOT NULL *PK autoincrement*
 - `projects_id` 			int NOT NULL *FK projects.id*
 - `employees_id`				int NOT NULL *FK employees.id*

   
**Филиалы (offices)**
 - `id` 					smallint NOT NULL *PK autoincrement*
 - `region` 				varchar(200)
 - `city` 				varchar(200)
 - `address` 				varchar(200)


**Информация о найме (hr_links)**
 - `id` 					int NOT NULL *PK autoincrement*
 - `employees_id`				int NOT NULL *FK employees.id*
 - `startwork_date` 			date
 - `salary_value` 		decimal
 - `offices_id` 			smallint NOT NULL *FK offices.id*
 - `divisions_id` 				smallint NOT NULL *FK divisions.id*
 - `positions_id` 				smallint NOT NULL *FK positions.id*
