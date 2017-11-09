# Data Modelling Part 1

---

# Origins of the Relational Model
- Conceived by **E.F. Dodd** (IBM, 1970)
- Based on **First-Order Predicate Logic** and **Set Theory**
- Example of first-order logic:
```javascript
Maxwell is a dog
// 'Maxwell' = subject
// 'is a dog' = predicate
Can be written in the form: D(x)
// 'D' = predicate
// 'x' = subject(variable)
```
- Another example of FOPL:
  - Maxwell is a dog | **D(x)**
  - A dog is an animal | **A(x)**
  - Maxwell is smelly | **S(x)**
- *Therefore...*
  - Maxwell is an animal | **∀x: A(x) -> D(x)**
  - Some dogs are smelly | **∃x: D(x) -> S(x)**

## Relational databases are also concerned with **objects** and their **properties**!
- They can be reduced to a set of **logical statements** about the **relationships** between objects (entities)
- They offer an approach to managing data using structure and language that is **consistent with FOPL**

## And sets?
- A **set** is a collection of zero or more **objects** (or elements)
```
eg. A = {}, B = {1, 2, 3}, C = {2, 3, 4}
```
- All objects in a set are **unique**
- A set is defined by the objects it contains
- In a relational database, a **table** is analogous to a **set**, and a **record** is analogous to an **object** in a set

## Before Relational Databases
- Data stored in **tab delimited files**
- These were text files with long lists of delimited values
- Difficult to retrieve sets of related data quickly
- Relational model designed to make this process much **simpler** and quicker
- Example of Tab Delimited Files:

| Entries | Name | QtyPizza | QtyBurger | QtyChips | EatIn | Cost |
| --- | --- | --- | --- | --- | --- | --- |
| Entry 1 | Abdul | 0 | 2 | 1 | 0 | 7.50 |
| Entry 2 | Ana | 1 | 0 | 1 | 1 | 8.25 |
| Entry 3 | Leah | 0 | 1 | 0 | 0 | 2.75 |

## Relational Model
- Data organised into **tables** ('relations') of **rows** and **columns**
- Rows are referred to as '**records**' and columns as **'fields'**
- Eg. for a 'Customer' *table name*, 'lastname' is a *field* and the row with id 1 is a *record*

| id | firstname | lastname |
| --- | --- | --- |
| 0 | Sheela | Begum |
| 1 | Nyambi | Wulubita |
| 2 | Steph | King |

# Integrity Constraints
**Very important in relational databases...**
- Sets of rules which help maintain **information integrity**
- i.e. its **accuracy**, **consistency** and **reliability**
- **MySQL** deals with 4 types of constraint:
  - Index constraints (PRIMARY KEY and UNIQUE)
  - Referential constraints (FOREIGN KEY)
  - Invalid data constraints (NOT NULL)
  - ENUM and SET constraints

# Primary Keys
- Provide a **unique identifier** for each record in a table
- Guarantees that every row is in some way unique
- Every table *should* have a field (or combination of fields) designated as its primary key
- Essentially the same as having **UNIQUE** and **NOT NULL** constraints applied
- Often an integer id field set to **AUTO_INCREMENT**

## Example: *Order* Table

| id | customer_id | eat_in | food_id |
| --- | --- | --- | --- |
| 0 | 1 | 1 | 0 |
| 1 | 0 | 0 | 1 |
| 2 | 2 | 0 | 0 |

- The id can be used to uniquely identify each row => PRIMARY KEYS

# Foreign Keys
- Causes column in one table to **reference** column in another table
- Creates relationship or **dependency** between the tables
- Can have **referential actions** applied to them

## Example: *Order* Table

| id | customer_id | eat_in | food_id |
| --- | --- | --- | --- |
| 0 | 1 | 1 | 0 |
| 1 | 0 | 0 | 1 |
| 2 | 2 | 0 | 0 |

-  *Customer_id* may be used as foreign key in a *Customer* table, and *food_id* in a *Food* table

## Design Patterns
- One-to-Many
- Many-to-Many

# Junction Table
- Has 2 or more fields that reference fields in 2 or more other tables
- Enables us to model a Many-to-Many association

## Associations
- "Each **Order** is associated with one or more **OrderLine**"
- "Each **OrderLine** is associated with one and only one **Order**"
- "Each **OrderLine** is associated with one and only one **Food**"

In database speak, we can say:
- "Order has a **One-to-Many** association with OrderLine"
- "OrderLine has a **Many-to-One** association with Food"

As a result:
- "Order has a **Many-to-Many** association with Food"

# Entity Relationship Diagram
- When designing or implementing a schema, it can be useful to refer to an **Entity Relationship (ER)** diagram

# Common Data Types
| Datatype | Description |
| --- | --- |
| INT, SMALLINT, TINYINT, etc. | **integer** values, fixed number of bytes |
| FLOAT | **floating point** numbers |
| DECIMAL(M,D) | **fixed point**, max digits = M, decimal places = D |
| CHAR(M) | **fixed length** strings, length = M |
| VARCHAR(M) | **variable length** strings, max length = M |
| TEXT, TINYTEXT, LONGTEXT, etc. | variable length strings, fixed maximum number of bytes |
| BLOB, MEDIUMBLOB, etc | binary large objects, fixed maximum bytes |
| DATE | date value (YYYY-MM-DD) |
| DATETIME | date and time value (YYYY-MM-DD HH:MM:SS) |
| TIMESTAMP | stores current date and time in UTC |


# Database Schema
- The **structure of the database**, defined in the formal language understood by the DBMS
- Essentially, it is a container for related objects (tables)
- The precise meaning varies between different DBMS's

# Database Management System (DBMS)
- Program (or collection of programs) designed to manage the **Creation**, **Retrieval**, **Updating** and **Deletion** of data in a database (CRUD operations)
- Common relational DBMS's include:
  - MySQL
  - PostgreSQL
  - Microsoft SQL Server
  - Oracle

# SQL (Structured Query Language)
- **The language understood by the MySQL** DBMS

# Using MySQL:
## Open MySQL Shell
- To open MySQL interactive shell from Igor:
```SQL
$ mysql -u USERNAME -p
```
- This starts mysql as you, prompting you for a password
- You can see existing schemas/databases with:
```MySql
$ show schemas;
$ show databases;
```

## SQL: Creating Schemas
- We will be using the MySQL DBMS (v5.5)
- To **create a new database** in MySQL:
```SQL
> CREATE DATABASE database_name;
> CREATE SCHEMA database_name;
```

## SQL: Creating Tables
- **Create a table**:
```SQL
> CREATE TABLE table_name (field definitions);
```
- For example:
```SQL
CREATE TABLE FOOD (
  id INT AUTO_INCREMENT,
  name VARCHAR(50),
  price DECIMAL(5, 2) unsigned,
  PRIMARY KEY(id)
);
```

## SQL: Insert Single Record
- **Insert a record** into a table:
```SQL
INSERT INTO FOOD
VALUES (NULL, 'Pizza', 6.25);
```
- Or:
```SQL
INSERT INTO FOOD (name, price)
VALUES ('Pizza', 6.25);
```
- MySQL variation:
```SQL
INSERT INTO FOOD (name, price) SET
'Pizza' = 6.25;
```

## SQL: Insert Multiple Records
- **Insert multiple records** into a table:
```SQL
INSERT INTO FOOD VALUES
(NULL, 'Pizza', 6.25),
(NULL, 'Chips', 2.00);
```
- Or:
```SQL
INSERT INTO FOOD (name, price)
VALUES
('Pizza', 6.25),
('Chips', 2.00);
```

## SQL: Define Foreign Key
- Make field reference primary key field in another table
- Define a **foreign key**:
```SQL
CREATE TABLE OrderLine (
  id INT AUTO_INCREMENT,
  quantity TINYINT unsigned,
  FOREIGN KEY(food_id)
    REFERENCES Food(id)
  FOREIGN KEY(customer_id)
    REFERENCES Customer(id)
);
```
