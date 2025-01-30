# Dart Programming: Working with Maps and Lists

## Overview
This guide provides a detailed explanation of how to retrieve values from Maps and Lists in Dart, along with practical questions for hands-on practice.

---
## **Getting Values from a Map**
Values can be accessed from a Map using its keys.

### **Example:**
```dart
Map<String, dynamic> person = { "name": "John", "age": 22 };
print(person["age"]);  // Output: 22
```

---
## **Getting Values from a List**
Values can be accessed from a List using their index positions.

### **Example:**
```dart
List<int> numbers = [10, 20, 30, 40];
print(numbers[1]);  // Output: 20
```

---
## **Practical Questions**
### **Map Operations**
1. Given the following Map:
   ```dart
   Map<String, dynamic> student = { "name": "John", "age": 22, "marks": [30, 50, 60] };
   ```
   - Print the marks of John.

2. Given the following Map:
   ```dart
   Map<String, dynamic> fruits = { "category": "fruits", "items": ["apple", "orange", "pineapple", "grapes"] };
   ```
   - Check if the items list contains "grapes" and print `true` if it does.

3. Given the following Map:
   ```dart
   Map<String, dynamic> a = { "name": "John", "numbers": [20, 23, 26, 29, 31, 32] };
   ```
   - Print all even numbers in the numbers list.

4. Given the following Map:
   ```dart
   Map<String, dynamic> item = { "name": "John", "prices": [230, 100, 310, 320] };
   ```
   - Print the total price.

5. Given the following List of Maps:
   ```dart
   List<Map> a = [
     { "name": "John", "numbers": [20, 23, 26, 29, 31, 32] },
     { "name": "John", "prices": [230, 100, 310, 320] }
   ];
   ```
   - Print the prices and marks.

### **Nested Map Operations**
6. Given the following List of Maps:
   ```dart
   List<Map> student = [
   { 
      "name": "John", 
      "marks": [ 
               {  
                   "chemistry": 60,
                   "physics": 70,
                   "maths": 30
                 }
                ],
     "address": { 
                             "place": "Kottakkal",
                             "district": "Malappuram",
                             "pincode": 676120
                           } 
    }
   ];
   ```
   (a) Print the place of John.
   (b) Print the mark in physics of John.
   (c) Print the total marks of John.

7. Given the following List of Maps with multiple students:
   ```dart
   List<Map> student = [ 
   { 
      "name": "John", 
      "marks": [ 
               {  
                   "chemistry": 60,
                   "physics": 70,
                   "maths": 30
                 }
                ],
     "address": { 
                             "place": "Kottakkal",
                             "district": "Malappuram",
                             "pincode": 676120
                           } 
   },
   { 
      "name": "Arun", 
      "marks": [ 
               {  
                   "chemistry": 40,
                   "physics": 80,
                   "maths": 50
                 }
                ],
     "address": { 
                             "place": "Edarikode",
                             "district": "Malappuram",
                             "pincode": 676120
                           } 
   }
   ];
   ```
   (a) Print the pincode of Arun.
   (b) Print the mark in physics of John.
   (c) Print the total marks of Arun.
   (d) Print the total marks of John.
   (e) Print the first rank holder's name based on their total marks.

---
