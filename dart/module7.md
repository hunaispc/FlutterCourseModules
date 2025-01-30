# Dart: Classes and Objects

## Introduction
In Dart, a **class** is a blueprint for creating objects. It contains variables, functions (methods), constructors, and more. An **object** is an instance of a class, meaning it represents a specific implementation of the class.

## Class and Object

### Syntax for Creating a Class
```dart
class ClassName {
  // Variables (properties)
  // Constructors
  // Methods (functions)
}
```

### Example: Class with Required Parameters
```dart
class Student {
  final String name;
  final String email;

  Student({required this.name, required this.email});

  void printDetails() {
    print("Name: $name");
    print("Email: $email");
  }
}

void main() {
  Student student = Student(name: "Arun", email: "abc@gmail.com");
  student.printDetails();
}
```

### Example: Class with Optional Parameters
```dart
class Student {
  final String? name;
  final String? email;

  Student([this.name, this.email]);

  void printDetails() {
    print("Name: $name");
  }
}

void main() {
  Student student = Student("Arun");
  student.printDetails();
}
```

### Example: Class with Both Required and Optional Parameters
```dart
class Student {
  final String name;
  final String? email;

  Student({required this.name, this.email});

  void printDetails() {
    print("Name: $name");
  }
}

void main() {
  Student student = Student(name: "Arun");
  student.printDetails();
}
```

## Practical Questions

1. Write a class in Dart that represents a **Person**. The `Person` class should have properties for:
   - Name
   - Age
   - Address

2. Write a method (function) in the `Person` class that returns the person's **name and age** as a string.

3. Write a class in Dart that represents a **Car**. The `Car` class should have properties for:
   - Model
   - Year
   - Color

4. Write a method (function) in the `Car` class that returns the car **color** as a string.

---
