# Firebase Realtime Database Integration in Flutter

## Introduction
Firebase Realtime Database is a cloud-hosted NoSQL database that allows real-time synchronization of data across all clients. In this guide, we will cover how to integrate Firebase Realtime Database into a Flutter application, perform CRUD operations, and set database rules for full access.

## Prerequisites
Before starting, ensure you have the following:
- Flutter installed on your system.
- A Firebase account and project setup.
- A basic understanding of Flutter and Dart.

## Step 1: Setup Firebase in Flutter

### 1. Create a Firebase Project
1. Go to [Firebase Console](https://console.firebase.google.com/)

### 2. Add Firebase Dependencies
Open `pubspec.yaml` and add:
```yaml
  dependencies:
    flutter:
      sdk: flutter
    firebase_core: latest_version
    firebase_database: latest_version
```
Run:
```sh
flutter pub get
```

### 3. Initialize Firebase in Your Flutter App
Modify `main.dart`:
```dart
import 'package:flutter/material.dart';
import 'package:firebase_core/firebase_core.dart';

void main() async {
  WidgetsFlutterBinding.ensureInitialized();
  await Firebase.initializeApp();
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
```

## Step 2: Configure Firebase Realtime Database

1. In Firebase Console, go to `Build > Realtime Database`
2. Click `Create Database` and select a region.
3. Choose `Start in test mode` for full access (modify later for security).

### Database Rules for Full Access
Set the following rules to allow read/write access:
```json
{
  "rules": {
    ".read": true,
    ".write": true
  }
}
```

## Step 3: Perform CRUD Operations

### 1. Writing Data
```dart
import 'package:firebase_database/firebase_database.dart';

final databaseRef = FirebaseDatabase.instance.ref();

void addData() {
  databaseRef.child("users").push().set({
    'name': 'John Doe',
    'age': 25
  });
}
```

### 2. Reading Data
```dart
void getData() {
  databaseRef.child("users").onValue.listen((event) {
    print(event.snapshot.value);
  });
}
```

### 3. Updating Data
```dart
void updateData(String key) {
  databaseRef.child("users").child(key).update({
    'age': 26
  });
}
```

### 4. Deleting Data
```dart
void deleteData(String key) {
  databaseRef.child("users").child(key).remove();
}
```

## Full Flutter Code Example
```dart
import 'package:flutter/material.dart';
import 'package:firebase_core/firebase_core.dart';
import 'package:firebase_database/firebase_database.dart';

void main() async {
  WidgetsFlutterBinding.ensureInitialized();
  await Firebase.initializeApp();
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  final databaseRef = FirebaseDatabase.instance.ref();

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        appBar: AppBar(title: Text("Firebase Realtime Database")),
        body: Center(
          child: Column(
            mainAxisAlignment: MainAxisAlignment.center,
            children: [
              ElevatedButton(
                onPressed: () {
                  databaseRef.child("users").push().set({
                    'name': 'John Doe',
                    'age': 25
                  });
                },
                child: Text("Add Data"),
              ),
              ElevatedButton(
                onPressed: () {
                  databaseRef.child("users").onValue.listen((event) {
                    print(event.snapshot.value);
                  });
                },
                child: Text("Read Data"),
              ),
              ElevatedButton(
                onPressed: () {
                  databaseRef.child("users").child("docId").update({
                    'age': 30
                  });
                },
                child: Text("Update Data"),
              ),
              ElevatedButton(
                onPressed: () {
                  databaseRef.child("users").child("docId").remove();
                },
                child: Text("Delete Data"),
              ),
            ],
          ),
        ),
      ),
    );
  }
}
```
