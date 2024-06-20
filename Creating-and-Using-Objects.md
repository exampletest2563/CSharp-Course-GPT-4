# Chapter: Creating and Using Objects in C#

## Introduction

Object-oriented programming (OOP) is a programming paradigm centered around objects and classes. In C#, everything revolves around objects, which are instances of classes. This chapter will guide you through the process of creating and using objects in C#, covering class definitions, constructors, properties, methods, and the `this` keyword.

## Classes and Objects

### Defining a Class

A class is a blueprint for creating objects. It defines the properties (data) and methods (behavior) that the objects created from the class will have. Here’s the basic syntax for defining a class:

```csharp
public class Person
{
    // Fields
    private string name;
    private int age;

    // Properties
    public string Name
    {
        get { return name; }
        set { name = value; }
    }

    public int Age
    {
        get { return age; }
        set { age = value; }
    }

    // Methods
    public void DisplayInfo()
    {
        Console.WriteLine($"Name: {Name}, Age: {Age}");
    }
}
```

### Creating Objects

To create an object, you use the `new` keyword followed by a call to the class constructor:

```csharp
Person person = new Person();
person.Name = "Alice";
person.Age = 30;
person.DisplayInfo(); // Output: Name: Alice, Age: 30
```

## Constructors

Constructors are special methods called when an object is instantiated. They initialize the object’s state. A class can have multiple constructors with different parameters (constructor overloading).

### Default Constructor

A default constructor has no parameters:

```csharp
public Person()
{
    Name = "Unknown";
    Age = 0;
}
```

### Parameterized Constructor

A parameterized constructor allows you to set properties when creating the object:

```csharp
public Person(string name, int age)
{
    Name = name;
    Age = age;
}

Person person = new Person("Alice", 30);
person.DisplayInfo(); // Output: Name: Alice, Age: 30
```

## Properties

Properties provide a flexible mechanism to read, write, or compute the values of private fields. They are defined using `get` and `set` accessors.

### Auto-Implemented Properties

For simple properties, you can use auto-implemented properties:

```csharp
public class Person
{
    public string Name { get; set; }
    public int Age { get; set; }

    public void DisplayInfo()
    {
        Console.WriteLine($"Name: {Name}, Age: {Age}");
    }
}
```

### Read-Only Properties

Read-only properties are useful when you want to allow read access but restrict write access:

```csharp
public class Person
{
    public string Name { get; private set; }
    public int Age { get; private set; }

    public Person(string name, int age)
    {
        Name = name;
        Age = age;
    }

    public void DisplayInfo()
    {
        Console.WriteLine($"Name: {Name}, Age: {Age}");
    }
}
```

## Methods

Methods define the behavior of objects. They can take parameters and return values. Methods can also be overloaded, meaning multiple methods can have the same name but different parameters.

### Defining Methods

```csharp
public class Calculator
{
    public int Add(int a, int b)
    {
        return a + b;
    }

    public double Add(double a, double b)
    {
        return a + b;
    }
}
```

### Using Methods

```csharp
Calculator calculator = new Calculator();
int sumInt = calculator.Add(2, 3); // Calls Add(int, int)
double sumDouble = calculator.Add(2.5, 3.5); // Calls Add(double, double)
Console.WriteLine($"Integer Sum: {sumInt}, Double Sum: {sumDouble}"); // Output: Integer Sum: 5, Double Sum: 6
```

## The `this` Keyword

The `this` keyword refers to the current instance of the class. It is useful for differentiating between class fields and parameters with the same name.

### Using `this` in a Constructor

```csharp
public class Person
{
    public string Name { get; set; }
    public int Age { get; set; }

    public Person(string name, int age)
    {
        this.Name = name;
        this.Age = age;
    }

    public void DisplayInfo()
    {
        Console.WriteLine($"Name: {Name}, Age: {Age}");
    }
}
```

### Chaining Constructors with `this`

```csharp
public class Person
{
    public string Name { get; set; }
    public int Age { get; set; }

    public Person() : this("Unknown", 0) { }

    public Person(string name, int age)
    {
        this.Name = name;
        this.Age = age;
    }

    public void DisplayInfo()
    {
        Console.WriteLine($"Name: {Name}, Age: {Age}");
    }
}
```

## Object-Oriented Principles

### Encapsulation

Encapsulation is the bundling of data (fields) and methods that operate on the data into a single unit (class). It restricts direct access to some of an object’s components.

### Inheritance

Inheritance allows a class (derived class) to inherit fields and methods from another class (base class):

```csharp
public class Person
{
    public string Name { get; set; }
    public int Age { get; set; }

    public void DisplayInfo()
    {
        Console.WriteLine($"Name: {Name}, Age: {Age}");
    }
}

public class Student : Person
{
    public string School { get; set; }
}

Student student = new Student();
student.Name = "Alice";
student.Age = 20;
student.School = "XYZ University";
student.DisplayInfo(); // Output: Name: Alice, Age: 20
Console.WriteLine($"School: {student.School}"); // Output: School: XYZ University
```

### Polymorphism

Polymorphism allows methods to do different things based on the object it is acting upon, typically through method overriding and interfaces.

#### Method Overriding

```csharp
public class Person
{
    public virtual void DisplayInfo()
    {
        Console.WriteLine("Person DisplayInfo");
    }
}

public class Student : Person
{
    public override void DisplayInfo()
    {
        Console.WriteLine("Student DisplayInfo");
    }
}

Person person = new Person();
person.DisplayInfo(); // Output: Person DisplayInfo

Person student = new Student();
student.DisplayInfo(); // Output: Student DisplayInfo
```

## Conclusion

Creating and using objects is central to programming in C#. By defining classes and creating objects, you can encapsulate data and behavior, promote code reuse, and implement object-oriented principles such as encapsulation, inheritance, and polymorphism. This chapter has provided an overview of how to define classes, create objects, use constructors and methods, and leverage the `this` keyword for more readable and maintainable code.
