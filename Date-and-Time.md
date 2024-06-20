# Chapter: Date and Time in C#

## Introduction

Working with dates and times is a common requirement in many applications. C# provides a robust set of classes and methods for handling date and time values. This chapter will cover the `DateTime`, `TimeSpan`, and `DateTimeOffset` structures, as well as formatting, parsing, and manipulating date and time values.

## The DateTime Structure

### Creating DateTime Instances

The `DateTime` structure represents dates and times. You can create `DateTime` instances in several ways:

```csharp
// Using the constructor
DateTime date1 = new DateTime(2024, 6, 19); // Year, Month, Day
DateTime date2 = new DateTime(2024, 6, 19, 14, 30, 0); // Year, Month, Day, Hour, Minute, Second

// Using static properties
DateTime now = DateTime.Now; // Current date and time
DateTime today = DateTime.Today; // Current date, time set to 00:00:00
DateTime utcNow = DateTime.UtcNow; // Current date and time in UTC
```

### Accessing DateTime Components

You can access various components of a `DateTime` instance:

```csharp
DateTime date = new DateTime(2024, 6, 19, 14, 30, 0);
int year = date.Year; // 2024
int month = date.Month; // 6
int day = date.Day; // 19
int hour = date.Hour; // 14
int minute = date.Minute; // 30
int second = date.Second; // 0
DayOfWeek dayOfWeek = date.DayOfWeek; // Wednesday
```

## Formatting and Parsing Dates

### Formatting Dates

You can format `DateTime` instances as strings using the `ToString` method with format specifiers:

```csharp
DateTime date = new DateTime(2024, 6, 19, 14, 30, 0);
string formattedDate = date.ToString("yyyy-MM-dd HH:mm:ss"); // "2024-06-19 14:30:00"
```

Common format specifiers:
- `"d"`: Short date pattern
- `"D"`: Long date pattern
- `"t"`: Short time pattern
- `"T"`: Long time pattern
- `"f"`: Full date/time pattern (short time)
- `"F"`: Full date/time pattern (long time)
- `"g"`: General date/time pattern (short time)
- `"G"`: General date/time pattern (long time)
- `"M"`: Month/day pattern
- `"Y"`: Year/month pattern

### Parsing Dates

You can parse strings into `DateTime` instances using the `Parse` and `TryParse` methods:

```csharp
string dateString = "2024-06-19 14:30:00";
DateTime date = DateTime.Parse(dateString);

string invalidDateString = "invalid date";
bool success = DateTime.TryParse(invalidDateString, out DateTime result); // success is false
```

## Manipulating Dates

### Adding and Subtracting

You can add or subtract time from `DateTime` instances using various methods:

```csharp
DateTime date = new DateTime(2024, 6, 19);

// Adding
DateTime newDate = date.AddDays(5); // 2024-06-24
newDate = date.AddMonths(1); // 2024-07-19
newDate = date.AddYears(1); // 2025-06-19
newDate = date.AddHours(2); // 2024-06-19 02:00:00

// Subtracting
newDate = date.AddDays(-5); // 2024-06-14
```

### Calculating Differences

You can calculate the difference between two `DateTime` instances using the `Subtract` method or the `-` operator, which returns a `TimeSpan`:

```csharp
DateTime startDate = new DateTime(2024, 6, 19, 14, 30, 0);
DateTime endDate = new DateTime(2024, 6, 20, 14, 30, 0);
TimeSpan difference = endDate - startDate; // 1.00:00:00 (1 day)

int days = difference.Days; // 1
int hours = difference.Hours; // 0
int minutes = difference.Minutes; // 0
```

## TimeSpan Structure

The `TimeSpan` structure represents a time interval. You can create `TimeSpan` instances in several ways:

```csharp
// Using the constructor
TimeSpan duration1 = new TimeSpan(1, 0, 0); // 1 hour
TimeSpan duration2 = new TimeSpan(1, 30, 0); // 1 hour, 30 minutes

// Using static methods
TimeSpan duration3 = TimeSpan.FromHours(1.5); // 1 hour, 30 minutes
TimeSpan duration4 = TimeSpan.FromMinutes(90); // 1 hour, 30 minutes
```

### Adding and Subtracting TimeSpans

You can add or subtract `TimeSpan` instances:

```csharp
TimeSpan time1 = new TimeSpan(1, 30, 0); // 1 hour, 30 minutes
TimeSpan time2 = new TimeSpan(0, 45, 0); // 45 minutes
TimeSpan result = time1 + time2; // 2 hours, 15 minutes
result = time1 - time2; // 45 minutes
```

### Comparing TimeSpans

You can compare `TimeSpan` instances using comparison operators or methods:

```csharp
TimeSpan time1 = new TimeSpan(1, 30, 0); // 1 hour, 30 minutes
TimeSpan time2 = new TimeSpan(0, 45, 0); // 45 minutes

bool isEqual = time1 == time2; // false
bool isGreater = time1 > time2; // true
int comparison = time1.CompareTo(time2); // 1 (greater than)
```

## DateTimeOffset Structure

The `DateTimeOffset` structure represents a point in time, typically expressed as a date and time of day, relative to Coordinated Universal Time (UTC). It includes a `DateTime` value and an offset.

### Creating DateTimeOffset Instances

You can create `DateTimeOffset` instances in several ways:

```csharp
// Using the constructor
DateTimeOffset dateTimeOffset1 = new DateTimeOffset(2024, 6, 19, 14, 30, 0, TimeSpan.FromHours(-7)); // Local time with offset

// Using static properties
DateTimeOffset now = DateTimeOffset.Now; // Current date and time with offset
DateTimeOffset utcNow = DateTimeOffset.UtcNow; // Current date and time in UTC
```

### Converting Between DateTime and DateTimeOffset

You can convert between `DateTime` and `DateTimeOffset`:

```csharp
DateTime dateTime = new DateTime(2024, 6, 19, 14, 30, 0);
DateTimeOffset dateTimeOffset = new DateTimeOffset(dateTime);

// Adjusting to a different time zone
DateTimeOffset localTime = dateTimeOffset.ToLocalTime();
DateTimeOffset utcTime = dateTimeOffset.ToUniversalTime();
```

## Time Zones

### TimeZoneInfo Class

The `TimeZoneInfo` class provides methods for working with time zones:

```csharp
// Get the local time zone
TimeZoneInfo localZone = TimeZoneInfo.Local;
Console.WriteLine(localZone.DisplayName);

// Get the UTC time zone
TimeZoneInfo utcZone = TimeZoneInfo.Utc;

// Convert time between time zones
DateTime utcTime = DateTime.UtcNow;
DateTime localTime = TimeZoneInfo.ConvertTimeFromUtc(utcTime, localZone);
```

### Working with Specific Time Zones

You can work with specific time zones by their identifiers:

```csharp
TimeZoneInfo easternZone = TimeZoneInfo.FindSystemTimeZoneById("Eastern Standard Time");
DateTime utcTime = DateTime.UtcNow;
DateTime easternTime = TimeZoneInfo.ConvertTimeFromUtc(utcTime, easternZone);
```

## Conclusion

Handling dates and times is a crucial part of many applications. C# provides a comprehensive set of tools and classes, such as `DateTime`, `TimeSpan`, and `DateTimeOffset`, to work with date and time values effectively. This chapter has covered creating, formatting, parsing, and manipulating dates and times, as well as working with time zones and intervals. Understanding these concepts will enable you to handle date and time data accurately and efficiently in your applications.
