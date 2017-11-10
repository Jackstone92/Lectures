# Data Modelling Part 2

---

# Advanced Querying
## **Sorting**
- MySQL sorts records in a result-set however it wants, without any guarantee of consistency
- Use `ORDER BY` keyword to sort rows in a result-set:
```SQL
SELECT id, firstname, lastname FROM Account
ORDER BY id DESC;
```
- Sort on multiple columns:
```SQL
SELECT firstname, lastname FROM Account
ORDER BY lastname, firstname ASC;
```
- Default sort order is ascending, with smallest values first (or case-insensitive a-z on character columns)

## **Table Joins**
- To fetch columns from multiple tables in a single **result-set**, use a table **JOIN**
- Tell the database where to join the tables - ie. which columns the tables have in common
- An `INNER JOIN` includes only rows with matches in both tables
- `LEFT` or `RIGHT` joins include all the rows from one table, and any matching rows from the other table
- For example:

Customer Table:
| id | firstname | lastname |
| --- | --- | --- |
| 0 | John | Smith |
| 1 | Maria | Gonzales |
| 2 | Abdul | Kahn |

Order Table:
| id | customer_id | eat_in |
| --- | --- | --- |
| 0 | 1 | 1 |
| 1 | 0 | 0 |

### INNER JOIN
```SQL
SELECT firstname, lastname, eat_in FROM Customer
INNER JOIN Order
ON Customer.id=Order.customer_id;
```

Results in:
| John | Smith | 0 |
| --- | --- | --- |
| Maria | Gonzales | 1 |

### LEFT JOIN
```SQL
SELECT firstname, lastname, eat_in FROM Customer
LEFT JOIN Order
ON Customer.id=Order.customer_id;
```

Results in:
| John | Smith | 0 |
| --- | --- | --- |
| Maria | Gonzales | 1 |
| Abdul | Kahn | NULL |

### Other SQL JOINS
- INNER JOIN
- LEFT JOIN
- RIGHT JOIN
- LEFT INCLUDING JOIN
- RIGHT INCLUDING JOIN
- OUTER INCLUDING JOIN
- OUTER EXCLUDING JOIN

### Joins for **Filtering Purposes**
- Use joins to filter data from one table based on the data in one or more other table
- Here, data from table 2 (MediaServe) isn't actually returned in the result-set
```SQL
SELECT id, username FROM Account
INNER JOIN MediaServe
  ON Account.id=MediaServe.account_id
WHERE MediaServe.img_url='someurl'
ORDER BY id ASC;
```
  - Get the id and usernames of Accounts that were served a specific image

### Joins to **Read Data from Multiple Tables**
- Use joins to combine fields (columns) from two or more tables in a single result-set
- Notice the use of **table aliases** here (a shorthand way to refer to a table)
```SQL
SELECT ms.id, m.image_url
FROM MediaServe ms
INNER JOIN Media m
  ON ms.media_id=m.id
WHERE ms.ts<'2017-10-26 12:00:00'
ORDER BY ms.id;
```
  - Get the serve id and URLs of images served before a certain date

# SQL Aliases
- SQL **aliases** are used to temporarily rename a table or a column heading
- Aliases can help make column names more readable
- **Column aliases** can help make reading the result-set more intuitive, and avoid ambiguity where fields in different tables share the same names
```SQL
SELECT ms.id, ms.ts AS when_served,
  fg.ts AS when_flucked
FROM MediaServe ms
INNER JOIN FluckGiven fg
  ON ms.id=fg.serve_id
ORDER BY ms.id;
```
  - When was an image served relative to when it was flucked?

# Read data from multiple tables
- Can also perform **multiple joins** to read data from 3 or more tables:
```SQL
SELECT fg.id AS fluck, a.username, fg.ts
FROM FluckGiven fg
INNER JOIN MediaServe ms
  ON ms.id=fg.serve_id
INNER JOIN Account a
  ON a.id=ms.account_id
WHERE ms.media_id=10;
```
  - Find out the fluck ids, flucker usernames and fluck times of a specific image

---

# Aggregate Functions
- Set of **built-in functions** available in MySQL
  - Perform calculations on sets of values
  - Return a single value
- Examples:
  - `AVG()` - Returns the average value
  - `COUNT()` - Returns the number of rows
  - `FIRST()` - Returns the first value
  - `LAST()` - Returns the last value
  - `MAX()` - Returns the largest value
  - `MIN()` - Returns the smallest value
  - `SUM()` - Returns the sum

- An example (from a music store schema):
```SQL
SELECT title, MAX(Album.price)
FROM Album;
```

## GROUP BY
- Aggregate functions are often used in conjunction with the `GROUP BY` clause
```SQL
SELECT firstname, lastname, COUNT(*) AS num_flucks
FROM FluckGiven fg
INNER JOIN MediaServe ms
  ON fg.serve_id=ms.id
INNER JOIN Account ac
  ON ms.account_id=ac.id
GROUP BY account_id;
```

## Nested Queries
- Aggregate functions may also be used in conjunction with **nested queries** (a query within a query)
```SQL
SELECT ms.id, ms.account_id
  (SELECT COUNT(*) FROM FluckGiven fg
    WHERE ms.id=fg.serve_id) AS num_flucks
FROM MediaServe ms
ORDER BY ms.id;
```

# Comparison Operators
- A variety of relational comparison operators can be used within SQL queries
```SQL
SELECT title, price
FROM Album
WHERE price >= 19.99 AND year < 1980;
```

```SQL
SELECT first_name, last_name
FROM Artist
WHERE band_id IS NULL;
```

## Full list:
| Name | Description |
| --- | --- |
| BETWEEN... AND... | Check whether a value is within a range of values |
| COALESCE() | Return the first non-NULL argument |
| = | Equal operator |
| <=> | NULL-safe equal to operator |
| > | Greater than operator |
| >= | Greater than or equal operator |
| GREATEST() | Return the largest argument |
| IN() | Check whether a value is within a set of values |
| INTERVAL() | Return the index of the argument that is less than the first argument |
| IS | Test a value against a boolean |
| IS NOT | Test a value against a boolean |
| IS NOT NULL | NOT NULL value test |
| IS NULL | NULL value test |
| ISNULL() | Test whether the argument is NULL |
| LEAST() | Return the smallest argument |
| < | Less than operator |
| <= | Less than or equal operator |
| LIKE | Simple pattern matching |
| NOT BETWEEN... AND... | Check whether a value is not within a range of values |
| !=, <> | Not equal operator |
| NOT IN() | Check whether a value is not within a set of values |
| NOT LIKE | Negation of simple pattern matching |
| STRCMP() | Compare two strings |


---

# MongoDB
## Basics
- **Open-source document-based** database management system
- Data *objects* represented by **documents**
- Related documents form a **collection**
- **Databases** house collections
- **No fixed structure** to the data in documents
- Mongo shell provides **interactive JS interface** to database
- Documents composed of **key-value pairs** (like JSON)
```javascript
var album = {
  _id: ObjectId("5099803df3f4948bd2f98391"), // _id is a Field (_id is always the unique identifier/primary key - automatically set when using 'insert')//
  title: "Imagine",
  released: new Date('Sep 9, 1971'),
  tracks: [ "Imagine", "Crippled Inside" ], // Values can be arrays //
  artist: { // Values can also be embedded documents //
    first: "John",
    last: "Lennon"
  }
};
```

## Relationships
- SQL-like joins are not possible, but data in different documents can be 'related' using **database references** (DBRefs)
```javascript
var album = {
  _id: ObjectId("5099803df3f4948bd2f98391"),
  title: "Imagine",
  released: new Date('Sep 9, 1971'),
  tracks: [ "Imagine", "Crippled Inside" ],
  artist: {
    "$ref": "artists",
    "$id": ObjectId("5126bc054aed4daf9e2ab772"),
    "$db": "musicstore" // Value is a reference to another document //
  }
};
```

## Creating Documents
From mongo shell...
- Documents inserted in a collection using mongo's `insert()` method
- If collection doesn't exist, it is created
```javascript
musicstore.albums.insert( // musicstore is Database, albums is Collection //
  {
    _id: ObjectId("5099803df3f4948bd2f98391"),
    title: "Imagine",
    released: new Date('Sep 9, 1971'),
    tracks: [ "Imagine", "Crippled Inside" ],
    artist: {
      first: "John",
      last: "Lennon"
    }
  }
);
```

## Reading Documents
From mongo shell...
- Documents can be queried using mongo's `find()` method
- **Query filters** or criteria can be specified
- **Cursor methods** can modify the way a query is executed
```javascript
musicstore.albums.find(
  { price: { $gt: 10.99 } }, // Criteria //
  { price: -1, title: 1 } // Projection (which fields to return) //
).limit(10); // Cursor modifier //
```

## Replica Sets: What?
- A **replica set** in MongoDB is a group of MongoDB processes that maintain the same data set
- May be distributed over multiple servers
- Consists of one **primary node (master)** and one or more **secondary nodes (slaves)**
- Master node handles **writes** while slaves synchronise with the master and may handle **reads**

## Replica Sets: Advantages
- Replication provides **redundancy** and increases **data availability**
- May improve **fault tolerance** and **read capacity**
