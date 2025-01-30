# Dart Programming: Operators, Decision Making, and Loops

## Overview
This repository provides a comprehensive guide to relational operators, logical operators, decision-making statements, and loops in Dart with examples.

---
## **Relational Operators**
Relational operators compare values and return a boolean result.

### **List of Relational Operators:**
1. `>` (Greater than) - Returns `true` if the left operand is greater than the right operand.
2. `<` (Less than) - Returns `true` if the left operand is smaller than the right operand.
3. `>=` (Greater than or equal to) - Returns `true` if the left operand is greater than or equal to the right operand.
4. `<=` (Less than or equal to) - Returns `true` if the left operand is less than or equal to the right operand.
5. `==` (Equal to) - Returns `true` if both operands are equal.
6. `!=` (Not equal to) - Returns `true` if both operands are not equal.

### **Example:**
```dart
int a = 10;
int b = 20;
print(a > b);  // false
print(a < b);  // true
print(a == 10); // true
```

---
## **Logical Operators**
Logical operators are used to combine multiple conditions.

### **List of Logical Operators:**
1. `&&` (AND) - Returns `true` if both conditions are `true`.
2. `||` (OR) - Returns `true` if at least one condition is `true`.
3. `!` (NOT) - Reverses the boolean value.

### **Example:**
```dart
bool x = true;
bool y = false;
print(x && y);  // false
print(x || y);  // true
print(!x);      // false
```

---
## **Decision Making Statements**
Decision-making statements allow conditional execution of code.

### **1. if-else Statement**
```dart
int a = 10;
int b = 20;
if (a > b) {
    print("a is greater");
} else {
    print("b is greater");
}
```

### **2. if-else-if Statement**
```dart
int marks = 74;
if (marks > 85) {
    print("Excellent");
} else if (marks > 75) {
    print("Very Good");
} else if (marks > 65) {
    print("Good");
} else {
    print("Average");
}
```

### **3. Nested if-else Statement**
```dart
int a = 10, b = 20, c = 30;
if (a > b) {
    if (a > c) {
        print("a is greatest");
    } else {
        print("c is greatest");
    }
} else if (b > c) {
    print("b is greatest");
} else {
    print("c is greatest");
}
```

### **4. Switch Case Statement**
```dart
void main() {
    int n = 3;
    switch (n) {
        case 1:
            print("Value is 1");
            break;
        case 2:
            print("Value is 2");
            break;
        case 3:
            print("Value is 3");
            break;
        default:
            print("Out of range");
    }
}
```

---
## **Loops in Dart**
Loops are used to execute a set of statements repeatedly.

### **1. For Loop**
```dart
for (int i = 1; i <= 100; i++) {
    print(i);
}
```

### **2. While Loop**
```dart
int i = 1;
while (i <= 100) {
    print(i);
    i++;
}
```

### **3. Do-While Loop**
```dart
int i = 1;
do {
    print(i);
    i++;
} while (i <= 100);
```

---
## **Practical Questions**
1. Pick the first and last element from a list and print their sum.
2. Write a program to check whether a student has passed or failed (pass mark for a subject is 50 out of 100).
3. Write a program to print even numbers between 1-100.
4. Write a program to print the multiplication table of number 5.
5. Write a program to print the sum of even numbers between 1-100.
6. Given `List<int> a = [12,30,65,34,10,13,15]`, print the even numbers from this list.
7. Given `List<int> a = [12,30,65,34,10,13,15]`, print the sum of odd numbers from this list.
8. Write a program to display which fruit is contained in the following variable using a switch statement:
   ```dart
   String fruit = "apple";
   ```
9. Write a program to print the multiplication table of 5 with the format:
   ```
   1 x 5 = 5
   2 x 5 = 10
   3 x 5 = 15
   ...
   10 x 5 = 50
   ```

---
