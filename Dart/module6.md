
## Null Safety in Dart

Null safety prevents errors that result from unintentional access of variables set to null. For example, if a function expects an integer but receives null, your app may cause a runtime error.

### Variable Types in Dart
1. **Nullable Variable:**
   ```dart
   String? name;
   ```
2. **Non-Nullable Variable:**
   ```dart
   String name = "arun";
   ```

## Types Of Function Parameters in Dart

### 1. Optional Parameters
Optional parameters do not require us to supply a value when calling a function.

#### (a) Positional Optional Parameters
A parameter wrapped by `[]` is a positional optional parameter.
   ```dart
   void sum([int? a, int? b]) {
      // Function body
   }
   
   // Function calling
   sum(5, 10);
   ```

#### (b) Named Optional Parameters
A parameter wrapped by `{}` is a named optional parameter.
   ```dart
   void sum({int? a, int? b}) {
      // Function body
   }
   
   // Function calling
   sum(a: 5, b: 10);
   ```

### 2. Required Parameters
All parameters must be supplied when calling the function to avoid compiler errors.

#### (a) Positional Required Parameters
A parameter written inside `()` is a positional required parameter.
   ```dart
   void sum(int a, int b) {
      // Function body
   }
   
   // Function calling
   sum(5, 10);
   ```

#### (b) Named Required Parameters
A parameter wrapped by `{}` and marked as `required` is a named required parameter.
   ```dart
   void sum({required int a, required int b}) {
      // Function body
   }
   
   // Function calling
   sum(a: 5, b: 10);
   ```

## Function Examples

### 1. Function with Positional Optional Parameters
   ```dart
   void student([String? name, String? age]) {
      print(name);
      print(age);
   }
   
   void main() {
      student("arun");
   }
   ```

### 2. Function with Named Optional Parameters
   ```dart
   void student({String? name, String? age}) {
      print(name);
      print(age);
   }
   
   void main() {
      student(name: "arun");
   }
   ```

### 3. Function with Positional Required Parameters
   ```dart
   void student(String name, String age) {
      print(name);
      print(age);
   }
   
   void main() {
      student("arun", "19");
   }
   ```

### 4. Function with Named Required Parameters
   ```dart
   void student({required String name, required String age}) {
      print(name);
      print(age);
   }
   
   void main() {
      student(name: "arun", age: "19");
   }
   ```

### 5. Function with Both Required and Optional Parameters
   ```dart
   void student({required String name, String? age}) {
      print(name);
   }
   
   void main() {
      student(name: "arun");
   }
   ```

## Practical Questions

1. **Create a function named `greetUser`**
   - The function should take a required parameter `name` and a required parameter `greeting`.
   - The function should return a string that greets the user by name with the specified greeting.
   - Example output: `Hi John`

2. **Create a function named `greetUser`**
   - The function should take a required parameter `name` and an optional parameter `greeting`.
   - The function should return a string that greets the user by name.
   - Example output: `John`


