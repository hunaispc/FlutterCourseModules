# Firebase Firestore Integration in Flutter

## Introduction
Firebase Firestore is a cloud-hosted NoSQL database that enables scalable and flexible data storage with real-time synchronization across all clients. In this guide, we will cover how to integrate Firebase Firestore into a Flutter application, perform CRUD operations, and set database rules for full access.

## Prerequisites
Before starting, ensure you have the following:
- Flutter installed on your system.
- A Firebase account and project setup.
- A basic understanding of Flutter and Dart.

## Step 1: Setup Firebase in Flutter

### 1. Create a Firebase Project
1. Go to [Firebase Console](https://console.firebase.google.com/)
2. Create a new project and add a Firebase app for your Flutter project.

### 2. Add Firebase Dependencies
Open `pubspec.yaml` and add:
```yaml
  dependencies:
    flutter:
      sdk: flutter
    firebase_core: latest_version
    cloud_firestore: latest_version
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

## Step 2: Configure Firebase Firestore

1. In Firebase Console, go to `Build > Firestore Database`
2. Click `Create Database` and select a region.
3. Choose `Start in test mode` for full access (modify later for security).

### Firestore Security Rules for Full Access
Set the following rules to allow read/write access:
```json
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /{document=**} {
      allow read, write: if true;
    }
  }
}
```

## Step 3: Perform CRUD Operations

### 1. Writing Data
```dart
import 'package:cloud_firestore/cloud_firestore.dart';

final firestore = FirebaseFirestore.instance;

void addData() {
  firestore.collection("users").add({
    'name': 'John Doe',
    'age': 25
  });
}
```

### 2. Reading Data
```dart
void getData() {
  firestore.collection("users").snapshots().listen((snapshot) {
    for (var doc in snapshot.docs) {
      print(doc.data());
    }
  });
}
```

### 3. Updating Data
```dart
void updateData(String docId) {
  firestore.collection("users").doc(docId).update({
    'age': 26
  });
}
```

### 4. Deleting Data
```dart
void deleteData(String docId) {
  firestore.collection("users").doc(docId).delete();
}
```

## Full Flutter Code Example
```dart
import 'package:flutter/material.dart';
import 'package:firebase_core/firebase_core.dart';
import 'package:cloud_firestore/cloud_firestore.dart';

void main() async {
  WidgetsFlutterBinding.ensureInitialized();
  await Firebase.initializeApp();
  runApp(MyApp());
}

final CollectionReference usersCollection = FirebaseFirestore.instance.collection('users');

void addData() {
  usersCollection.add({
    'name': 'John Doe',
    'age': 25
  });
}

void deleteData(String docId) {
  usersCollection.doc(docId).delete();
}

void updateData(String docId) {
  usersCollection.doc(docId).update({
    'age': 26
  });
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        appBar: AppBar(title: Text("Firebase Firestore Database")),
        body: Column(
          children: [
            Expanded(
              child: StreamBuilder(
                stream: usersCollection.snapshots(),
                builder: (context, AsyncSnapshot<QuerySnapshot> snapshot) {
                  if (!snapshot.hasData) {
                    return Center(child: Text("No Data Available"));
                  }
                  
                  List<QueryDocumentSnapshot> items = snapshot.data!.docs;
                  
                  return ListView.builder(
                    itemCount: items.length,
                    itemBuilder: (context, index) {
                      return ListTile(
                        title: Text(items[index]['name']),
                        subtitle: Text("Age: \${items[index]['age']}"),
                        trailing: Row(
                          mainAxisSize: MainAxisSize.min,
                          children: [
                            IconButton(
                              icon: Icon(Icons.edit),
                              onPressed: () => updateData(items[index].id),
                            ),
                            IconButton(
                              icon: Icon(Icons.delete),
                              onPressed: () => deleteData(items[index].id),
                            ),
                          ],
                        ),
                      );
                    },
                  );
                },
              ),
            ),
            Padding(
              padding: const EdgeInsets.all(16.0),
              child: ElevatedButton(
                onPressed: addData,
                child: Text("Add Data"),
              ),
            )
          ],
        ),
      ),
    );
  }
}

```

This guide provides a complete setup for integrating Firebase Firestore in Flutter, allowing you to perform CRUD operations efficiently.

