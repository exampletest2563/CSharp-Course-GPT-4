# Chapter: Text Processing in C#

## Introduction

Text processing is a fundamental aspect of many software applications. In C#, the `string` class provides a rich set of methods for handling and manipulating text. Additionally, the `System.Text` namespace and regular expressions offer powerful tools for more advanced text processing tasks. This chapter will cover essential string operations, regular expressions, string interpolation, and working with different text encodings.

## String Basics

### Declaring and Initializing Strings

In C#, a `string` is a sequence of characters. Strings are immutable, meaning their values cannot be changed after they are created.

```csharp
string greeting = "Hello, World!";
```

### Common String Operations

#### Concatenation

You can concatenate strings using the `+` operator or the `String.Concat` method:

```csharp
string firstName = "John";
string lastName = "Doe";
string fullName = firstName + " " + lastName; // Using +
string fullName2 = String.Concat(firstName, " ", lastName); // Using String.Concat
```

#### Substrings

The `Substring` method extracts a portion of a string:

```csharp
string text = "Hello, World!";
string subText = text.Substring(7, 5); // "World"
```

#### Length

The `Length` property returns the number of characters in a string:

```csharp
string text = "Hello";
int length = text.Length; // 5
```

#### Indexing

You can access individual characters using the indexer:

```csharp
string text = "Hello";
char firstChar = text[0]; // 'H'
```

#### Trimming

The `Trim`, `TrimStart`, and `TrimEnd` methods remove whitespace from a string:

```csharp
string text = "   Hello   ";
string trimmedText = text.Trim(); // "Hello"
string trimmedStart = text.TrimStart(); // "Hello   "
string trimmedEnd = text.TrimEnd(); // "   Hello"
```

#### Changing Case

Use `ToUpper` and `ToLower` to change the case of a string:

```csharp
string text = "Hello";
string upperText = text.ToUpper(); // "HELLO"
string lowerText = text.ToLower(); // "hello"
```

## String Interpolation

String interpolation allows you to embed expressions within string literals. It is a more readable and convenient way to format strings.

```csharp
string name = "John";
int age = 30;
string message = $"Name: {name}, Age: {age}"; // "Name: John, Age: 30"
```

## String Formatting

The `String.Format` method allows you to create formatted strings using placeholders:

```csharp
string name = "John";
int age = 30;
string message = String.Format("Name: {0}, Age: {1}", name, age); // "Name: John, Age: 30"
```

## StringBuilder

The `StringBuilder` class, found in the `System.Text` namespace, is used for efficiently creating and manipulating large or complex strings. Unlike strings, `StringBuilder` objects are mutable.

### Creating a StringBuilder

```csharp
StringBuilder sb = new StringBuilder();
sb.Append("Hello");
sb.Append(" ");
sb.Append("World");
string result = sb.ToString(); // "Hello World"
```

### StringBuilder Methods

- **Append**: Adds text to the end.
- **Insert**: Inserts text at a specified index.
- **Remove**: Removes a specified range of characters.
- **Replace**: Replaces all occurrences of a specified character with another character.

```csharp
StringBuilder sb = new StringBuilder("Hello, World!");
sb.Replace("World", "C#"); // "Hello, C#!"
```

## Regular Expressions

Regular expressions (regex) provide a powerful way to perform pattern matching and text manipulation. The `System.Text.RegularExpressions` namespace contains classes for working with regular expressions.

### Basic Usage

```csharp
using System.Text.RegularExpressions;

string pattern = @"\d+";
string input = "There are 123 apples";
Match match = Regex.Match(input, pattern);

if (match.Success)
{
    Console.WriteLine($"Found a match: {match.Value}"); // "123"
}
```

### Common Regex Operations

- **Match**: Finds the first match of a pattern.
- **Matches**: Finds all matches of a pattern.
- **Replace**: Replaces text that matches a pattern.
- **Split**: Splits a string based on a pattern.

```csharp
string input = "one1two2three3four4";
string pattern = @"\d";
string[] result = Regex.Split(input, pattern);
// result: ["one", "two", "three", "four"]

string replaced = Regex.Replace(input, pattern, "-");
// replaced: "one-two-three-four-"
```

### Regex Patterns

Regex patterns use special characters to define search criteria:
- `\d`: Digit
- `\w`: Word character (alphanumeric)
- `\s`: Whitespace
- `.`: Any character
- `*`: Zero or more
- `+`: One or more
- `?`: Zero or one
- `^`: Start of string
- `$`: End of string

## Working with Encodings

Text encoding is essential for reading and writing text in different formats. The `System.Text.Encoding` class provides methods to handle various encodings, such as UTF-8, UTF-16, and ASCII.

### Common Encodings

- **UTF-8**: Variable-width encoding, efficient for most languages.
- **UTF-16**: Fixed-width encoding, used internally by .NET.
- **ASCII**: 7-bit encoding, suitable for English text.

### Encoding and Decoding

```csharp
using System.Text;

string original = "Hello, World!";
byte[] utf8Bytes = Encoding.UTF8.GetBytes(original);
string utf8String = Encoding.UTF8.GetString(utf8Bytes);

byte[] utf16Bytes = Encoding.Unicode.GetBytes(original);
string utf16String = Encoding.Unicode.GetString(utf16Bytes);
```

## File I/O with Text

Reading and writing text files is a common task in text processing. The `System.IO` namespace provides classes for file I/O operations.

### Reading Text Files

```csharp
using System.IO;

string path = "example.txt";
string text = File.ReadAllText(path);
string[] lines = File.ReadAllLines(path);
```

### Writing Text Files

```csharp
using System.IO;

string path = "example.txt";
string text = "Hello, World!";
File.WriteAllText(path, text);

string[] lines = { "Line 1", "Line 2", "Line 3" };
File.WriteAllLines(path, lines);
```

## Conclusion

Text processing is a crucial skill in software development. In C#, you have a wealth of tools and techniques at your disposal for handling and manipulating text. From basic string operations and formatting to advanced pattern matching with regular expressions and efficient text manipulation with `StringBuilder`, this chapter has provided a comprehensive overview of text processing in C#. Additionally, understanding text encoding and file I/O operations will enable you to work with text data effectively in your applications.
