# 📌 Networking & APIs in Flutter

## 🚀 Introduction
Networking is an essential part of mobile apps, allowing them to **fetch data from the internet, communicate with servers, and display dynamic content**. In Flutter, the **http** package is commonly used for making API calls.

This guide will walk you through:
- **Making HTTP Requests** using the `http` package.
- **Fetching and displaying JSON data** in a Flutter app.
- **Handling errors** in API calls.

By the end, you'll understand how to make API calls in Flutter **step by step**.

---

## 🔹 1. Setting Up HTTP Package
### 📌 Step 1: Add `http` Package to Your Project
To use the `http` package, add it to your **pubspec.yaml** file:
```yaml
dependencies:
  flutter:
    sdk: flutter
  http: ^0.13.5  # Check for the latest version on pub.dev
```
Then, run:
```sh
flutter pub get
```
This installs the package and makes it ready to use.

---

## 🔹 2. Making an API Call (GET Request)
### 📌 Step 2: Import `http` Package
In your Dart file, import the package:
```dart
import 'package:flutter/material.dart';
import 'package:http/http.dart' as http;
import 'dart:convert';
```

### 📌 Step 3: Fetch Data from API
Now, let's create a function to fetch data from a sample API (`https://jsonplaceholder.typicode.com/users`):
```dart
Future<List<dynamic>> fetchUsers() async {
  final response = await http.get(Uri.parse('https://jsonplaceholder.typicode.com/users'));

  if (response.statusCode == 200) {
    return json.decode(response.body);
  } else {
    throw Exception('Failed to load users');
  }
}
```
**📌 Explanation:**
- `http.get()` makes a GET request to fetch data.
- `json.decode(response.body)` converts the response into a Dart list.
- If the request fails, it throws an error.

---

## 🔹 3. Displaying Data in UI
### 📌 Step 4: Create a Simple UI to Show API Data
Now, let's create a UI that fetches and displays the user list:
```dart
class UserListScreen extends StatefulWidget {
  @override
  _UserListScreenState createState() => _UserListScreenState();
}

class _UserListScreenState extends State<UserListScreen> {
  List<dynamic>? users;
  bool isLoading = true;
  String? errorMessage;

  @override
  void initState() {
    super.initState();
    fetchUsers().then((data) {
      setState(() {
        users = data;
        isLoading = false;
      });
    }).catchError((error) {
      setState(() {
        errorMessage = error.toString();
        isLoading = false;
      });
    });
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('User List')),
      body: isLoading
          ? Center(child: CircularProgressIndicator())
          : errorMessage != null
              ? Center(child: Text(errorMessage!))
              : ListView.builder(
                  itemCount: users?.length ?? 0,
                  itemBuilder: (context, index) {
                    return ListTile(
                      title: Text(users![index]['name']),
                      subtitle: Text(users![index]['email']),
                    );
                  },
                ),
    );
  }
}
```
**📌 Explanation:**
- `initState()` calls `fetchUsers()` and updates the state when data is received.
- `CircularProgressIndicator()` shows a loading state until data is fetched.
- If there's an error, it displays an error message.
- `ListView.builder()` displays the list of users dynamically.

---

## 🔹 4. Handling Errors in API Calls
### 📌 Step 5: Implement Error Handling
Always handle errors to prevent app crashes.
Here are some common error scenarios:

1️⃣ **No Internet Connection:**
```dart
catch (SocketException) {
  throw Exception('No Internet Connection');
}
```

2️⃣ **Server Errors:**
```dart
if (response.statusCode >= 500) {
  throw Exception('Server Error. Please try again later.');
}
```

3️⃣ **Invalid Response Format:**
```dart
try {
  json.decode(response.body);
} catch (e) {
  throw Exception('Invalid JSON format');
}
```
By handling these cases, the app provides a better user experience.

---

## 🔹 5. Full Example Code
```dart
import 'package:flutter/material.dart';
import 'package:http/http.dart' as http;
import 'dart:convert';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: UserListScreen(),
    );
  }
}

Future<List<dynamic>> fetchUsers() async {
  final response = await http.get(Uri.parse('https://jsonplaceholder.typicode.com/users'));

  if (response.statusCode == 200) {
    return json.decode(response.body);
  } else {
    throw Exception('Failed to load users');
  }
}

class UserListScreen extends StatefulWidget {
  @override
  _UserListScreenState createState() => _UserListScreenState();
}

class _UserListScreenState extends State<UserListScreen> {
  List<dynamic>? users;
  bool isLoading = true;
  String? errorMessage;

  @override
  void initState() {
    super.initState();
    fetchUsers().then((data) {
      setState(() {
        users = data;
        isLoading = false;
      });
    }).catchError((error) {
      setState(() {
        errorMessage = error.toString();
        isLoading = false;
      });
    });
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('User List')),
      body: isLoading
          ? Center(child: CircularProgressIndicator())
          : errorMessage != null
              ? Center(child: Text(errorMessage!))
              : ListView.builder(
                  itemCount: users?.length ?? 0,
                  itemBuilder: (context, index) {
                    return ListTile(
                      title: Text(users![index]['name']),
                      subtitle: Text(users![index]['email']),
                    );
                  },
                ),
    );
  }
}
```

---

## ✅ Summary
| Step | Task |
|------|------|
| 1️⃣ | Add `http` package to `pubspec.yaml` |
| 2️⃣ | Import `http` package in your Dart file |
| 3️⃣ | Make an API call using `http.get()` |
| 4️⃣ | Parse JSON response with `json.decode()` |
| 5️⃣ | Display data in `ListView.builder()` |
| 6️⃣ | Handle errors to prevent app crashes |

📚 **Happy Coding!** 🚀
