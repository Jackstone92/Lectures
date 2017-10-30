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
