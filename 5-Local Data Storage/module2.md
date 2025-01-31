# Shared Preferences in Flutter (Key-Value Storage)

## Introduction
Shared Preferences is a lightweight storage solution in Flutter that allows you to store key-value pairs persistently. It is useful for saving small amounts of data such as user preferences, login states, and simple settings.

---

## Installation

### 1. Add Dependency
To use Shared Preferences, add the following dependency in your `pubspec.yaml` file:

```yaml
dependencies:
  flutter:
    sdk: flutter
  shared_preferences: ^2.2.2  # Check the latest version on pub.dev
```

Run the following command to install the package:
```sh
flutter pub get
```

### 2. Import the Package
```dart
import 'package:shared_preferences/shared_preferences.dart';
```

---

## Saving Data
To store data, use the `set` methods such as `setString`, `setInt`, `setBool`, etc.

```dart
Future<void> saveData() async {
  final prefs = await SharedPreferences.getInstance();
  await prefs.setString('username', 'JohnDoe');
  await prefs.setInt('age', 25);
  await prefs.setBool('isLoggedIn', true);
}
```

---

## Retrieving Data
To retrieve stored data, use the `get` methods:

```dart
Future<void> getData() async {
  final prefs = await SharedPreferences.getInstance();
  String? username = prefs.getString('username');
  int? age = prefs.getInt('age');
  bool? isLoggedIn = prefs.getBool('isLoggedIn');

  print("Username: $username");
  print("Age: $age");
  print("Is Logged In: $isLoggedIn");
}
```

---

## Updating Data
Updating data is as simple as overwriting the existing key:

```dart
Future<void> updateData() async {
  final prefs = await SharedPreferences.getInstance();
  if (prefs.containsKey('username')) {
    await prefs.setString('username', 'UpdatedJohnDoe');
    print("Username updated successfully!");
  } else {
    print("No existing username found to update.");
  }
}
```

---

## Removing Data
To remove a specific key:
```dart
Future<void> removeData() async {
  final prefs = await SharedPreferences.getInstance();
  await prefs.remove('username');
}
```

To clear all stored data:
```dart
Future<void> clearAllData() async {
  final prefs = await SharedPreferences.getInstance();
  await prefs.clear();
}
```

---

## Full Code Example
This is a simple Flutter app demonstrating **Shared Preferences**:

```dart
import 'package:flutter/material.dart';
import 'package:shared_preferences/shared_preferences.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: SharedPreferencesDemo(),
    );
  }
}

class SharedPreferencesDemo extends StatefulWidget {
  @override
  _SharedPreferencesDemoState createState() => _SharedPreferencesDemoState();
}

class _SharedPreferencesDemoState extends State<SharedPreferencesDemo> {
  TextEditingController _controller = TextEditingController();
  String _storedData = "No data saved yet";

  @override
  void initState() {
    super.initState();
    _loadData();
  }

  Future<void> _saveData() async {
    final prefs = await SharedPreferences.getInstance();
    await prefs.setString('username', _controller.text);
    setState(() {
      _storedData = _controller.text;
    });
  }

  Future<void> _loadData() async {
    final prefs = await SharedPreferences.getInstance();
    String? username = prefs.getString('username');
    setState(() {
      _storedData = username ?? "No data saved yet";
    });
  }

  Future<void> _updateData() async {
    final prefs = await SharedPreferences.getInstance();
    if (prefs.containsKey('username')) {
      await prefs.setString('username', _controller.text);
      setState(() {
        _storedData = _controller.text;
      });
    } else {
      print("No data found to update.");
    }
  }

  Future<void> _clearData() async {
    final prefs = await SharedPreferences.getInstance();
    await prefs.remove('username');
    setState(() {
      _storedData = "No data saved yet";
    });
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text("Shared Preferences Example")),
      body: Padding(
        padding: const EdgeInsets.all(16.0),
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            TextField(
              controller: _controller,
              decoration: InputDecoration(
                border: OutlineInputBorder(),
                labelText: "Enter username",
              ),
            ),
            SizedBox(height: 10),
            ElevatedButton(
              onPressed: _saveData,
              child: Text("Save Data"),
            ),
            SizedBox(height: 10),
            ElevatedButton(
              onPressed: _updateData,
              child: Text("Update Data"),
            ),
            SizedBox(height: 10),
            ElevatedButton(
              onPressed: _clearData,
              child: Text("Clear Data"),
            ),
            SizedBox(height: 20),
            Text("Stored Data: $_storedData"),
          ],
        ),
      ),
    );
  }
}
```

---

## Summary
- Shared Preferences is used for simple key-value storage.
- Use `set` methods to store data (`setString`, `setInt`, etc.).
- Use `get` methods to retrieve data (`getString`, `getInt`, etc.).
- Use `remove` to delete a specific key.
- Use `clear` to delete all stored data.

This is a **beginner-friendly approach** to local storage in Flutter. 🚀

Would you like to explore **advanced topics** such as:
- **Using Shared Preferences for dark/light theme settings**?
- **Storing and retrieving lists using JSON format**?
- **Encrypting sensitive data in Shared Preferences**?

Let me know how I can improve this guide! 😊
