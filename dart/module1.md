# Dart Basics

## Variables
Variables are containers for storing data.

### Format:
```dart
DataType name;
```

## Data Types in Dart

### 1. String
Used for storing string-type data.
```dart
String a = "flutter";
String a = 'flutter';
```

### 2. int
Used for storing integer numbers.
```dart
int a = 10;
```

### 3. double
Used for storing floating-point numbers.
```dart
double a = 10.5;
```

### 4. num
Used for storing both integer and floating-point numbers.
```dart
num a = 10;
num a = 10.5;
```

### 5. bool
Used for storing `true` or `false` values.
```dart
bool a = true;
bool a = false;
```

### 6. var
Can store any type of data.
```dart
var a = 10;
var a = 10.5;
var a = 'flutter';
var a = true;
```

### 7. dynamic
Can store any type of data, and its type can change at runtime.
```dart
dynamic a = 10;
dynamic a = 10.5;
dynamic a = 'flutter';
dynamic a = true;
```

### 8. List
Used for storing a list of data.

#### Format:
```dart
List<value_data_type> name = [];
```
#### Examples:
```dart
List<int> a = [10, 20, 30];
List<String> a = ['Arun', 'Amal', 'Ajith'];
List<dynamic> a = ['Arun', 20, 10.5, true];
```

### 9. Map
Used for storing a list of data with key-value pairs.

#### Format:
```dart
Map<key_data_type, value_data_type> name = {};
```
#### Examples:
```dart
Map<String, String> a = {
  'name': 'Arun',
  'place': 'Kottakal'
};
Map<String, dynamic> a = {
  'name': 'Arun',
  'mark': 40,
  'passed': true
};
```

## Difference Between `var` and `dynamic`
```dart
dynamic a = 10;  // Output: 10
a = 'Arun';  // Output: Arun

var a = 10;  // Output: 10
a = 'Arun';  // Output: Error
a = 20;  // Output: 20
```

### Final Keyword
`final` is used to declare a constant value that cannot be reassigned.
```dart
final a = 10;  // Output: 10
a = 'Arun';  // Output: Error
a = 20;  // Output: Error
```

## Operators in Dart
### 1. Arithmetic Operators
```dart
+ , - , * , / , %
```

### 2. Relational Operators
```dart
== , != , > , < , >= , <=
```

### 3. Logical Operators
```dart
&& , || , !
```

## Practical Questions

### 1. Print total of two variables
Given:
- `a = 10`
- `b = 20`

### 2. Calculate Simple Interest
Given:
- Principal amount = 12000
- Interest Rate = 10%
- Number of years = 2

Formula:
```dart
(Principal amount * Interest Rate * Number of years) / 100
```

### 3. Print full name from first and last name
Given:
- First name = 'Ali'
- Last name = 'Althaf'

### 4. Swap Two Numbers
Given:
- `a = 10`
- `b = 20`

### 5. Split Restaurant Bill
Given:
- Total bill amount = 1200
- Number of people = 10

Formula:
```dart
total bill amount / number of people
```
