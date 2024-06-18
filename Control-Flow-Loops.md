# 📘 Chapter: Control Flow - Loops in C#

## Introduction
Loops are essential for executing repetitive tasks efficiently in programming. In C#, there are several types of loops, each suited for different scenarios. This chapter covers the various loops available in C#, including `for`, `foreach`, `while`, and `do-while` loops, with engaging examples to help you understand and apply these concepts effectively. Let's dive in! 🚀

## For Loop 🔄
The `for` loop is ideal for scenarios where you know in advance how many times you need to execute a block of code.

**Syntax:**

```csharp
for (initialization; condition; iteration) {
    // Code to be executed
}
```

**Example:**

```csharp
for (int i = 0; i < 5; i++) {
    Console.WriteLine($"Iteration {i + 1}: Hello, World! 🌍");
}
```

### Using for Loop with Arrays 📊

**Example:**

```csharp
int[] numbers = { 1, 2, 3, 4, 5 };
for (int i = 0; i < numbers.Length; i++) {
    Console.WriteLine($"Element at index {i} is {numbers[i]}");
}
```

### Nested For Loops 🏠

**Example:**

```csharp
for (int i = 1; i <= 3; i++) {
    for (int j = 1; j <= 3; j++) {
        Console.WriteLine($"i: {i}, j: {j}");
    }
}
```

## Foreach Loop 🔄
The `foreach` loop is perfect for iterating over collections such as arrays and lists without needing an index variable.

**Syntax:**

```csharp
foreach (var item in collection) {
    // Code to be executed
}
```

**Example:**

```csharp
string[] fruits = { "Apple", "Banana", "Cherry" };
foreach (string fruit in fruits) {
    Console.WriteLine($"I like {fruit} 🍎🍌🍒");
}
```

### Modifying Collections with Foreach ✏️

**Example:**

```csharp
List<int> numbers = new List<int> { 1, 2, 3, 4, 5 };
for (int i = 0; i < numbers.Count; i++) {
    numbers[i] *= 2; // Doubling each number
}
foreach (int number in numbers) {
    Console.WriteLine($"Number: {number}");
}
```

## While Loop 🔁
The `while` loop is suitable when you don't know in advance how many times you need to execute a block of code. The loop continues as long as the condition is true.

**Syntax:**

```csharp
while (condition) {
    // Code to be executed
}
```

**Example:**

```csharp
int counter = 0;
while (counter < 5) {
    Console.WriteLine($"Counter: {counter}");
    counter++;
}
```

### Infinite Loops 🔄♾️

**Example (with break):**

```csharp
int count = 0;
while (true) {
    if (count >= 5) break;
    Console.WriteLine($"Count: {count}");
    count++;
}
```

## Do-While Loop 🔁
The `do-while` loop is similar to the `while` loop, but it guarantees that the code block executes at least once, as the condition is checked after the block executes.

**Syntax:**

```csharp
do {
    // Code to be executed
} while (condition);
```

**Example:**

```csharp
int number = 0;
do {
    Console.WriteLine($"Number: {number}");
    number++;
} while (number < 5);
```

## Break and Continue Keywords ⏸️🔄
The `break` keyword exits the loop immediately, while the `continue` keyword skips the current iteration and proceeds with the next iteration.

### Break Example 🛑

**Example:**

```csharp
for (int i = 0; i < 10; i++) {
    if (i == 5) {
        break; // Exit the loop
    }
    Console.WriteLine($"i: {i}");
}
```

### Continue Example ⏭️

**Example:**

```csharp
for (int i = 0; i < 10; i++) {
    if (i % 2 == 0) {
        continue; // Skip even numbers
    }
    Console.WriteLine($"i: {i}");
}
```

## Nested Loops with Different Types 🌟
You can nest different types of loops within each other to handle complex scenarios.

**Example:**

```csharp
int[,] matrix = {
    { 1, 2, 3 },
    { 4, 5, 6 },
    { 7, 8, 9 }
};

for (int i = 0; i < 3; i++) {
    foreach (int value in matrix) {
        Console.Write($"{value} ");
    }
    Console.WriteLine();
}
```

## Looping Through Collections with LINQ 🔄🔍
LINQ (Language Integrated Query) provides a powerful way to loop through collections and perform operations.

**Example:**

```csharp
List<int> numbers = new List<int> { 1, 2, 3, 4, 5 };
var evenNumbers = numbers.Where(n => n % 2 == 0);

foreach (int number in evenNumbers) {
    Console.WriteLine($"Even number: {number}");
}
```

## Using Loops with Dictionaries 📚
Dictionaries store key-value pairs, and you can loop through them to access each pair.

**Example:**

```csharp
Dictionary<string, int> ages = new Dictionary<string, int> {
    { "Alice", 30 },
    { "Bob", 25 },
    { "Charlie", 35 }
};

foreach (var kvp in ages) {
    Console.WriteLine($"{kvp.Key} is {kvp.Value} years old.");
}
```

## Summary 📝
In this chapter, we explored various types of loops in C#, including `for`, `foreach`, `while`, and `do-while` loops. We covered practical examples of using loops to iterate through arrays, lists, dictionaries, and even complex nested loops. We also learned about the `break` and `continue` keywords to control loop execution flow. Understanding these loop constructs will enable you to write efficient and effective code for repetitive tasks. Keep practicing to master these essential programming tools. Happy coding! 💻✨
