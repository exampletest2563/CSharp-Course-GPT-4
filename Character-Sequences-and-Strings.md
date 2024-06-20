# Chapter: Character Sequences and Strings in C#

## Introduction

Strings are a fundamental part of programming in C#. They are used to store and manipulate text. Understanding how to work with strings effectively is crucial for tasks ranging from simple text processing to complex data manipulation. This chapter covers various aspects of handling strings and character sequences in C#, including creation, manipulation, formatting, and advanced techniques.

## Creating Strings

### Basic String Creation

Strings in C# are instances of the `System.String` class. You can create strings in several ways:

```csharp
// Using string literals
string hello = "Hello, World!";

// Using the String constructor
char[] chars = { 'H', 'e', 'l', 'l', 'o' };
string helloFromChars = new string(chars);

// Using verbatim strings for multi-line and special characters
string filePath = @"C:\Users\Name\Documents\File.txt";
string multiLine = @"This is a
multi-line
string.";
```

### Interesting Example: Dynamic String Creation

```csharp
// Generate a greeting based on the time of day
DateTime now = DateTime.Now;
string greeting;

if (now.Hour < 12)
{
    greeting = "Good morning!";
}
else if (now.Hour < 18)
{
    greeting = "Good afternoon!";
}
else
{
    greeting = "Good evening!";
}

Console.WriteLine(greeting); // Outputs the appropriate greeting based on the current time
```

## String Immutability

Strings in C# are immutable, meaning once they are created, their values cannot be changed. Any operation that seems to modify a string actually creates a new string.

### Example: Demonstrating Immutability

```csharp
string original = "Hello";
string modified = original.Replace('H', 'J');

Console.WriteLine(original); // Outputs: Hello
Console.WriteLine(modified); // Outputs: Jello
```

## String Operations

### Concatenation

You can concatenate strings using the `+` operator or the `String.Concat` method:

```csharp
string firstName = "John";
string lastName = "Doe";
string fullName = firstName + " " + lastName; // Using +
string fullNameConcat = String.Concat(firstName, " ", lastName); // Using String.Concat
```

### Substrings

The `Substring` method extracts a portion of a string:

```csharp
string text = "Hello, World!";
string subText = text.Substring(7, 5); // "World"
```

### Trimming

The `Trim`, `TrimStart`, and `TrimEnd` methods remove whitespace from a string:

```csharp
string text = "   Hello   ";
string trimmedText = text.Trim(); // "Hello"
```

### Changing Case

Use `ToUpper` and `ToLower` to change the case of a string:

```csharp
string text = "Hello";
string upperText = text.ToUpper(); // "HELLO"
string lowerText = text.ToLower(); // "hello"
```

## String Formatting

### Composite Formatting

Composite formatting uses placeholders within a string:

```csharp
string name = "John";
int age = 30;
string formattedString = String.Format("Name: {0}, Age: {1}", name, age);
Console.WriteLine(formattedString); // "Name: John, Age: 30"
```

### String Interpolation

String interpolation is a more readable way to format strings:

```csharp
string name = "John";
int age = 30;
string interpolatedString = $"Name: {name}, Age: {age}";
Console.WriteLine(interpolatedString); // "Name: John, Age: 30"
```

## Advanced String Manipulation

### Splitting and Joining

You can split a string into an array of substrings and join an array of strings into a single string:

```csharp
string sentence = "This is a sample sentence.";
string[] words = sentence.Split(' ');
string joinedSentence = String.Join(", ", words);
Console.WriteLine(joinedSentence); // "This, is, a, sample, sentence."
```

### Replacing

The `Replace` method substitutes all occurrences of a specified character or substring:

```csharp
string text = "Hello, World!";
string replacedText = text.Replace("World", "C#");
Console.WriteLine(replacedText); // "Hello, C#!"
```

### Removing

The `Remove` method deletes a specified number of characters from a string:

```csharp
string text = "Hello, World!";
string removedText = text.Remove(5, 7); // Starting at index 5, remove 7 characters
Console.WriteLine(removedText); // "Hello"
```

## Working with Character Arrays

Strings can be converted to and from character arrays, which allows for more complex manipulations:

```csharp
string text = "Hello";
char[] charArray = text.ToCharArray();
Array.Reverse(charArray);
string reversedText = new string(charArray);
Console.WriteLine(reversedText); // "olleH"
```

## Using StringBuilder for Efficient String Manipulation

For scenarios involving frequent string modifications, the `StringBuilder` class from the `System.Text` namespace is more efficient:

```csharp
using System.Text;

StringBuilder sb = new StringBuilder();
sb.Append("Hello");
sb.Append(", ");
sb.Append("World!");
string result = sb.ToString();
Console.WriteLine(result); // "Hello, World!"
```

### Interesting Example: Building a Dynamic HTML Table

```csharp
using System.Text;

StringBuilder htmlTable = new StringBuilder();
htmlTable.Append("<table>");

for (int i = 0; i < 3; i++)
{
    htmlTable.Append("<tr>");
    for (int j = 0; j < 3; j++)
    {
        htmlTable.AppendFormat("<td>Row {0}, Cell {1}</td>", i + 1, j + 1);
    }
    htmlTable.Append("</tr>");
}

htmlTable.Append("</table>");
Console.WriteLine(htmlTable.ToString());
```

## Handling Null and Empty Strings

C# provides methods to handle null and empty strings effectively:

```csharp
string emptyString = "";
string nullString = null;

bool isEmpty = String.IsNullOrEmpty(emptyString); // true
bool isNullOrEmpty = String.IsNullOrEmpty(nullString); // true
bool isWhitespace = String.IsNullOrWhiteSpace("   "); // true
```

## Regular Expressions for Advanced Text Processing

Regular expressions (regex) provide powerful pattern matching and text manipulation capabilities:

```csharp
using System.Text.RegularExpressions;

string text = "The quick brown fox jumps over the lazy dog.";
string pattern = @"\b\w{5}\b"; // Matches words with exactly 5 letters
MatchCollection matches = Regex.Matches(text, pattern);

foreach (Match match in matches)
{
    Console.WriteLine(match.Value); // Outputs "quick" and "brown"
}
```

## Conclusion

Strings are a versatile and essential part of C# programming. This chapter has covered a wide range of topics, from basic string creation and manipulation to advanced techniques using `StringBuilder` and regular expressions. By understanding and utilizing these tools and methods, you can handle text data efficiently and effectively in your applications.
