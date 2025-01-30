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
6. **Write a Dart function called `sum`**
   - The function should take two integer parameters and return their sum.

7. **Write a Dart function called `printEvenNumbers`**
   - The function should take an integer parameter `limit` and print all even numbers from 1 to `limit`.
   - Test the function by calling it with different values.

8. **Create a Dart function called `printEmployeeInfo`**
   - The function should take a named parameter `employee` of type `Map<String, dynamic>`.
   - The `employee` map should have keys such as `'name'`, `'age'`, `'designation'`, etc., with their corresponding values.
   - Inside the function, print the employee's information in a structured format.

9. **Create a Dart function called `printUserInfo`**
   - The function should take named parameters `name`, `age`, and `address`.
   - The function should print the user's information in a formatted way.

---
