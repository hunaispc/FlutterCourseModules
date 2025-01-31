# Hive (NoSQL Storage) in Flutter

Hive is a lightweight and fast NoSQL database designed for Flutter and Dart applications. It provides a simple way to store and retrieve data without requiring complex configurations like SQLite.

## Why Use Hive?
- **Lightweight & Fast**
- **No Native Dependencies**
- **Efficient Key-Value Store**
- **Supports Complex Data Types**
- **Type Safety with Adapters**

## Getting Started
### Step 1: Add Dependencies
Add the following dependencies to your `pubspec.yaml` file:
```yaml
dependencies:
  flutter:
    sdk: flutter
  hive: ^2.2.3
  hive_flutter: ^1.1.0

dev_dependencies:
  hive_generator: ^2.0.0
  build_runner: ^2.3.2
```
Run:
```sh
flutter pub get
```

### Step 2: Initialize Hive
In your `main.dart` file, initialize Hive before running the app.

```dart
import 'package:flutter/material.dart';
import 'package:hive_flutter/hive_flutter.dart';

void main() async {
  WidgetsFlutterBinding.ensureInitialized();
  await Hive.initFlutter();
  runApp(MyApp());
}
```

### Step 3: Create a Data Model
Hive uses TypeAdapters to support complex objects. Define a model class and generate an adapter.

```dart
import 'package:hive/hive.dart';

part 'user.g.dart';

@HiveType(typeId: 0)
class User {
  @HiveField(0)
  final String name;

  @HiveField(1)
  final int age;

  User({required this.name, required this.age});
}
```

Run the following command to generate the adapter:
```sh
flutter pub run build_runner build
```

### Step 4: Register the Adapter
Before using the model, register it inside `main.dart`.

```dart
void main() async {
  WidgetsFlutterBinding.ensureInitialized();
  await Hive.initFlutter();
  Hive.registerAdapter(UserAdapter());
  runApp(MyApp());
}
```

## CRUD Operations with Hive

### Open a Box
A **Box** is a persistent storage container in Hive.
```dart
var box = await Hive.openBox('users');
```

### Create (Insert Data)
```dart
final userBox = Hive.box('users');
var user = User(name: 'John Doe', age: 25);
await userBox.put('user1', user);
```

### Read Data
```dart
User? retrievedUser = userBox.get('user1');
print(retrievedUser?.name);
```

### Update Data
```dart
var updatedUser = User(name: 'John Doe', age: 26);
await userBox.put('user1', updatedUser);
```

### Delete Data
```dart
await userBox.delete('user1');
```

## Full Code Example

```dart
import 'package:flutter/material.dart';
import 'package:hive_flutter/hive_flutter.dart';
import 'package:hive/hive.dart';

part 'user.g.dart';

@HiveType(typeId: 0)
class User {
  @HiveField(0)
  final String name;

  @HiveField(1)
  final int age;

  User({required this.name, required this.age});
}

void main() async {
  WidgetsFlutterBinding.ensureInitialized();
  await Hive.initFlutter();
  Hive.registerAdapter(UserAdapter());
  await Hive.openBox('users');
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: HomeScreen(),
    );
  }
}

class HomeScreen extends StatefulWidget {
  @override
  _HomeScreenState createState() => _HomeScreenState();
}

class _HomeScreenState extends State<HomeScreen> {
  final box = Hive.box('users');

  void addUser() {
    final user = User(name: 'Alice', age: 30);
    box.put('user1', user);
    setState(() {});
  }

  void updateUser() {
    final updatedUser = User(name: 'Alice', age: 31);
    box.put('user1', updatedUser);
    setState(() {});
  }

  void deleteUser() {
    box.delete('user1');
    setState(() {});
  }

  @override
  Widget build(BuildContext context) {
    final user = box.get('user1') as User?;
    return Scaffold(
      appBar: AppBar(title: Text('Hive Example')),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            if (user != null) Text('User: ${user.name}, Age: ${user.age}'),
            SizedBox(height: 20),
            ElevatedButton(onPressed: addUser, child: Text('Add User')),
            ElevatedButton(onPressed: updateUser, child: Text('Update User')),
            ElevatedButton(onPressed: deleteUser, child: Text('Delete User')),
          ],
        ),
      ),
    );
  }
}
```

## Conclusion
Hive is a powerful, fast, and easy-to-use NoSQL storage solution for Flutter. It provides a seamless way to store and retrieve data while maintaining excellent performance. The above guide covers basic integration and CRUD operations to help beginner Flutter developers get started with Hive.
