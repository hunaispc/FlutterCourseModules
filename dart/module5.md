# Dart Programming: Functions

## Overview
A function is a group of statements that together perform a task. Functions help in reducing code redundancy and improving modularity.

---
## **Function Structure**
A function generally follows this format:
```dart
ReturnType FunctionName(ArgumentType name) {
    // Function code
}
```

---
## **Types of Functions**
### **1. Function Without Arguments and Without Return Value**
A function that does not accept parameters and does not return any value.

#### **Example:**
```dart
void sum() {
    int a = 10;
    int b = 20;
    int total = a + b;
    print(total);
}

void main() {
    sum();
}
```

---
### **2. Function With Arguments and Without Return Value**
A function that accepts parameters but does not return any value.

#### **Example:**
```dart
void sum(int a, int b) {
    int total = a + b;
    print(total);
}

void main() {
    int a = 10;
    int b = 20;
    sum(a, b);
}
```

---
### **3. Function With Arguments and With Return Value**
A function that accepts parameters and returns a value.

#### **Example:**
```dart
int sum(int a, int b) {
    int total = a + b;
    return total;
}

void main() {
    int a = 10;
    int b = 20;
    int c = sum(a, b);
    print(c);
}
```

---
### **4. Function Without Arguments and With Return Value**
A function that does not accept parameters but returns a value.

#### **Example:**
```dart
int sum() {
    int a = 10;
    int b = 20;
    int total = a + b;
    return total;
}

void main() {
    int c = sum();
    print(c);
}
```

---
## **Practical Questions**
1. Write a Dart function that takes a list of integers as a parameter and returns the sum of all the numbers in the list.
2. Write a Dart function that takes a string as a parameter and returns the number of characters in the string.
3. Write a Dart function that takes a list of integers as a parameter and returns a new list with all the even numbers from the original list.
4. Write a Dart function that takes a list of strings as a parameter and returns a new list with all the strings in uppercase.
5. Write a Dart function that takes one integer as a parameter and returns its multiplication table.

---
