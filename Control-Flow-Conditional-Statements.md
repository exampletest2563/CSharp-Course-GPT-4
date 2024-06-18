# 📘 Chapter: Control Flow - Conditional Statements in C#

## Introduction
Control flow in programming determines the order in which code executes. Conditional statements are a key part of control flow, allowing your program to make decisions based on conditions. In this chapter, we’ll cover the main types of conditional statements in C#, including `if`, `else`, `else if`, `switch`, and ternary operators. We'll use simple, engaging examples to make these concepts easy to understand. Let's dive in! 🚀

## If Statement 🛣️
The `if` statement allows you to execute a block of code only if a specified condition is true.

**Example:**

```csharp
int age = 20;
if (age >= 18) {
    Console.WriteLine("You are an adult. 🎉");
}
```

## If-Else Statement 🌐
The `if-else` statement lets you execute one block of code if the condition is true and another block if it is false.

**Example:**

```csharp
int age = 16;
if (age >= 18) {
    Console.WriteLine("You are an adult. 🎉");
} else {
    Console.WriteLine("You are a minor. 👶");
}
```

## If-Else If-Else Statement 🔄
When you have multiple conditions to check, you can use the `if-else if-else` statement.

**Example:**

```csharp
int temperature = 25;
if (temperature > 30) {
    Console.WriteLine("It's hot outside! ☀️");
} else if (temperature > 20) {
    Console.WriteLine("It's warm outside. 🌤️");
} else if (temperature > 10) {
    Console.WriteLine("It's cool outside. 🌬️");
} else {
    Console.WriteLine("It's cold outside. ❄️");
}
```

## Nested If Statements 🏠
You can place `if` statements inside other `if` statements to check multiple conditions.

**Example:**

```csharp
int age = 22;
bool hasID = true;
if (age >= 18) {
    if (hasID) {
        Console.WriteLine("You can enter the club. 🎉");
    } else {
        Console.WriteLine("You need an ID to enter. 🆔");
    }
} else {
    Console.WriteLine("You are not old enough to enter. 🚫");
}
```

## Switch Statement 🔀
The `switch` statement is a cleaner way to execute different blocks of code based on the value of a variable, especially when there are many conditions.

**Example:**

```csharp
string day = "Monday";
switch (day) {
    case "Monday":
        Console.WriteLine("Start of the work week. 💼");
        break;
    case "Friday":
        Console.WriteLine("Almost the weekend! 🎉");
        break;
    case "Saturday":
    case "Sunday":
        Console.WriteLine("It's the weekend! 🏖️");
        break;
    default:
        Console.WriteLine("Just another day. 🌞");
        break;
}
```

## Ternary Operator 🎭
The ternary operator is a concise way to perform a simple `if-else` operation in a single line.

**Example:**

```csharp
int score = 85;
string result = (score >= 60) ? "Pass 😊" : "Fail 😞";
Console.WriteLine(result);
```

## Combining Conditions 🧩
You can combine multiple conditions using logical operators like `&&` (AND) and `||` (OR).

### AND Operator (&&) 👫

**Example:**

```csharp
int age = 25;
bool hasTicket = true;
if (age >= 18 && hasTicket) {
    Console.WriteLine("You can watch the movie. 🍿");
} else {
    Console.WriteLine("You cannot watch the movie. 🚫");
}
```

### OR Operator (||) 🤝

**Example:**

```csharp
bool isMember = false;
bool hasDiscountCoupon = true;
if (isMember || hasDiscountCoupon) {
    Console.WriteLine("You get a discount! 🎁");
} else {
    Console.WriteLine("No discount for you. 😕");
}
```

## Switch with Enums 🧩
Using `enum` types with `switch` statements can make your code more readable and maintainable.

**Example:**

```csharp
enum DayOfWeek {
    Monday, Tuesday, Wednesday, Thursday, Friday, Saturday, Sunday
}

DayOfWeek today = DayOfWeek.Friday;

switch (today) {
    case DayOfWeek.Monday:
        Console.WriteLine("Back to work! 💼");
        break;
    case DayOfWeek.Friday:
        Console.WriteLine("Almost weekend! 🎉");
        break;
    case DayOfWeek.Saturday:
    case DayOfWeek.Sunday:
        Console.WriteLine("Enjoy the weekend! 🏖️");
        break;
    default:
        Console.WriteLine("Another regular day. 🌞");
        break;
}
```

## Pattern Matching in Switch 🌈
C# 8.0 introduced pattern matching in `switch` statements, which allows more complex and expressive conditions.

**Example:**

```csharp
object value = 42;

switch (value) {
    case int i when i > 0:
        Console.WriteLine("Positive integer. ➕");
        break;
    case int i when i < 0:
        Console.WriteLine("Negative integer. ➖");
        break;
    case string s:
        Console.WriteLine($"String of length {s.Length}. 🧵");
        break;
    default:
        Console.WriteLine("Other type or value. ❓");
        break;
}
```

## Summary 📝
In this chapter, we explored the essential conditional statements in C#, including `if`, `else`, `else if`, `switch`, and ternary operators. We also covered nested conditions, combining conditions, and advanced topics like using enums and pattern matching in `switch` statements. Mastering these control flow tools will help you write more dynamic and responsive code. Keep practicing these techniques to improve your programming skills. Happy coding! 💻✨
