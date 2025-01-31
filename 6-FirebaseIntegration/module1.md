# Firebase Integration in Flutter

## Overview
This guide provides steps to integrate Firebase with a Flutter project using the latest Firebase commands.

## Prerequisites
- Install Firebase CLI ([Guide](https://firebase.google.com/docs/cli))
- A Firebase project ([Create Here](https://console.firebase.google.com/))

## Steps to Connect Flutter Project with Firebase

### 1. Create a Flutter Project
```sh
flutter create firebase_app
cd firebase_app
```

### 2. Install Required CLI Tools
```sh
npm install -g firebase-tools
firebase login
```

### 3. Install FlutterFire CLI
```sh
dart pub global activate flutterfire_cli
```

### 4. Configure Firebase in Your Flutter Project
```sh
flutterfire configure
```
This command does the following:
- Connects your Flutter project to Firebase.
- Generates a `firebase_options.dart` file with Firebase configurations.
- Ensures Gradle dependencies are correctly set for Android.

### 5. Add Firebase Core Plugin
```sh
flutter pub add firebase_core
```

### 6. Initialize Firebase in Flutter
Edit `main.dart` file:
```dart
import 'package:flutter/material.dart';
import 'package:firebase_core/firebase_core.dart';
import 'firebase_options.dart';

void main() async {
  WidgetsFlutterBinding.ensureInitialized();
  await Firebase.initializeApp(
    options: DefaultFirebaseOptions.currentPlatform,
  );
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        appBar: AppBar(title: Text('Firebase Integration')),
        body: Center(child: Text('Firebase Initialized Successfully!')),
      ),
    );
  }
}
```

### 7. Add Firebase Plugins for Additional Features
To use specific Firebase services, install corresponding plugins:
```sh
flutter pub add cloud_firestore
flutter pub add firebase_auth
flutter pub add firebase_storage
flutter pub add firebase_messaging
```
After adding plugins, run:
```sh
flutterfire configure
```
This ensures Firebase settings are up-to-date.

### 8. Run the Project
```sh
flutter pub get
flutter run
```
