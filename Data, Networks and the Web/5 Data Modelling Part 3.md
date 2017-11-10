# Data Modelling Part 3

---

# What is NoSQL?
- **Non-SQL** or **non-relational** database technologies
- Aka, **Not Only SQL**, to emphasise the fact that some non-relational DBMS support SQL-like query languages
- Increasingly used by **big data** and **real-time web apps**

# Types of NoSQL Databases
- Column
- Key-value
- Document
- Graph
- Multi-model

## Examples
- CouchDB
- Redis
- Cassandra
- Neo4j
- MongoDB
- Membase
- Riak
- Google BigTable
- Apache HBASE

# Recap Relational Model
- Data organised into **2D tables** (relations) of related data
- Each row can be considered a unique instance of a type of **object**
- Each column (field) has a well-defined data **type**
- Data is highly **structured**

| ean | title | artist_id | genre | year | price |
| --- | --- | --- | --- | --- | --- |
| 00345781 | Uprising | 1 | reggae | 1974 | 12.99 |
| 00338271 | London Calling | 12 | pop | 2002 | 9.99 |
| 00384628 | Stand Up | 23 | jazz | 1948 | 21.50 |
| 13028723 | Boom Boom | 8 | ska | 1969 | 8.75 |

## Row-Based Storage: Good For...
- Relational way of representing data exists only in **theory**
- In practice, data needs to be **serialised** for storage
- In RDBMS, rows generally serialised by **row**:
  - 00345781, Uprising, 1, reggae, 1974, 12.99;
- Efficient for retrieving entire rows (ie. to retrieve a specific **object**) as each row is likely to be in the same disk block

## Row-Based Storage: Drawbacks
- Row-based data storage is inefficient for performing operations on a **whole data set**
- For example:
  - To fetch **all** albums within a certain price range requires me to search through the entire data set
  - May require **multiple disk operations** (multiple seeks) as all records unlikely to fit in a single block

## Database Indexes
Workaround?
- **Database indexes** can be used to speed up the retrieval of data in a relational database, at the cost of extra writes and storage space
- Consist of **copies** of select columns of data from a table
```SQL
CREATE TABLE Artist (
  id INT AUTO_INCREMENT,
  firstname VARCHAR(25),
  lastname VARCHAR(25),
  PRIMARY KEY(id),
  INDEX(UPPER(lastname))
);
```
  - creates an index from the lastname field; stores the data uppercase; ordered; with a pointer to relevant row in Artist table

## Column-Based Data Stores
- Seem to store data in related rows, but actually serialise the data into columns
- Allow much faster querying and processing of data while storing data that is somewhat related
- More easily distributed
- May be relational or not
- For example:
  'Bob', 'John', 'Barry';
  'Marley', 'Lennon', 'White';
- **Examples**: Cassandra, Druid

# Types of Database Query
- We can loosely separate queries into 2 groups:
- **Transactional**
  - Retrieve or modify individual records
    - Queries often triggered by user action
    - ACID properties may be important
    - Read/write
- **Analytical**
  - Reporting
    - Deriving new information from existing data
    - Queries run on many records
    - ACID properties often not important
    - Mainly read
- Generally speaking, we could say that:
  - **Transactional** suits row-based data store types
  - **Analytical** suits column-based data store types

# Big Data!
- **Big Data** refers to large volumes of data, or complex data, that cannot be dealt with using traditional processing applications
- In relational database models, data is stored in a very organised, **structured** way...
- ...with the drawback that performance decreases as the volume of data increases
- Not a sufficiently **scalable** solution for big data!
- NoSQL achieves higher performance for data of a massive scale, because it is **unstructured**
- It is designed for **distributed** storage and processing
- Lends itself better to **horizontal-scaling** (ie. multiple servers across different countries)

## In short
- For some operations, some data store types may be more efficient than the relational model, which mainly uses row-based storage
- Which type of data store type for the job depends on what **type of queries** will be run on the data...
- ...and also **how much data** is being stored!

# **Key-Value** Data Stores
- A data storage paradigm for storing and retrieving data as associative arrays (aka **dictionaries** or **hash tables**)
- Dictionaries contain collections of objects, or records, which in turn have many different fields within them, each containing data
- Records are stored and retrieved using a key that uniquely identifies the record
- Example of a dictionary:

| Key | Value |
| --- | --- |
| ean | 00347245 |
| title | Natty Dread |
| price | 12.99 |
| year | 1969 |
| genre | ska |

- Unlike the Relational Database Model, **structure is not predefined**
- Data treated as **single collection of records**
- It's possible to have **different fields for every record**
- This can **save space** (no empty fields/placeholders)
- Example of collection:

| record123_ean | 00347245 |
| --- | --- |
| record123_title | Natty Dread |
| record123_price | 12.99 |
| record435_year | 1969 |
| record435_genre | ska |
| record435_title | Boom Boom |


# **Document** Databases
- Subclass of key-value database
- **Keys** are mapped to **documents**
- Documents consist of **attributes**
- Attributes are **name/type value pairs** and can be **nested**
- Documents may be organised in **collections**
```javascript
Document A {
  ean: 00347245,
  title: 'Uprising',
  year: 1974,
  price: 12.99
};

Document B {
  name: {
    first: 'Bob',
    last: 'Marley'
  },
  living: false
};
```
- Looks a lot like **JSON**
- Some document DBMS do store their data in the JSON format (eg. CouchDB, RavenDB)
- Some may use **XML** (eg. eXistDB, MarkLogic)
- MongoDB uses a variant: **BSON** that's able to perform **binary serialisation**

# **Graph** Databases
Based on graph theory and consisting of:
- **Nodes**: unique entities (ie. an album, artist or customer)
- **Properties**: information associated with nodes (expressed as key/value pairs)
- **Edges**: lines connecting nodes, with unique id and properties
- Excellent for **analysing relationships** between nodes and **pattern finding** (ie. applications in **data mining**)
- Great for social network and retail marketing related data
- Examples: Neo4j, OrientDB

# Multi-Model
- **Polyglot persistence** refers to the use of multiple data storage technologies within the same project for different kinds of data
- Leads to more complicated deployment, more frequent upgrades, data consistency and duplication issues
- Solution: Multi-model database provides a single backend that supports multiple data models
- Examples: FoundationDB, ArangoDB

# Summary
- The efficiency of the model is relative to the type and volume of data, and the type of query (ie. **transactional**/**analytical**)
- **Relational** databases for structured, tabular data
- **Document** databases for unstructured, object-like data
- **Key/value** databases for hash tables
- **Graph** databases for highly linked referential data


---

# Python
- Among the most popular and widely used programming languages
- Large organisations often use python (Google, Yahoo!, CERN, NASA) and conduct programming interviews with python as an option
- Python can be used for scientific computing (numpy, scipy, matplotlib) as well as machine learning (scikit-learn)
- Often used for educational purposes as a first language

## Why Python?
- **General-purpose**, high-level programming language
- Designed emphasising **readability**
- **Easy** to learn
- **Syntax** allows programmers to express concepts with fewer lines of code (eg. compared to C)
- Large and comprehensive standard library
- Supports **object-oriented** programming
- Primary compilers, IDE's and many libraries **open-source**

## Running Python Code
- **Option 1**: Execute python code from a Python interpreter
  - Invoke the Python interpreter from a terminal/Unix shell:
```python
$ python
```
  - Type code...ie. use the built-in function `print` to output text:
```python
>>> print("Hellooo!")
```
- **Option 2**: Write a Python program in any plain text or code editor and save with **.py** extension (ie. hello.py)
  - Run the .py file from terminal:
```python
$ python hello.py
```

## Indentation
- **Python is strict on indentation!**
  - Whitespace indentation used to delimit blocks of code
  - No "start/end" or curly braces to indicate where function or block of code starts or ends
```python
def fib(n):
  print("n = ", n)
  if n > 1:
    return n * fib(n-1)
  else:
    print("end of the line")
  return 1
```

## Variables and Types
- A **variable** is a **name** (identifier) that is associated with a **value**
- Certain keywords are reserved and cannot be used as identifiers in python (eg. and, not, with, if, else, false)...
```python
str string_w = "foo" # String
int int_x = 1 # Integer
bool bool_y = True # Boolean
float float_z = 1.0 # Float
```
- Python is **dynamically typed** (types are implicit at point of assignment, and names may be bound to different objects over the duration of a program)
- Python is **strongly typed** (you cannot coerce a type mutation implicitly... a variable name may only be reassigned to an object of another type)
```python
w = "3"
x = 1
y = w + x # TypeError!
w = int(w) # w reassigned int value
y = w + x # no error
```

## Operators
- An **operator** is a symbol that represents an operation that may be performed on one or more **operands**
- The **+** symbol represents the operation of addition
- An operand is a value that a given operator is applied to (such as 2 and 3 in the expression 2+3)
- Python provides the arithmetic operators: **+**, **-**, **/**, __*__, **//**, **%**, __**__
  - exponent use __**__
  - for example `ten_squared  = 10 ** 2`

## Control Statements
- In python, control statements are defined within indented blocks
```python
if a < b:
  print(str(a) + " is less than " + str(b))
elif a == b:
  print(str(a) + " is equal to " + str(b))
else:
  print(str(a) + " is greater than " + str(b)) # If using + to concatenate (join) strings, you need to convert a non-string variable to a string
```

## Iteration Statements
- Used to loop through (repeat) a section of code **for** a specific number of cycles, or **while** some condition evaluates True
- For example, a **while** loop could look like this:
```python
secret_number = 10
guess = 1
# Do something while guess is not equal to secret_number...
while guess != secret_number :
  # Code to repeat while above condition is true
  guess = int( input( "Guess the secret number: " ) )
# This will happen only when condition is false
print( "You guessed correct!" )
```
- And a **for** loop could look like this:
```python
# i is a `pseudo­-variable' which exists while this statement # executes
for i in range(0, 5):
  print( i )
```
- It is also easy to **iterate through list elements** using a for loop:
```python
# item is another pseudo­-variable which takes the value of
# the current list element
for item in my_list:
  print(item)

# or dictionary items!
for k, v in my_dict.items():
  print(k, v)
```

## Built-in Data Structures
- Python has several built-in **data structures**
- They allow us to group together related values in a single variable
- **Lists** are for a **mutable** sequence of comma-separated values
- **Dictionaries** are unordered sets of **key/value pairs** with the requirement that the keys are unique
- **Tuples** are for an **immutable** sequence of comma-separated values
- **Sets** are for an unordered collection of unique values
```python
list_a = [1, 2, 3, "foo", list_b] # Duplicates allowed!
list_a[3] = "bar" # Mutable!
tup_a = (1, 2, 3)
dict_a = { "name": "pie and peas", "price": 6.50 }
set_a = { "carrots", "apples", "pears" } # No duplicates allowed!
```

## Function Definitions
- A **function** is a block of organised, re-useable code that performs a specific action
- In Python, a user-defined function begins with the keyword **def** followed by the function name and paretheses
- Any input parameters or arguments are placed in the parentheses
```python
def fib(n):
  print("N = ", n)
  if n > 1:
    return n * fib(n-1)
  else:
    print("end of the line")
  return 1
```
- A function definition is an executable statement:
```python
>>> fib(5)
```

## Modules
- A **module** is a file containing Python definitions and statements
- Many open-source modules are available for different purposes
- For list of available modules, run `help() -> modules` in Python shell
- To use all or part of a module, you **import** it
- You can import definitions to current **namespace** using **from**
- You can import modules or group definitions under an **alias**
```python
# import
import random
from fibo import fib
import numpy as np

# use
random.random()
fib(5)
np.arange(10)
```

## Coding Style
- Try to observe the **style conventions** outlied in **PEP 8**
- Most noteworthy:
  - Use **lower case** with **underscores** for **variable** and **function names**
  - Use **CamelCase** for **class names**
  - Use **4 spaces** per indentation level

# Python Practice: **Task 1**
- Let's imagine we are developing the logic for the Catflucks app...
- One of the requirements is to **serve random** image from a database
- In Task 1, write code to do this, but faking the backend...
```python
# import random module from Python standard library
import random
# define a list of image urls (i.e. list of strings)
image_url_list = ['http://image1', 'http://image2', 'http://image3']
# put a random element from imgs in a served_img variable
served_img = random.choice(image_url_list)
# output the value of served_img
print(served_img)
```

# Python Practice: **Task 2**
- The next requirement is to **allow a user to fluck the image**
- We'll fake this using the **input()** function
```python
# ask if user wants to fluck image
answer = bool(input("Do you want to fluck an image? "))
# if they said yes, output a message...
if answer == True:
  print("Image flucking will commence shortly...")
# else, output a different message...
else:
  print("That's a shame... maybe come back later?")
```

# Python Practice: **Task 3**
- In this task, use a different type of data structure to associate number of flucks with images
- If the user flucks, update the value
- Repeat the process after each user response
- Push results to new branch in group-work
```git
git branch python-practice
git checkout python-practice
```

```python
import random

image_url_dictionary = {
  "http://image1": 0,
  "http://image2": 0,
  "http://image3": 0
}

answer = bool(input("Do you want to fluck an image? "))
if answer == True:
  served_img = random.choice(image_url_dictionary.keys())
  print(served_img)
  toFluck = bool(input(Do you want to fluck this image?))
  if(toFluck == True):
    image_url_dictionary[served_img] += 1
    ("Image has been flucked")
  else:
    print("Oh well...")
else:
  print("That's a shame... maybe come back later?")
```
