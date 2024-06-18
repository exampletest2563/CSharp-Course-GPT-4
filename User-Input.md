# 📘 Chapter: User Input in C#

## Introduction
Handling user input is a fundamental aspect of programming in C#. This chapter covers various methods to capture and process user input with simple and interesting examples suitable for beginners. Let's get started! 🚀

## I/O Operations 🔄
Input and Output (I/O) operations are crucial for interacting with the user and the system. In C#, the `System.Console` class provides methods for both input and output operations.

### Output Operations 📤
**Example:**

```csharp
Console.WriteLine("Welcome to the C# User Input Guide! 📘");
```

### Input Operations 📥
To capture input from the user, we typically use `Console.ReadLine()`.

## Reading User Input 📝
The `Console.ReadLine()` method is the most common way to get user input in a console application. This method reads a line of text from the console.

**Example:**

```csharp
Console.Write("Enter your name: ");
string name = Console.ReadLine();
Console.WriteLine($"Hello, {name}! 👋");
```

## Parsing User Input 🌐
User input is often read as a string, but we may need to convert it to other data types. Parsing is essential for such conversions.

### Converting to Integer 🔢

**Example:**

```csharp
Console.Write("Enter your age: ");
string ageInput = Console.ReadLine();
int age = int.Parse(ageInput);
Console.WriteLine($"You are {age} years old. 🎂");
```

### Handling Invalid Input 🚫
It's important to handle scenarios where the user input might not be valid. We can use `TryParse` methods to safely attempt conversions.

**Example:**

```csharp
Console.Write("Enter a number: ");
string input = Console.ReadLine();
if (int.TryParse(input, out int number)) {
    Console.WriteLine($"You entered the number {number}. 👍");
} else {
    Console.WriteLine("Invalid input. Please enter a valid number. ⚠️");
}
```

## Using Console.ReadKey() ⌨️
The `Console.ReadKey()` method is useful for reading a single key press from the user. It can be used for creating interactive console applications.

**Example:**

```csharp
Console.WriteLine("Press any key to continue... ⏩");
Console.ReadKey();
Console.WriteLine("You pressed a key! 🖱️");
```

## Handling Key Events 🔑
For more complex input scenarios, handling key events is crucial. This involves detecting specific keys being pressed.

**Example:**

```csharp
Console.WriteLine("Press 'Q' to quit.");
while (true) {
    var keyInfo = Console.ReadKey(intercept: true);
    if (keyInfo.Key == ConsoleKey.Q) {
        Console.WriteLine("\nYou pressed 'Q'. Exiting... ❌");
        break;
    } else {
        Console.WriteLine($"\nYou pressed {keyInfo.Key}. Try again. 🔄");
    }
}
```

## Getting Secure Input 🔒
For scenarios where you need to capture sensitive information like passwords, you can mask the input.

**Example:**

```csharp
Console.Write("Enter your password: ");
string password = "";
while (true) {
    var key = Console.ReadKey(intercept: true);
    if (key.Key == ConsoleKey.Enter) break;
    password += key.KeyChar;
    Console.Write("*");
}
Console.WriteLine();
Console.WriteLine("Password captured securely! 🔐");
```

## Using Environment Variables 🌍
Sometimes, we might need to use environment variables as a source of input.

**Example:**

```csharp
string userName = Environment.GetEnvironmentVariable("USERNAME");
Console.WriteLine($"Hello, {userName}! 🌐");
```

## Command Line Arguments 🖥️
Command line arguments are another way to pass input to a C# application.

**Example:**

```csharp
static void Main(string[] args) {
    if (args.Length > 0) {
        Console.WriteLine($"Hello, {args[0]}! 👋");
    } else {
        Console.WriteLine("No arguments provided. 😕");
    }
}
```

## Using Forms for User Input 🖼️
For GUI applications, you can use Windows Forms or WPF to capture user input through various controls like text boxes, buttons, etc.

**Example with Windows Forms:**

```csharp
using System;
using System.Windows.Forms;

public class InputForm : Form {
    private TextBox inputBox;
    private Button submitButton;

    public InputForm() {
        inputBox = new TextBox() { Left = 50, Top = 20, Width = 200 };
        submitButton = new Button() { Text = "Submit", Left = 100, Top = 50 };
        submitButton.Click += (sender, e) => MessageBox.Show($"You entered: {inputBox.Text}");
        Controls.Add(inputBox);
        Controls.Add(submitButton);
    }
}

public class Program {
    [STAThread]
    static void Main() {
        Application.Run(new InputForm());
    }
}
```

## Summary 📝
In this chapter, we've explored various methods to capture and process user input in C#, including I/O operations, reading from the console, handling invalid input, using `Console.ReadKey()`, capturing secure input, using environment variables, command line arguments, key events, and creating GUI applications. Understanding these methods will enable you to build more interactive and user-friendly applications. 🎉

Keep experimenting with these techniques to enhance your skills. Happy coding! 💻✨
