# SQL    

### [Приклади з курсів](https://github.com/Svitlana-Kostromitina/SQL-Examples-from-courses/blob/main/README.md)

**SQL (Structured query language — мова структурованих запитів)** — Інформаційно-логічна мова, призначена для опису, зміни та вилучення даних, що зберігаються в реляційних базах даних.

**База даних (англ. database)** – сукупність даних, організованих відповідно до концепції, яка описує характеристику цих даних і взаємозв'язки між їх елементами. В загальному випадку база даних містить схеми, таблиці, подання, збережені процедури та інші об'єкти. Дані у базі організовують відповідно до моделі організації даних. Таким чином, сучасна база даних, крім самих даних, містить їх опис та може містити засоби для їх обробки.

Для управління базами даних створено програмні продукти, які є програмним забезпеченням баз даних.

**СУБД** - система управління базами даних.

**Система управління базами дааних (СУБД, СКБД англ. Database Management System, DBMS)** — набір взаємопов'язаних даних (база даних) і програм для доступу до цих даних[1]. Надає можливості створення, збереження, оновлення та пошуку інформації в базах даних з контролем доступу до даних.


**Реляційна база даних (Relational Database)** - це тип бази даних, яка зберігає дані у вигляді таблиць, що складаються з рядків та стовпців. Кожна таблиця в базі даних містить дані про конкретний тип об'єктів, наприклад, користувачів, продукти, замовлення тощо. Взаємозв'язки між таблицями можуть бути задані за допомогою зв'язків, які встановлюють зв'язки між різними таблицями за певними полями. Реляційні бази даних є одним з найбільш поширених типів баз даних і використовуються в багатьох сферах, включаючи банківський сектор, логістику, виробництво, медицину та інші.

**Сутності баз даних** - це об'єкти, які представляють реальні об'єкти або поняття, які потрібно зберігати та обробляти в базі даних. Наприклад, в базі даних для онлайн-магазину можуть бути сутності "клієнт", "товар", "замовлення" і т.д. Кожна сутність містить атрибути, що визначають її характеристики. Наприклад, у сутності "клієнт" можуть бути атрибути "ім'я", "прізвище", "адреса", "електронна пошта" і т.д. Кожна сутність має також ідентифікатор - унікальне поле, за яким можна ідентифікувати окремі записи цієї сутності в базі даних.

**Реляційна база** даних містить у собі набір таблиць, пов'язаних між собою. Вид зберігання даних визначається заданою структурою (схемою) бази даних і правилами її керування.


**Таблиця зберігає безпосередньо дані і складається з двох частин:**

-	Поле - вертикальний стовпець (він же колонка або атрибут таблиці);
-	Запис - горизонтальний рядок (або кортеж таблиці).

**Основні властивості поля таблиці:**

-	Ім'я - кожне поле має своє ім'я;
-	Зміст стовпців має бути унікальним;
-	Тип даних - текст, число, дата, час, валюта тощо.

 ## Види зв'язків у таблиці
    
**Зв'язок (relationship)** - це асоціація, що встановлюється між двома і більше сутностями.

-	**Один до одного (One-to-One)** - Кожен запис в одній таблиці пов'язаний з одним записом в іншій таблиці. Наприклад, таблиця "студенти" та таблиця "паспорти", де кожен студент має один паспорт, а кожен паспорт належить лише одному студенту.
-	**Один до багатьох (One-to-Many)** -Кожен запис в одній таблиці пов'язаний з багатьма записами в іншій таблиці. Наприклад, таблиця "замовлення" та таблиця "товари", де кожен замовлення може містити багато товарів, але кожен товар може бути включений тільки в одне замовлення.
-	**Багато до багатьох (Many-to-Many)** - Багато записів в одній таблиці пов'язані з багатьма записами в іншій таблиці, і навпаки. Для реалізації цього типу зв'язку потрібна додаткова таблиця, яка містить зв'язки між записами обох таблиць. Наприклад, таблиця "студенти" та таблиця "курси", де кожен студент може бути зареєстрований на багато курсів, і кожен курс може мати багато студентів.

Ці типи зв'язків допомагають організувати дані в базі даних та забезпечують їх цілісність та консистентність.

## Ключі в SQL

**Primary Key (Головний, Первинний ключ)** — це стовпець або комбінація стовпців, які однозначно ідентифікують запис у базі даних. Первинний ключ може мати лише унікальні значення, а не значення NULL, і в таблиці може бути тільки один первинний ключ. Головна роль первинного ключа — підтримувати цілісність БД.

_CREATE TABLE my_table (
id INT PRIMARY KEY,
name VARCHAR(50)
);_

**Foreign Key (Вторинний, Зовнішній ключ)** —це поле в таблиці бази даних, яке посилається на первинний ключ іншої таблиці. Цей механізм зв'язує дані між двома таблицями і забезпечує цілісність даних. Звичайно використовується в базах даних реляційної моделі. Фактично це зв'язок між таблицями, де вторинний ключ таблиці А вказує на первинний ключ таблиці В, що дозволяє виконувати операції з посиланнями на дані в обох таблицях.

_CREATE TABLE orders (
order_id INT PRIMARY KEY,
customer_id INT,
order_date DATE,
FOREIGN KEY (customer_id) REFERENCES customers(customer_id)
);_

**Unique Key (Унікальний ключ)** - це обмеження, яке застосовується до стовпця таблиці в реляційній базі даних і забезпечує унікальність значень в цьому стовпці. Це означає, що в стовпці не може бути двох однакових значень. Якщо спроба вставити запис з уже існуючим унікальним значенням виконується, база даних видасть помилку. Обмеження UNIQUE можна встановити як при створенні таблиці, так і пізніше змінити за допомогою оператора ALTER TABLE.

_CREATE TABLE my_table (
id INT,
name VARCHAR(50),
email VARCHAR(100) UNIQUE
);_


## Основний набір операцій SQL:

-	Створення баз даних;
-	Створення в базі даних;
-	Зміна структур нових таблиць;
-	Видалення таблиць;
-	Додавання в таблицю нових записів;
-	Зміна записів;
-	Видалення записів;
-	Вибірка записів з однієї або декількох таблиць відповідно до заданої умови.


## У SQL існує кілька типів даних, основні з яких наведені нижче:

**Числові типи даних:**

-	INTEGER - ціле число (INT - зберігає ціле число в діапазоні від -2147483648 до 2147483647)
-	BIGINT - довге ціле число (BIGINT - зберігає ціле число в діапазоні від -9223372036854775808 до 9223372036854775807)
-	FLOAT - число з плаваючою точкою (FLOAT(10, 2) - зберігає дійсне число з точністю до 2 знаків після коми)
-	DECIMAL - десяткове число

**Символьні типи даних:**
-	CHAR - фіксована довжина символьного рядка (CHAR(10) - зберігає рядок з 10 символів)
-	VARCHAR - змінна довжина символьного рядка (VARCHAR(255) - зберігає рядок з максимальною довжиною 255 символів)
-	TEXT - великий текст

**Дати та час:**
-	DATE – дата (DATE - зберігає дату у форматі "рік-місяць-день")
-	TIME – час (TIME - зберігає час у форматі "година:хвилина:секунда")
-	DATETIME - дата та час (DATETIME - зберігає дату та час у форматі "рік-місяць-день година:хвилина:секунда")

**Логічний тип даних:**
-	BOOLEAN - логічне значення (TRUE або FALSE)

## DML (Data Manipulation Language)

**DML (Data Manipulation Language)** - що означає мову маніпулювання даними. Це набір команд SQL для взаємодії з даними в таблицях бази даних, таких як додавання, видалення, оновлення та вибірка даних. Для виконання DML-операцій використовуються команди як **SELECT, INSERT, UPDATE та DELETE**. 

**SELECT** - це команда мови SQL, яка використовується для вибірки (запиту) даних з реляційної бази даних. Вона дозволяє вибирати певні стовпці таблиці чи комбінації стовпців з кількох таблиць, виконувати фільтрацію, сортування, групування та інші операції над даними. Синтаксис команди SELECT включає ключові слова SELECT, FROM, WHERE, GROUP BY, HAVING, ORDER BY, що дозволяє розширювати її функціональність.


**INSERT** використовується для додавання нових рядків у таблицю бази даних. Синтаксис команди INSERT виглядає наступним чином:

_INSERT INTO table_name (column1, column2, column3)_

_VALUES (value1, value2, value3)_

***Де:*** 

-	_table_name_ – назва таблиці;
-	_column1, column2, column3_ – назва стовпців таблиці;
-	_value1, value2, value3_ – значення, відповідних стовпців таблиці.


**UPDATE** - це операція мовою SQL, яка дозволяє оновити дані у таблиці бази даних. За допомогою команди UPDATE, можна змінити значення одного або декількох стовпців в одному або декількох рядках таблиці.

Наприклад, щоб оновити значення стовпця _name_ у таблиці _users_, використовуючи умову id=1, можна скористатися наступним запитом:

_UPDATE users_

_SET name = 'Alex'_

_WHERE id = 1_

Цей запит змінить ім'я користувача з _id=1_ на _Alex_.


**DELETE** - це команда мови SQL, яка використовується для видалення даних з таблиці в реляційній базі даних. Синтаксис команди DELETE виглядає наступним чином:

_DELETE FROM table_name WHERE condition_

Де _table_name_ - назва таблиці, з якої необхідно видалити дані, _condition_ - умова, за якою будуть вибрані рядки для видалення. Якщо умова не вказана, то видаляться всі рядки з таблиці.


Наприклад, якщо ми маємо таблицю _users_ з колонками _id_, _name_ та _age_, то для видалення рядка з певним _id_ ми можемо використати наступний запит:

_DELETE FROM users WHERE id = 1;_

Цей запит видалить рядок з таблиці _users_, де значення колонки _id_ дорівнює 1.


## Оператори які використовуються з WHERE:

- "=" перевірка на рівність;
- "<> або !="  перевірка на нерівність;
- "<"  перевірка на менше;
- ">" перевірка на більше;
- "<=" перевірка на менше або дорівнює;
- ">="  перевірка на більше або дорівнює;
- BETWEEN перевірка на те, чи належить значення до діапазону;
- LIKE перевірка на збіг з виразом;
- IN перевірка на те, чи належить значення до переліку значень;
- IS NULL перевірка на те, що значення є NULL;
- NOT оператор відмови, який змінює значення оператора на протилежне.
- AND використовується для того, щоб об'єднати дві або більше умов, що повинні бути виконані, щоб рядок даних відповідав запиту. Запит, який містить AND, поверне тільки ті рядки даних, які відповідають обом (або більше) умовам. Наприклад, SELECT * FROM customers WHERE city = 'Kyiv' AND age > 30; поверне всіх замовників, які живуть в Києві та мають більше 30 років;
- OR також використовується для об'єднання двох або більше умов, проте він поверне всі рядки даних, які відповідають принаймні одній з умов. Наприклад, SELECT * FROM customers WHERE city = 'Kyiv' OR age > 30; поверне всіх замовників, які живуть в Києві або мають більше 30 років.

## Вибірка унікальних даних DISTINCT

**DISTINCT** в мові запитів SQL використовується для вибірки унікальних значень зі стовпця або стовпців в таблиці бази даних. Він забезпечує те, що кожен запис вибірки буде містити лише одне значення для кожної вказаної колонки.

*Наприклад*, запит _SELECT DISTINCT city FROM customers_ поверне унікальні значення міст зі стовпця _"city"_ таблиці _"customers"_. Якщо в таблиці є декілька записів з однаковим значенням міста, то результат запиту буде містити лише одне таке значення.

Оператор DISTINCT може бути також використаний для вибірки унікальних значень з кількох стовпців. Наприклад, запит _SELECT DISTINCT city, country FROM customers _ поверне унікальні комбінації значень міст і країн зі стовпців "_city" і "country"_ таблиці _"customers"_.

## Сортування даних таблиці ORDER BY

Оператор **ORDER BY** використовується для сортування результатів запиту за певними полями. Він приймає список полів, за якими потрібно відсортувати результати, та напрямок сортування - за замовчуванням він сортує в порядку зростання **(ASC)**, але можна задати сортування за спаданням **(DESC)**.

_SELECT column1, column2, ..._

_FROM table_name_

_ORDER BY column1 ASC_


## Вибір певної кількості записів TOP

Оператор **TOP** використовується в SQL для вибору певної кількості записів з результатів запиту. Він може бути використаний з оператором SELECT для вибору перших N рядків з результатів запиту, де N - це число, яке ви хочете вибрати. 

Наприклад, якщо ви хочете вибрати тільки перші 10 рядків з таблиці, ви можете написати запит:

_SELECT TOP 10 * FROM table_name;_


## Об'єднання запитів оператором UNION та UNION ALL

Це оператори мови SQL, які дозволяють об'єднувати результати двох або більше запитів у єдиний результат. 
Оператор **UNION/ UNION ALL** об'єднує запити вертикально, тобто додає рядки результату одного запиту до рядків іншого запиту. Кожен запит повинен мати однакову кількість стовпців та типи даних кожного стовпця повинні відповідати одне одному. 

**Основна різниця** між UNION та UNION ALL полягає в тому, що UNION виключає дублікати, тоді як UNION ALL включає всі рядки з обох запитів, включаючи дублікати.

_SELECT column1, column2 FROM table1_          

_UNION_                                        

_SELECT column1, column2 FROM table2;_         

## З'єднання таблиць за допомогою JOIN

**JOIN** — операція з'єднання таблиць в SQL, яка сполучає таблиці в реляційній базі даних, утворюючи нову тимчасову таблицю, яку інколи називають «з'єднаною таблицею»
-	**INNER JOIN** - повертає лише ті рядки, які мають спільні значення в обох таблицях.
-	**LEFT JOIN** - повертає всі рядки з лівої таблиці, а також ті рядки з правої таблиці, які мають спільні значення. Якщо у правій таблиці немає спільних значень, то для цієї таблиці повернеться значення NULL.
-	**RIGHT JOIN** -симетричний LEFT JOIN - повертає всі рядки з правої таблиці, а також ті рядки з лівої таблиці, які мають спільні значення. Якщо у лівій таблиці немає спільних значень, то для цієї таблиці повернеться значення NULL.
-	**FULL OUTER JOIN** - повертає всі рядки з обох таблиць. Якщо у одній таблиці немає спільних значень, то для цієї таблиці повернеться значення NULL.
-	**CROSS JOIN** - Оператор перехресного з'єднання  виконує декартовий добуток між двома таблицями, тобто повертає комбінації кожного рядка з першої таблиці з кожним рядком з другої таблиці.


## Агрегатні функції

**Агрегатні функції** - є функціями, які застосовуються до множини значень і повертають єдине значення, яке є результатом обчислення. Вони використовуються для обчислення загальних статистичних даних з множини даних, таких як сума, середнє значення, максимум, мінімум, кількість тощо.

- COUNT - підраховує кількість рядків в стовпці.
- SUM - обчислює суму числових значень в стовпці.
- AVG - обчислює середнє значення числових значень в стовпці.
- MAX - знаходить максимальне значення в стовпці.
- MIN - знаходить мінімальне значення в стовпці.

Ці агрегатні функції можуть використовуватись в комбінації з операціями SELECT, GROUP BY, HAVING, ORDER BY та іншими операціями SQL. Вони дозволяють здійснювати складні операції обробки даних в базі даних.



## GROUP BY

Коли ви використовуєте агрегатні функції, зазвичай також потрібно створити речення GROUP BY. У реченні GROUP BY перелічуються всі поля, до яких не застосовується агрегатна функція. Якщо агрегатні функції застосовуються до всіх полів у запиті, речення GROUP BY створювати не потрібно.

Речення GROUP BY слідує безпосередньо після речення WHERE або FROM, якщо немає речення WHERE. У реченні GROUP BY поля перелічуються в тому самому порядку, що й в реченні SELECT.

GROUP BY зазвичай використовується разом з агрегатними функціями для отримання зведених даних з бази даних. Він також може бути корисним при аналізі даних та статистичних висновках.

## HAVING

Оператор HAVING в SQL використовується, коли потрібно відфільтрувати дані від використання агрегатних функцій, таких як MIN() і MAX(), SUM() і AVG() та COUNT().

Оператор WHERE не підтримує агрегатні функції. Крім того, перед оператором HAVING необхідно використовувати GROUP BY.

## DDL (Data Definition Language)

**DDL** використовується для створення, модифікації та видалення об'єктів баз даних, таких як таблиці, індекси, схеми тощо. До команд DDL належать, наприклад, CREATE, ALTER та DROP.

**CREATE DATABASE** використовується для створення нової бази даних. Він використовується тоді, коли потрібно створити нову базу даних, яка раніше не існувала. Крім того, він може бути використаний для відновлення резервної копії бази даних або для створення копії бази даних для тестування та експериментів.

Оператор CREATE DATABASE дозволяє вказати ім'я нової бази даних та додаткові параметри, такі як розмір та параметри зберігання даних. Наприклад, наступний SQL запит створить нову базу даних з ім'ям "mydatabase":  CREATE DATABASE mydatabase

Команда CREATE в SQL використовується для створення нових об'єктів в базі даних, таких як таблиці, індекси, процедури, функції та інші. Синтаксис команди залежить від типу об'єкту, який потрібно створити.

_CREATE TABLE table_name (_

   _column1 datatype1,_
   
   _column2 datatype2,_
   _column3 datatype3,_
   _...)_

**Де** _table_name_ - назва таблиці, _column1, column2, column3_ - назви стовпців, а _datatype1, datatype2, datatype3_ - типи даних для відповідних стовпців.

Залежно від типу об'єкту, який створюється, можуть бути також додаткові параметри та обмеження.

### Зміна типу даних колонки:

_ALTER TABLE table_name_

_ALTER COLUMN column_name NVARCHAR(100)_


**Де** _ALTER_ – ключове слово для зміни об'єкта бази даних;

_TABLE_ – ключове слово, яке вказує, що даний об’єкт таблиця;

_table_name_ – им’я таблиці;

_column_name_ – им’я колонки(поля), якої змінюється тип даних;

_NVARCHAR(100)_ – новий тип і розмір даних для колонки(поля) column_name


### Додавання колонки в таблицю:

_ALTER TABLE table_name_

_ADD COLUMN column_name_

**Де** _ADD_ – ключове слово, яке відповідає за додавання об’єкта;

### Видалення колонки з таблиці:

_ALTER TABLE table_name_

_DROP COLUMN column_name_

**Де** _DROP_ - ключове слово, яке відповідає за видалення об’єкта;

### Видалення таблиці:

_DROP TABLE table_name_

**Де** _DROP_ - ключове слово, яке відповідає за видалення об’єкта;

_TABLE_ – ключове слово, яке вказує, що даний об’єкт таблиця;

_table_name_ – им’я таблиці, що видаляється.





