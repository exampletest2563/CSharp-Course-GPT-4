# Chapter: Associative Arrays and Dictionaries in C#

## Introduction

Associative arrays, also known as maps or dictionaries, are data structures that allow you to store key-value pairs. In C#, the `Dictionary<TKey, TValue>` class from the `System.Collections.Generic` namespace provides a powerful implementation of an associative array. This chapter covers the creation, manipulation, and advanced usage of dictionaries in C#, including interesting examples to demonstrate various features.

## Creating Dictionaries

### Basic Dictionary Creation

You can create a dictionary by specifying the types for the keys and values:

```csharp
using System;
using System.Collections.Generic;

Dictionary<int, string> idToName = new Dictionary<int, string>(); // Dictionary with integer keys and string values
Dictionary<string, int> nameToAge = new Dictionary<string, int>(); // Dictionary with string keys and integer values
```

### Initializing with Elements

You can initialize a dictionary with a collection of key-value pairs:

```csharp
Dictionary<int, string> idToName = new Dictionary<int, string>
{
    { 1, "Alice" },
    { 2, "Bob" },
    { 3, "Charlie" }
};

Dictionary<string, int> nameToAge = new Dictionary<string, int>
{
    { "Alice", 30 },
    { "Bob", 25 },
    { "Charlie", 35 }
};
```

### Interesting Example: Dictionary of Custom Objects

```csharp
public class Person
{
    public string Name { get; set; }
    public int Age { get; set; }

    public Person(string name, int age)
    {
        Name = name;
        Age = age;
    }

    public override string ToString() => $"Name: {Name}, Age: {Age}";
}

Dictionary<int, Person> idToPerson = new Dictionary<int, Person>
{
    { 1, new Person("Alice", 30) },
    { 2, new Person("Bob", 25) },
    { 3, new Person("Charlie", 35) }
};

foreach (var kvp in idToPerson)
{
    Console.WriteLine($"ID: {kvp.Key}, {kvp.Value}");
}
```

## Adding and Removing Elements

### Adding Elements

You can add elements to a dictionary using the `Add` method or the indexer:

```csharp
Dictionary<int, string> idToName = new Dictionary<int, string>();
idToName.Add(1, "Alice");
idToName[2] = "Bob"; // Using the indexer

foreach (var kvp in idToName)
{
    Console.WriteLine($"ID: {kvp.Key}, Name: {kvp.Value}");
}
```

### Removing Elements

You can remove elements using the `Remove` method or clear the dictionary with the `Clear` method:

```csharp
Dictionary<int, string> idToName = new Dictionary<int, string>
{
    { 1, "Alice" },
    { 2, "Bob" },
    { 3, "Charlie" }
};

idToName.Remove(2); // Removes the element with key 2
idToName.Clear(); // Removes all elements

Console.WriteLine($"Count after clearing: {idToName.Count}");
```

### Interesting Example: Removing Elements Based on Condition

```csharp
Dictionary<int, string> idToName = new Dictionary<int, string>
{
    { 1, "Alice" },
    { 2, "Bob" },
    { 3, "Charlie" },
    { 4, "David" }
};

// Remove all entries with names starting with 'C'
foreach (var key in new List<int>(idToName.Keys))
{
    if (idToName[key].StartsWith("C"))
    {
        idToName.Remove(key);
    }
}

foreach (var kvp in idToName)
{
    Console.WriteLine($"ID: {kvp.Key}, Name: {kvp.Value}");
}
```

## Accessing Elements

### Indexing

You can access elements in a dictionary using the indexer:

```csharp
Dictionary<int, string> idToName = new Dictionary<int, string>
{
    { 1, "Alice" },
    { 2, "Bob" },
    { 3, "Charlie" }
};

string name = idToName[1];
Console.WriteLine($"Name with ID 1: {name}");
```

### Iterating

You can iterate over the elements using a `foreach` loop:

```csharp
Dictionary<int, string> idToName = new Dictionary<int, string>
{
    { 1, "Alice" },
    { 2, "Bob" },
    { 3, "Charlie" }
};

foreach (var kvp in idToName)
{
    Console.WriteLine($"ID: {kvp.Key}, Name: {kvp.Value}");
}
```

### Interesting Example: Finding Elements

```csharp
Dictionary<int, string> idToName = new Dictionary<int, string>
{
    { 1, "Alice" },
    { 2, "Bob" },
    { 3, "Charlie" },
    { 4, "David" }
};

string name = idToName.FirstOrDefault(kvp => kvp.Key == 3).Value;
Console.WriteLine($"Name with ID 3: {name}");
```

## Modifying Elements

### Updating Elements

You can update elements in a dictionary by accessing them through the indexer:

```csharp
Dictionary<int, string> idToName = new Dictionary<int, string>
{
    { 1, "Alice" },
    { 2, "Bob" },
    { 3, "Charlie" }
};

idToName[2] = "Robert"; // Updates "Bob" to "Robert"

foreach (var kvp in idToName)
{
    Console.WriteLine($"ID: {kvp.Key}, Name: {kvp.Value}");
}
```

## Advanced Dictionary Features

### Checking for Keys and Values

You can check if a dictionary contains a specific key or value:

```csharp
Dictionary<int, string> idToName = new Dictionary<int, string>
{
    { 1, "Alice" },
    { 2, "Bob" },
    { 3, "Charlie" }
};

bool containsKey = idToName.ContainsKey(2);
bool containsValue = idToName.ContainsValue("Charlie");

Console.WriteLine($"Contains key 2: {containsKey}");
Console.WriteLine($"Contains value 'Charlie': {containsValue}");
```

### Interesting Example: Dictionary of Lists

```csharp
Dictionary<string, List<string>> countryToCities = new Dictionary<string, List<string>>
{
    { "USA", new List<string> { "New York", "Los Angeles", "Chicago" } },
    { "UK", new List<string> { "London", "Manchester", "Liverpool" } },
    { "India", new List<string> { "Mumbai", "Delhi", "Bangalore" } }
};

foreach (var kvp in countryToCities)
{
    Console.WriteLine($"Country: {kvp.Key}");
    Console.WriteLine("Cities:");
    foreach (var city in kvp.Value)
    {
        Console.WriteLine($"  {city}");
    }
}
```

### Merging Dictionaries

You can merge two dictionaries using the `Union` method from LINQ:

```csharp
using System.Linq;

Dictionary<int, string> dict1 = new Dictionary<int, string>
{
    { 1, "Alice" },
    { 2, "Bob" }
};

Dictionary<int, string> dict2 = new Dictionary<int, string>
{
    { 3, "Charlie" },
    { 4, "David" }
};

Dictionary<int, string> mergedDict = dict1.Union(dict2).ToDictionary(kvp => kvp.Key, kvp => kvp.Value);

foreach (var kvp in mergedDict)
{
    Console.WriteLine($"ID: {kvp.Key}, Name: {kvp.Value}");
}
```

## Performance Considerations

Dictionaries offer fast lookups, insertions, and deletions on average, but there are some performance considerations to keep in mind:

- **Load Factor and Resizing**: The performance of a dictionary can degrade if it needs to resize its internal data structures frequently. You can set the initial capacity if you know the approximate size in advance.
- **Hash Collisions**: Performance can be affected by hash collisions, where multiple keys have the same hash code. Ensuring a good distribution of hash codes can help mitigate this.

### Example: Setting Initial Capacity

```csharp
Dictionary<int, string> idToName = new Dictionary<int, string>(100); // Initial capacity for 100 elements

for (int i = 0; i < 100; i++)
{
    idToName.Add(i, $"Name{i}");
}

Console.WriteLine($"Count: {idToName.Count}");
```

## Conclusion

Dictionaries are an essential and versatile data structure in C#. The `Dictionary<TKey, TValue>` class provides a robust implementation for managing collections of key-value pairs, with extensive support for adding, removing, accessing, and modifying elements. This chapter has covered the basics and advanced usage of dictionaries, along with interesting examples to demonstrate their capabilities. By leveraging the features of `Dictionary<TKey, TValue>`, you can efficiently manage and manipulate associative data in your C# projects.
