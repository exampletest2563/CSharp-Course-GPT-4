# 📘 Primitive Data Types and Variables in C#

In this chapter, we'll explore the fundamental building blocks of C# programming: primitive data types and variables. 🧱 Understanding these concepts is essential for writing effective and efficient code. Let's dive in! 🚀

## Primitive Data Types 📊

Primitive data types are the most basic data types available in C#. They represent simple values like numbers, characters, and booleans. Here are the common primitive data types in C#:

### Integer Types ➕➖

1. **byte**: 8-bit unsigned integer (0 to 255)
2. **sbyte**: 8-bit signed integer (-128 to 127)
3. **short**: 16-bit signed integer (-32,768 to 32,767)
4. **ushort**: 16-bit unsigned integer (0 to 65,535)
5. **int**: 32-bit signed integer (-2,147,483,648 to 2,147,483,647)
6. **uint**: 32-bit unsigned integer (0 to 4,294,967,295)
7. **long**: 64-bit signed integer (-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807)
8. **ulong**: 64-bit unsigned integer (0 to 18,446,744,073,709,551,615)

Example:
```csharp
byte a = 255;
sbyte b = -128;
short c = 32767;
ushort d = 65535;
int e = 2147483647;
uint f = 4294967295;
long g = 9223372036854775807L;
ulong h = 18446744073709551615UL;
```

### Floating-Point Types 🔢

1. **float**: 32-bit single-precision floating-point number
2. **double**: 64-bit double-precision floating-point number
3. **decimal**: 128-bit precise decimal for financial and monetary calculations

Example:
```csharp
float temperature = 36.6F;
double pi = 3.14159265358979;
decimal price = 19.99M;
```

### Character Type 🔤

- **char**: Represents a single 16-bit Unicode character

Example:
```csharp
char grade = 'A';
```

### Boolean Type ✅❌

- **bool**: Represents a boolean value (true or false)

Example:
```csharp
bool isRaining = false;
```

### String Type 📝

- **string**: Represents a sequence of characters

Example:
```csharp
string greeting = "Hello, World! 👋";
```

## Variables 📦

Variables are used to store data in a program. Each variable has a data type, a name, and a value. In C#, you must declare a variable before using it.

### Variable Declaration and Initialization 🛠️

- **Declaration**: Specifies the variable's type and name.
- **Initialization**: Assigns a value to the variable.

Example:
```csharp
int number;            // Declaration
number = 10;           // Initialization
int age = 25;          // Declaration and initialization
string message = "Hi!"; // Declaration and initialization
```

### Variable Naming Rules ✍️

- Must start with a letter or an underscore (_).
- Can contain letters, digits, and underscores.
- Cannot contain spaces or special characters.
- Cannot be a reserved keyword.

Example:
```csharp
int playerScore = 100;
double accountBalance = 250.75;
bool isGameOver = false;
```

### Naming Conventions 📏

- **Camel Case**: Used for local variables and method parameters (e.g., `playerScore`).
- **Pascal Case**: Used for method names, properties, and class names (e.g., `CalculateTotal`).
- **Underscore**: Prefix private fields with an underscore (e.g., `_totalAmount`).

## Type Inference with var 🔍

The `var` keyword allows the compiler to infer the type of the variable from the assigned value. It's useful for readability but should be used wisely.

Example:
```csharp
var age = 25;           // int
var temperature = 36.6; // double
var name = "Alice";     // string
var isActive = true;    // bool
```

## Type Conversion 🔄

Sometimes you need to convert a value from one data type to another. This can be done explicitly or implicitly.

### Implicit Conversion 🤝

Implicit conversions are done automatically when there is no risk of data loss.

Example:
```csharp
int num = 123;
double doubleNum = num;  // Implicit conversion from int to double
```

### Explicit Conversion (Casting) 🎭

Explicit conversions are required when there is a possibility of data loss.

Example:
```csharp
double pi = 3.14159;
int intPi = (int)pi;  // Explicit conversion from double to int
```

### Using the Convert Class 🛠️

The `Convert` class provides methods for converting between different types.

Example:
```csharp
string strNumber = "123";
int num = Convert.ToInt32(strNumber);  // Convert string to int

double doubleNumber = 123.45;
string strDouble = Convert.ToString(doubleNumber); // Convert double to string
```

### Parsing Strings to Numbers 📜

The `int.Parse()` and `double.Parse()` methods convert strings to numeric types. If the conversion fails, it throws a `FormatException`.

Example:
```csharp
string strNumber = "123";
int num = int.Parse(strNumber); // Convert string to int

string strDouble = "123.45";
double doubleNum = double.Parse(strDouble); // Convert string to double
```

### TryParse Method 🧪

`TryParse` methods attempt to convert a string to a number and return a boolean indicating success or failure, without throwing an exception.

Example:
```csharp
string strNumber = "123";
bool success = int.TryParse(strNumber, out int num);
if (success)
{
    Console.WriteLine($"Conversion successful: {num}");
}
else
{
    Console.WriteLine("Conversion failed.");
}
```

## Constants 🔒

Constants are variables whose values cannot change after they are initialized. Use the `const` keyword to declare a constant.

Example:
```csharp
const double PI = 3.14159;
const int MaxScore = 100;
```

### Readonly Fields 📘

`readonly` fields can be assigned values only during declaration or in a constructor, making them different from constants.

Example:
```csharp
public class Circle
{
    public readonly double Radius;
    
    public Circle(double radius)
    {
        Radius = radius;
    }
}
```

## Nullable Types ❓

In C#, value types (like int, double) cannot be null by default. To allow null values, use nullable types with the `?` symbol.

Example:
```csharp
int? nullableInt = null;
double? nullableDouble = 3.14;

if (nullableInt.HasValue)
{
    Console.WriteLine($"Nullable int value: {nullableInt.Value}");
}
else
{
    Console.WriteLine("Nullable int is null.");
}
```

## Default Values of Data Types 🌟

Each data type in C# has a default value:

- **int**: 0
- **double**: 0.0
- **bool**: false
- **char**: '\0'
- **string**: null

Example:
```csharp
int defaultInt;       // defaultInt is 0
double defaultDouble; // defaultDouble is 0.0
bool defaultBool;     // defaultBool is false
char defaultChar;     // defaultChar is '\0'
string defaultString; // defaultString is null
```

## Using var and Dynamic for Flexibility 🔄

### var Keyword 🔍

The `var` keyword allows for type inference by the compiler at compile time.

Example:
```csharp
var age = 30; // age is inferred as int
var name = "Alice"; // name is inferred as string
var price = 19.99; // price is inferred as double
```

### dynamic Keyword 🧬

The `dynamic` keyword allows for type flexibility at runtime, which can be useful for certain scenarios but should be used with caution.

Example:
```csharp
dynamic variable = 1; // variable is initially an int
variable = "Hello"; // now variable is a string
variable = 3.14; // now variable is a double
```

## String Interpolation and Concatenation 🧩

String manipulation is a common task in programming. C# provides several ways to work with strings.

### Concatenation ➕

Joining strings using the `+` operator:

Example:
```csharp
string firstName = "John";
string lastName = "Doe";
string fullName = firstName + " " + lastName; // "John Doe"
```

### String Interpolation 🧵

Embedding expressions within string literals using `$`:

Example:
```csharp
string firstName = "John";
string lastName = "Doe";
string fullName = $"{firstName} {lastName}"; // "John Doe"
```

### String Methods 🛠️

Commonly used string methods:

- `Length`: Returns the number of characters in a string

.
- `ToUpper()`, `ToLower()`: Converts the string to uppercase or lowercase.
- `Trim()`: Removes leading and trailing whitespace.
- `Substring(startIndex, length)`: Extracts a substring.
- `Contains(value)`: Checks if the string contains a specified value.

Example:
```csharp
string message = " Hello, World! ";
int length = message.Length; // 15
string upper = message.ToUpper(); // " HELLO, WORLD! "
string trimmed = message.Trim(); // "Hello, World!"
string substring = message.Substring(7, 5); // "World"
bool contains = message.Contains("World"); // true
```

## Summary 🎓

In this chapter, you've learned about the primitive data types in C#, how to declare and initialize variables, and the basics of type conversion. You've also explored constants, nullable types, default values, and string manipulation. Understanding these fundamentals is crucial for writing effective C# programs. Practice using these data types and variables in your code to become more comfortable with them. Happy coding! 🖥️✨
