# Dart Data Types, Properties, and Methods

## Data Types Overview
Dart provides various data types with specific properties and methods. Below is a detailed guide with examples.

---
## 1. **String**
### Properties:
- `isEmpty` - Returns `true` if the string is empty.
- `isNotEmpty` - Returns `true` if the string is not empty.
- `length` - Returns the number of characters in the string.

### Methods:
- `toLowerCase()` - Converts all characters in a string to lowercase.
- `toUpperCase()` - Converts all characters in a string to uppercase.
- `trim()` - Removes leading and trailing whitespaces.
- `split(pattern)` - Splits the string at the specified pattern and returns a list.
- `replaceAll(from, to)` - Replaces all occurrences of a substring with another substring.

### Example:
```dart
String name = "  John Doe  ";
print(name.length); // Output: 10
print(name.toLowerCase()); // Output: john doe
print(name.toUpperCase()); // Output: JOHN DOE
print(name.trim()); // Output: John Doe
print(name.replaceAll("John", "Jane")); // Output: Jane Doe
```

---
## 2. **int / double**
### Properties:
- `isEven` - Returns `true` if the number is even.
- `isOdd` - Returns `true` if the number is odd.
- `isNegative` - Returns `true` if the number is negative.
- `isPositive` - Returns `true` if the number is positive.

### Methods:
- `round()` - Returns the value of a number rounded to the nearest integer.
- `ceil()` - Rounds the number up to the nearest integer.
- `floor()` - Rounds the number down to the nearest integer.
- `abs()` - Returns the absolute value of the number.

### Example:
```dart
int number = -10;
double decimal = 10.6;
print(number.isEven); // Output: true
print(number.isOdd); // Output: false
print(decimal.round()); // Output: 11
print(decimal.ceil()); // Output: 11
print(decimal.floor()); // Output: 10
print(number.abs()); // Output: 10
```

---
## 3. **List**
### Properties:
- `first` - Returns the first element of the list.
- `isEmpty` - Returns `true` if the list is empty.
- `isNotEmpty` - Returns `true` if the list is not empty.
- `length` - Returns the number of elements in the list.
- `last` - Returns the last element of the list.

### Methods:
- `add(value)` - Adds an element to the list.
- `insert(index, value)` - Inserts an element at a specific position.
- `remove(value)` - Removes an element from the list.
- `removeAt(index)` - Removes an element at a specified index.
- `contains(value)` - Checks if the list contains a specific value.
- `reversed` - Returns an iterable of the reversed list.

### Example:
```dart
List<int> numbers = [1, 2, 3, 4, 5];
numbers.add(6);
numbers.insert(3, 10);
numbers.remove(2);
numbers.removeAt(0);
print(numbers.contains(4)); // Output: true
print(numbers.reversed.toList()); // Output: [6, 5, 4, 10, 3]
```

---
## 4. **Map**
### Properties:
- `length` - Returns the number of key-value pairs in the map.
- `isEmpty` - Returns `true` if the map is empty.
- `isNotEmpty` - Returns `true` if the map is not empty.
- `keys` - Returns a list of all keys in the map.
- `values` - Returns a list of all values in the map.

### Methods:
- `addAll({key: value})` - Adds multiple key-value pairs to the map.
- `clear()` - Removes all elements from the map.
- `remove(key)` - Removes an element by key.
- `containsKey(key)` - Checks if the map contains a specific key.
- `containsValue(value)` - Checks if the map contains a specific value.

### Example:
```dart
Map<String, int> scores = {"Alice": 90, "Bob": 85};
scores["Charlie"] = 88;
scores.remove("Bob");
print(scores.containsKey("Alice")); // Output: true
print(scores.containsValue(85)); // Output: false
print(scores); // Output: {Alice: 90, Charlie: 88}
```

---
## Practical Questions
### String Operations
1. Declare a variable named `name`, assign it a string value, and print its length.
2. Create a list of 5 numbers and assign it to a variable named `numbers`.
3. Create a list of 6 numbers and check whether the 4th element is even or odd.
4. Create a list, extract its first and last elements into another list, and print it.
5. Create a list, remove its first and last elements, and print the updated list.

### Map Operations
6. Create two maps, merge the second map into the first, and print the result.
7. Create a map and print its keys.
8. Create a map and print its values.

### Complex Structures
9. Create a list that contains multiple maps and print it.
10. Create a map where one value is a list and print it.

---
