# 📘 Chapter: Text Formatting in C#

## Introduction
Text formatting in C# is an essential skill for creating user-friendly and readable output. Whether you're building a console application, a web application, or working with any kind of text output, understanding how to format text effectively can greatly enhance the user experience. This chapter covers various methods and techniques for text formatting in C# with simple and engaging examples. Let's get started! 🚀

## Basic String Interpolation 🧵
String interpolation is a powerful and concise way to include variables and expressions inside a string.

**Example:**

```csharp
string name = "Alice";
int age = 30;
Console.WriteLine($"Hello, my name is {name} and I am {age} years old. 🎂");
```

## String Concatenation ➕
String concatenation combines multiple strings into one using the `+` operator.

**Example:**

```csharp
string part1 = "Hello, ";
string part2 = "World!";
string greeting = part1 + part2;
Console.WriteLine(greeting + " 🌍");
```

## Formatting Numbers 🔢
Formatting numbers is crucial for displaying values like currency, percentages, and decimals.

### Currency Formatting 💲

**Example:**

```csharp
decimal price = 19.99m;
Console.WriteLine($"The price is {price:C}. 💵");
```

### Decimal Places 📏

**Example:**

```csharp
double number = 123.456789;
Console.WriteLine($"Formatted number: {number:F2}"); // Output: 123.46
```

### Percentages 📊

**Example:**

```csharp
double ratio = 0.854;
Console.WriteLine($"Success rate: {ratio:P2}"); // Output: 85.40%
```

## Formatting Dates and Times ⏰
Working with dates and times is common in many applications. C# provides various ways to format `DateTime` values.

**Example:**

```csharp
DateTime now = DateTime.Now;
Console.WriteLine($"Current date and time: {now:dddd, MMMM d, yyyy h:mm tt}"); // Output: Monday, June 18, 2023 2:30 PM
```

## Padding and Aligning Strings 📏
Padding and aligning strings help in creating neat and organized text outputs, especially in tabular formats.

**Example:**

```csharp
string leftAligned = "Left".PadRight(10);
string rightAligned = "Right".PadLeft(10);
Console.WriteLine($"|{leftAligned}|{rightAligned}|"); // Output: |Left      |     Right|
```

## Composite Formatting 📚
Composite formatting uses placeholders in a string, which are replaced by corresponding arguments.

**Example:**

```csharp
string format = "Name: {0}, Age: {1}, Score: {2:F1}";
string result = string.Format(format, "Bob", 25, 93.456);
Console.WriteLine(result); // Output: Name: Bob, Age: 25, Score: 93.5
```

## Using the StringBuilder Class 🏗️
For more complex or performance-critical string manipulations, the `StringBuilder` class is preferred.

**Example:**

```csharp
using System.Text;

StringBuilder sb = new StringBuilder();
sb.Append("Hello");
sb.Append(", ");
sb.Append("World");
sb.Append("!");
Console.WriteLine(sb.ToString() + " 🌍");
```

## Escape Sequences 🔡
Escape sequences allow you to include special characters in strings, such as newlines and tabs.

**Example:**

```csharp
string multiLine = "Line 1\nLine 2\nLine 3";
Console.WriteLine(multiLine);

string tabbed = "Item\tPrice\nApple\t$1\nBanana\t$2";
Console.WriteLine(tabbed);
```

## Verbatim Strings 📝
Verbatim strings preserve whitespace and special characters, making them useful for file paths and multiline strings.

**Example:**

```csharp
string filePath = @"C:\Users\Alice\Documents\file.txt";
Console.WriteLine($"File path: {filePath}");

string multiLine = @"This is a
multiline
string.";
Console.WriteLine(multiLine);
```

## Custom Numeric Formatting 🧮
Custom numeric formatting allows you to define your own patterns for displaying numbers.

**Example:**

```csharp
double number = 1234.567;
Console.WriteLine(number.ToString("0.###")); // Output: 1234.567
Console.WriteLine(number.ToString("00000.00")); // Output: 01234.57
```

## Custom Date and Time Formatting 📅
Just like numeric formatting, you can define custom patterns for dates and times.

**Example:**

```csharp
DateTime date = DateTime.Now;
Console.WriteLine(date.ToString("yyyy-MM-dd HH:mm:ss")); // Output: 2024-06-18 14:30:00
Console.WriteLine(date.ToString("MMMM dd, yyyy")); // Output: June 18, 2024
```

## Culture-Specific Formatting 🌍
Different cultures have different conventions for displaying numbers and dates. You can format strings according to specific cultures.

**Example:**

```csharp
using System.Globalization;

double number = 1234.56;
CultureInfo germanCulture = new CultureInfo("de-DE");
Console.WriteLine(number.ToString("C", germanCulture)); // Output: 1.234,56 €

DateTime date = DateTime.Now;
CultureInfo frenchCulture = new CultureInfo("fr-FR");
Console.WriteLine(date.ToString("D", frenchCulture)); // Output: lundi 18 juin 2024
```

## String Interpolation with Expressions 🧮
String interpolation can include more complex expressions.

**Example:**

```csharp
int a = 5, b = 10;
Console.WriteLine($"The sum of {a} and {b} is {a + b}. ➕");
```

## Summary 📝
In this chapter, we've explored various methods and techniques for text formatting in C#. From basic string interpolation and concatenation to advanced formatting of numbers, dates, and times, you now have a comprehensive understanding of how to make your text output more readable and user-friendly. We also covered the use of `StringBuilder` for performance-critical operations and culture-specific formatting for international applications. Keep practicing these techniques to enhance your text formatting skills. Happy coding! 💻✨
