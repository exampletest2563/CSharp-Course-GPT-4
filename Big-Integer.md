# Chapter: Big Integer in C#

## Introduction

In many applications, the default integer types provided by C# (`int`, `long`, etc.) may not be sufficient to handle extremely large numbers. For such scenarios, C# provides the `BigInteger` structure, which is part of the `System.Numerics` namespace. This chapter covers the usage of `BigInteger`, including creation, arithmetic operations, comparisons, and other advanced techniques.

## The BigInteger Structure

The `BigInteger` structure represents an arbitrarily large signed integer. It is part of the `System.Numerics` namespace, so you need to add a reference to `System.Numerics.dll` and include the namespace in your code:

```csharp
using System.Numerics;
```

### Creating BigInteger Instances

You can create `BigInteger` instances in several ways:

```csharp
using System;
using System.Numerics;

// From an integer
BigInteger bigInt1 = new BigInteger(123456789);

// From a long
BigInteger bigInt2 = new BigInteger(9876543210L);

// From a string
BigInteger bigInt3 = BigInteger.Parse("123456789012345678901234567890");

// From a byte array (little-endian)
byte[] bytes = { 1, 0, 0, 0 }; // Represents 1
BigInteger bigInt4 = new BigInteger(bytes);

// From hexadecimal string
BigInteger bigInt5 = BigInteger.Parse("1A2B3C4D5E6F", System.Globalization.NumberStyles.HexNumber);
```

## Arithmetic Operations

The `BigInteger` structure supports all standard arithmetic operations, including addition, subtraction, multiplication, division, and modulus.

### Basic Operations

```csharp
BigInteger a = new BigInteger(1234567890123456789);
BigInteger b = new BigInteger(9876543210987654321);

BigInteger sum = a + b; // Addition
BigInteger difference = b - a; // Subtraction
BigInteger product = a * b; // Multiplication
BigInteger quotient = b / a; // Division
BigInteger remainder = b % a; // Modulus

Console.WriteLine($"Sum: {sum}");
Console.WriteLine($"Difference: {difference}");
Console.WriteLine($"Product: {product}");
Console.WriteLine($"Quotient: {quotient}");
Console.WriteLine($"Remainder: {remainder}");
```

### Interesting Example: Factorials

Calculating the factorial of large numbers is a common use case for `BigInteger`:

```csharp
BigInteger Factorial(int n)
{
    BigInteger result = BigInteger.One;
    for (int i = 1; i <= n; i++)
    {
        result *= i;
    }
    return result;
}

int num = 100;
BigInteger factorialOfNum = Factorial(num);
Console.WriteLine($"Factorial of {num}: {factorialOfNum}");
```

## Comparisons

You can compare `BigInteger` instances using standard comparison operators and methods:

```csharp
BigInteger a = new BigInteger(1234567890123456789);
BigInteger b = new BigInteger(9876543210987654321);

bool isEqual = a == b;
bool isNotEqual = a != b;
bool isLessThan = a < b;
bool isGreaterThan = a > b;
bool isLessThanOrEqual = a <= b;
bool isGreaterThanOrEqual = a >= b;

Console.WriteLine($"a == b: {isEqual}");
Console.WriteLine($"a != b: {isNotEqual}");
Console.WriteLine($"a < b: {isLessThan}");
Console.WriteLine($"a > b: {isGreaterThan}");
Console.WriteLine($"a <= b: {isLessThanOrEqual}");
Console.WriteLine($"a >= b: {isGreaterThanOrEqual}");
```

## Conversions

The `BigInteger` structure provides methods to convert between different numeric types:

### Converting to Other Types

```csharp
BigInteger bigInt = new BigInteger(1234567890123456789);

int intValue = (int)bigInt; // May overflow
long longValue = (long)bigInt; // May overflow
double doubleValue = (double)bigInt; // May lose precision
decimal decimalValue = (decimal)bigInt; // May lose precision

Console.WriteLine($"Int value: {intValue}");
Console.WriteLine($"Long value: {longValue}");
Console.WriteLine($"Double value: {doubleValue}");
Console.WriteLine($"Decimal value: {decimalValue}");
```

### Converting from Other Types

```csharp
int intValue = 12345;
BigInteger fromInt = new BigInteger(intValue);

long longValue = 1234567890L;
BigInteger fromLong = new BigInteger(longValue);

double doubleValue = 12345.6789;
BigInteger fromDouble = new BigInteger(doubleValue);

decimal decimalValue = 1234567890.1234567890M;
BigInteger fromDecimal = new BigInteger(decimalValue);

Console.WriteLine($"From int: {fromInt}");
Console.WriteLine($"From long: {fromLong}");
Console.WriteLine($"From double: {fromDouble}");
Console.WriteLine($"From decimal: {fromDecimal}");
```

## Advanced BigInteger Features

### Bitwise Operations

`BigInteger` supports bitwise operations such as AND, OR, XOR, and NOT:

```csharp
BigInteger a = new BigInteger(0b1010); // Binary 1010
BigInteger b = new BigInteger(0b1100); // Binary 1100

BigInteger andResult = a & b; // Binary 1000
BigInteger orResult = a | b; // Binary 1110
BigInteger xorResult = a ^ b; // Binary 0110
BigInteger notResult = ~a; // Binary 0101 (bitwise NOT)

Console.WriteLine($"AND: {andResult}");
Console.WriteLine($"OR: {orResult}");
Console.WriteLine($"XOR: {xorResult}");
Console.WriteLine($"NOT: {notResult}");
```

### Interesting Example: Large Exponentiation

Calculating large powers of numbers:

```csharp
BigInteger baseNum = new BigInteger(2);
int exponent = 1000;
BigInteger result = BigInteger.Pow(baseNum, exponent);
Console.WriteLine($"2^1000: {result}");
```

### GCD and LCM

Calculating the greatest common divisor (GCD) and least common multiple (LCM):

```csharp
BigInteger GCD(BigInteger a, BigInteger b)
{
    while (b != 0)
    {
        BigInteger temp = b;
        b = a % b;
        a = temp;
    }
    return a;
}

BigInteger LCM(BigInteger a, BigInteger b)
{
    return (a * b) / GCD(a, b);
}

BigInteger num1 = new BigInteger(1234567890123456789);
BigInteger num2 = new BigInteger(9876543210987654321);

BigInteger gcd = GCD(num1, num2);
BigInteger lcm = LCM(num1, num2);

Console.WriteLine($"GCD: {gcd}");
Console.WriteLine($"LCM: {lcm}");
```

## Performance Considerations

While `BigInteger` provides powerful capabilities for handling large numbers, it comes with performance overhead. For operations involving extremely large numbers or requiring high performance, consider using specialized libraries or algorithms optimized for large integer arithmetic.

## Conclusion

The `BigInteger` structure in C# allows for the representation and manipulation of arbitrarily large integers, providing a robust solution for applications that require working with large numbers. This chapter has covered the basics of creating and manipulating `BigInteger` instances, performing arithmetic and bitwise operations, and handling advanced scenarios. By leveraging the capabilities of `BigInteger`, you can handle complex numerical computations in your C# projects with ease and precision.
