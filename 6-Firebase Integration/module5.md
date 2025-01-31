# Firebase Cloud Messaging (FCM) - Push Notifications in Flutter

## Introduction
Firebase Cloud Messaging (FCM) is a cross-platform messaging solution that allows you to send notifications and messages to users. It works seamlessly with Flutter and can be integrated into both Android and iOS applications.

This guide provides a step-by-step tutorial on integrating FCM in a Flutter application, including sending push notifications, handling messages, and performing CRUD operations with FCM data.

---

## Prerequisites
Before starting, ensure you have:
- A Flutter project set up
- Firebase configured in your Flutter project
- A Firebase account

### 1. Setting up Firebase
#### Step 1: Create a Firebase Project
1. Go to [Firebase Console](https://console.firebase.google.com/).
2. Click **Add Project** and follow the setup instructions.
3. Register your app with Firebase (for both Android and iOS if required).

#### Step 2: Add Firebase to Your Flutter Project
1. Install the Firebase CLI tool:
   ```sh
   dart pub global activate flutterfire_cli
   ```
2. Connect Firebase to your Flutter project:
   ```sh
   flutterfire configure
   ```

This command links Firebase to your Flutter project and generates a `firebase_options.dart` file.

#### Step 3: Add Firebase Dependencies
Update `pubspec.yaml` with the required dependencies:
```yaml
dependencies:
  flutter:
    sdk: flutter
  firebase_core: latest_version
  firebase_messaging: latest_version
  cloud_firestore: latest_version
```
Run:
```sh
flutter pub get
```

#### Step 4: Configure Android & iOS
Follow the Firebase official setup guide to add the required configurations:
- **Android:** Modify `AndroidManifest.xml` and `build.gradle` files.
- **iOS:** Enable push notifications and background modes.

#### Step 5: Initialize Firebase in `main.dart`
Modify your `main.dart` file:
```dart
import 'package:firebase_core/firebase_core.dart';
import 'package:firebase_messaging/firebase_messaging.dart';
import 'package:flutter/material.dart';
import 'firebase_options.dart';

Future<void> backgroundHandler(RemoteMessage message) async {
  print("Message received: ${message.notification?.title}");
}

void main() async {
  WidgetsFlutterBinding.ensureInitialized();
  await Firebase.initializeApp(options: DefaultFirebaseOptions.currentPlatform);
  FirebaseMessaging.onBackgroundMessage(backgroundHandler);
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: HomePage(),
    );
  }
}
```

---

## 2. Handling Push Notifications

### Requesting Notification Permissions
Before receiving notifications, request permission from the user:
```dart
void requestPermission() async {
  FirebaseMessaging messaging = FirebaseMessaging.instance;
  NotificationSettings settings = await messaging.requestPermission(
    alert: true,
    announcement: false,
    badge: true,
    carPlay: false,
    criticalAlert: false,
    provisional: false,
    sound: true,
  );
  print("Permission status: ${settings.authorizationStatus}");
}
```

### Receiving Notifications
Listen for foreground messages:
```dart
FirebaseMessaging.onMessage.listen((RemoteMessage message) {
  print("Message received: ${message.notification?.title}");
});
```

Retrieve the device token for sending notifications:
```dart
void getToken() async {
  String? token = await FirebaseMessaging.instance.getToken();
  print("FCM Token: $token");
}
```

---

## 3. CRUD Operations with Firestore
We will store notification data in Firestore for future reference.

### Create Notification Entry
```dart
void sendNotification(String title, String body) {
  FirebaseFirestore.instance.collection("notifications").add({
    'title': title,
    'body': body,
    'timestamp': FieldValue.serverTimestamp(),
  });
}
```

### Read Notifications
```dart
Stream<QuerySnapshot> getNotifications() {
  return FirebaseFirestore.instance.collection("notifications").snapshots();
}
```

### Update Notification
```dart
void updateNotification(String docId, String newTitle) {
  FirebaseFirestore.instance.collection("notifications").doc(docId).update({
    'title': newTitle,
  });
}
```

### Delete Notification
```dart
void deleteNotification(String docId) {
  FirebaseFirestore.instance.collection("notifications").doc(docId).delete();
}
```

---

## 4. Full Code Example
Here’s a complete Flutter app integrating Firebase Cloud Messaging:

```dart
import 'package:firebase_core/firebase_core.dart';
import 'package:firebase_messaging/firebase_messaging.dart';
import 'package:flutter/material.dart';
import 'package:cloud_firestore/cloud_firestore.dart';
import 'firebase_options.dart';

void main() async {
  WidgetsFlutterBinding.ensureInitialized();
  await Firebase.initializeApp(options: DefaultFirebaseOptions.currentPlatform);
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: HomePage(),
    );
  }
}

class HomePage extends StatefulWidget {
  @override
  _HomePageState createState() => _HomePageState();
}

class _HomePageState extends State<HomePage> {
  FirebaseMessaging messaging = FirebaseMessaging.instance;

  @override
  void initState() {
    super.initState();
    messaging.requestPermission();
    FirebaseMessaging.onMessage.listen((RemoteMessage message) {
      print("Foreground message: ${message.notification?.title}");
    });
  }

  void sendNotification(String title, String body) {
    FirebaseFirestore.instance.collection("notifications").add({
      'title': title,
      'body': body,
      'timestamp': FieldValue.serverTimestamp(),
    });
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text("FCM Demo")),
      body: Center(
        child: ElevatedButton(
          onPressed: () => sendNotification("Hello", "This is a test notification"),
          child: Text("Send Notification"),
        ),
      ),
    );
  }
}
```

---

## Conclusion
This guide covered:
- Setting up Firebase Cloud Messaging
- Requesting user permissions
- Handling push notifications
- Performing CRUD operations

By following this step-by-step approach, you can implement FCM in your Flutter application and manage notifications efficiently. Happy coding!
