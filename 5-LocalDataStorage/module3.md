# SQLite in Flutter - A Comprehensive Guide for Beginners

## Introduction
SQLite is a lightweight, local database used for storing structured data in mobile applications. It allows Flutter developers to perform database operations such as Create, Read, Update, and Delete (CRUD). This module will guide you step by step through integrating SQLite into your Flutter application.

## Prerequisites
Before starting, ensure you have:
- Flutter installed on your system
- Basic knowledge of Dart
- An integrated development environment (IDE) such as Android Studio or VS Code

## Installation
To use SQLite in Flutter, add the required dependencies in your `pubspec.yaml` file:

```yaml
dependencies:
  flutter:
    sdk: flutter
  sqflite: ^2.2.0+3
  path_provider: ^2.0.14
```

Run the command to fetch the dependencies:
```sh
flutter pub get
```

## Database Setup
Create a database helper class (`database_helper.dart`) to manage SQLite operations.

```dart
import 'package:sqflite/sqflite.dart';
import 'package:path/path.dart';

class DatabaseHelper {
  static final DatabaseHelper instance = DatabaseHelper._init();
  static Database? _database;

  DatabaseHelper._init();

  Future<Database> get database async {
    if (_database != null) return _database!;
    _database = await _initDB('app_database.db');
    return _database!;
  }

  Future<Database> _initDB(String filePath) async {
    final dbPath = await getDatabasesPath();
    final path = join(dbPath, filePath);
    return await openDatabase(path, version: 1, onCreate: _createDB);
  }

  Future<void> _createDB(Database db, int version) async {
    await db.execute('''
      CREATE TABLE users (
        id INTEGER PRIMARY KEY AUTOINCREMENT,
        name TEXT NOT NULL,
        email TEXT NOT NULL
      )
    ''');
  }
}
```

## CRUD Operations

### Insert Data
```dart
Future<int> insertUser(Map<String, dynamic> user) async {
  final db = await DatabaseHelper.instance.database;
  return await db.insert('users', user);
}
```

### Retrieve Data
```dart
Future<List<Map<String, dynamic>>> fetchUsers() async {
  final db = await DatabaseHelper.instance.database;
  return await db.query('users');
}
```

### Update Data
```dart
Future<int> updateUser(Map<String, dynamic> user, int id) async {
  final db = await DatabaseHelper.instance.database;
  return await db.update('users', user, where: 'id = ?', whereArgs: [id]);
}
```

### Delete Data
```dart
Future<int> deleteUser(int id) async {
  final db = await DatabaseHelper.instance.database;
  return await db.delete('users', where: 'id = ?', whereArgs: [id]);
}
```

## Full Example

```dart
import 'package:flutter/material.dart';
import 'database_helper.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'SQLite Example',
      home: UserScreen(),
    );
  }
}

class UserScreen extends StatefulWidget {
  @override
  _UserScreenState createState() => _UserScreenState();
}

class _UserScreenState extends State<UserScreen> {
  List<Map<String, dynamic>> users = [];

  @override
  void initState() {
    super.initState();
    _refreshUsers();
  }

  Future<void> _refreshUsers() async {
    final data = await DatabaseHelper.instance.fetchUsers();
    setState(() {
      users = data;
    });
  }

  Future<void> _addUser() async {
    await DatabaseHelper.instance.insertUser({'name': 'New User', 'email': 'newuser@example.com'});
    _refreshUsers();
  }

  Future<void> _deleteUser(int id) async {
    await DatabaseHelper.instance.deleteUser(id);
    _refreshUsers();
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('SQLite CRUD Example')),
      body: ListView.builder(
        itemCount: users.length,
        itemBuilder: (context, index) {
          return ListTile(
            title: Text(users[index]['name']),
            subtitle: Text(users[index]['email']),
            trailing: IconButton(
              icon: Icon(Icons.delete),
              onPressed: () => _deleteUser(users[index]['id']),
            ),
          );
        },
      ),
      floatingActionButton: FloatingActionButton(
        child: Icon(Icons.add),
        onPressed: _addUser,
      ),
    );
  }
}
```

## Conclusion
This guide covered how to integrate SQLite in Flutter, perform CRUD operations, and implement a full example. By following these steps, you can efficiently manage local databases in your Flutter applications.
