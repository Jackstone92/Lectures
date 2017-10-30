# Data Types and Arithmetic Operations

---

# Declaring variables
## 1. Allocate in memory
- Syntax: `type variableName`
- Eg. `double radius`

## 2. Assign a value
- Syntax: `variableName = value;`
- Eg. `radius = 5;`

## 3. Constants `final`
- Syntax: `final type variableName`
- Eg. `final int size = 3;`

# Primitive data types
## Char data type

| Type | Description | Default | Storage Size | Example |
| --- | --- | --- | --- | --- |
| char | Unicode Character | \u0000 | 16-bit | 'a', '\u0000', '\101', '\\', '\n'

## Boolean data type

| Type | Description | Default | Storage Size | Example |
| --- | --- | --- | --- | --- |
| bool | true or false | false | 1 bit | true, false |

# Numerical data types

| Type | Description | Default | Storage Size | Example | Range |
| --- | --- | --- | --- | --- | --- |
| byte | Two's compliment integer | 0 | 8 bits | (none) | -2<sup>7</sup> (-128) to 2<sup>7</sup>-1 (127)
| short | Two's compliment integer | 0 | 16 bits | (none) | -2<sup>15</sup> (-32768) to 2<sup>15</sup>-1 (32767)|
| int | Two's compliment integer | 0 | 32 bits | -2, -1, 0, 1, 2 | -2<sup>31</sup> (-2147483648) to 2<sup>31</sup>-1 (2147483647) |
| long | Two's compliment integer | 0 | 64 bits | -2L, -1L, 0L, 1L, 2L | -2<sup>63</sup> to 2<sup>63</sup>-1 |
| float | IEEE 754 floating point | 0.0 | 32 bits | 1.23e100f, -1.23e-100f, .3f, 3.14F | Negative range: -3.4028235E+38 to -1.4E-45 Positive range: 1.4E-45 to 3.408235E+38 |
| double | IEEE 754 floating point | 0.0 | 64 bits | 1.23456e300d, -1.23456e-300d, 1e1d | Negative range: -1.7976931348623157E+308 to -4.9E-324 Positive range: 4.9E-324 to 7976931348623157E+308 |

# Conversions
## Ranks
Types have ranks - higher types occupy more space and hold more digits
1. byte
2. short
3. int
4. long
5. float
6. double

## Widening conversion
- Converting from lower-ranked to higher-ranked types
- Done automatically with Java

## Narrowing conversion
- Converting from higher-ranked to lower-ranked types
- Java doesn't perform this as it may cause loss of **precision**

## Type cast operators
Manually convert a variable from typeA to typeB
```java
int x;
double y = 10;
x = (int)y;
```

## Type casting side effects
```java
int a = 10, b = 4;
double c = a / b;
double d = (double)a / b;
double e = (double)(a / b);

System.out.println(c); // 2.0, c = 10/4 = 2
System.out.println(d); // 2.5, d = double(10)/4 = 10.0/4 = 2.5
System.out.println(e); // 2.0, e = double(10/4) = double(2) = 2.0
```

## Explicit conversion
```java
int i = 999999999;
byte b = (byte)i; // The type cast causes an explicit conversion //
b = i; // Compliation error! No implicit conversion
```

## implicit conversion
```java
int i = 999999999;
float f = i; // An implicit conversion is performed here //
```

> Conversion order: lower rank to higher rank types!

# Mixed integer operations
Whenever using any integer in an arithmetic operation, Java **temporarily converts them to int** and **doesn't convert it back automatically**
```java
short x = 10, y = 20, z;
//z = x + y; // typeError
z = (short) x + y; // convert (int) x + y to short
```

# Casting between char and Numeric Types
```java
int i = 'a'; // same as int i = (int)'a';
char c = 97; // same as char c = (char)97;
```

# `++a` vs `a++`
## `++a`
Return `a` **after** executing `a += 1`
```java
int a = 5;
int b = ++a;
System.out.println(a); // 6
System.out.println(b); // 6
```

## `a++`
Return `a` **before** executing `a += 1`
```java
int a = 5;
int b = a++;
System.out.println(a); // 6
System.out.println(b); // 5
```
