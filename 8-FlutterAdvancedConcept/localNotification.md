# Flutter Local Notifications - Beginner's Guide

## Introduction
Flutter Local Notifications is a package that allows displaying notifications within a Flutter application without needing an internet connection. This guide is designed for beginners and includes step-by-step instructions to integrate and use `flutter_local_notifications` with example code.

---

## Features of `flutter_local_notifications`
- Show simple local notifications
- Schedule notifications for a later time
- Customize notification sounds, icons, and actions
- Works on both Android and iOS

---

## Step 1: Add Dependencies
To use `flutter_local_notifications`, first, add the package to your `pubspec.yaml` file:

```yaml
dependencies:
  flutter:
    sdk: flutter
  flutter_local_notifications: ^16.1.0 # Use the latest version available
```

Run the following command to install the package:

```sh
flutter pub get
```

---

## Step 2: Configure Android and iOS

### Android Setup
Modify `AndroidManifest.xml` by adding the necessary permissions inside `<manifest>`:

```xml
<uses-permission android:name="android.permission.RECEIVE_BOOT_COMPLETED"/>
<uses-permission android:name="android.permission.FOREGROUND_SERVICE"/>
```

Inside the `<application>` tag, add:

```xml
<service
    android:name="com.dexterous.flutterlocalnotifications.ForegroundService"
    android:permission="android.permission.BIND_JOB_SERVICE"
    android:exported="false"/>
```

### iOS Setup
For iOS, add this inside `ios/Runner/Info.plist`:

```xml
<key>UIBackgroundModes</key>
<array>
    <string>fetch</string>
    <string>remote-notification</string>
</array>
```

Then, in `ios/Runner/AppDelegate.swift`, import the package:

```swift
import flutter_local_notifications
```

---

## Step 3: Initialize Notifications in `main.dart`

Create an instance of `FlutterLocalNotificationsPlugin` and initialize it:

```dart
import 'package:flutter/material.dart';
import 'package:flutter_local_notifications/flutter_local_notifications.dart';

final FlutterLocalNotificationsPlugin flutterLocalNotificationsPlugin =
    FlutterLocalNotificationsPlugin();

void main() async {
  WidgetsFlutterBinding.ensureInitialized();

  // Define Android initialization settings
  const AndroidInitializationSettings androidInitializationSettings =
      AndroidInitializationSettings('@mipmap/ic_launcher');

  // Create initialization settings object
  final InitializationSettings initializationSettings =
      InitializationSettings(android: androidInitializationSettings);

  // Initialize the plugin
  await flutterLocalNotificationsPlugin.initialize(initializationSettings);

  runApp(MyApp());
}
```

### Explanation:
- `flutterLocalNotificationsPlugin`: An instance of the plugin to control notifications.
- `AndroidInitializationSettings('@mipmap/ic_launcher')`: Specifies the default notification icon.
- `InitializationSettings(android: androidInitializationSettings)`: Combines platform-specific settings.
- `flutterLocalNotificationsPlugin.initialize()`: Initializes the plugin with defined settings.

---

## Step 4: Request Permissions (For iOS)

For iOS, request permission to show notifications:

```dart
Future<void> requestPermissions() async {
  flutterLocalNotificationsPlugin
      .resolvePlatformSpecificImplementation<IOSFlutterLocalNotificationsPlugin>()
      ?.requestPermissions(
        alert: true,
        badge: true,
        sound: true,
      );
}
```

Call `requestPermissions();` inside `main()`. This ensures that iOS users grant permission to display notifications.

---

## Step 5: Show a Simple Notification

Create a function to display a notification:

```dart
Future<void> showNotification() async {
  // Define notification details
  const AndroidNotificationDetails androidDetails = AndroidNotificationDetails(
      'channel_id', 'channel_name',
      importance: Importance.high, priority: Priority.high);

  // Combine platform-specific details
  const NotificationDetails notificationDetails =
      NotificationDetails(android: androidDetails);

  // Show the notification
  await flutterLocalNotificationsPlugin.show(
      0, 'Test Notification', 'This is a simple notification', notificationDetails);
}
```

### Explanation:
- `AndroidNotificationDetails('channel_id', 'channel_name')`: Defines the notification channel.
  - `'channel_id'`: A unique identifier for the notification channel.
  - `'channel_name'`: A user-readable name for the channel.
- `importance: Importance.high`: Ensures the notification appears prominently.
- `priority: Priority.high`: Ensures immediate delivery.
- `NotificationDetails()`: Combines all platform-specific settings.
- `flutterLocalNotificationsPlugin.show()`: Displays the notification.

---

## Step 6: Schedule a Notification

To show a notification after a delay:

```dart
Future<void> scheduleNotification() async {
  await flutterLocalNotificationsPlugin.zonedSchedule(
    1,
    'Scheduled Notification',
    'This will appear after 5 seconds',
    DateTime.now().add(Duration(seconds: 5)),
    const NotificationDetails(
      android: AndroidNotificationDetails('channel_id', 'channel_name'),
    ),
    androidAllowWhileIdle: true,
    uiLocalNotificationDateInterpretation:
        UILocalNotificationDateInterpretation.absoluteTime,
  );
}
```

### Explanation:
- `zonedSchedule()`: Schedules a notification.
- `DateTime.now().add(Duration(seconds: 5))`: Triggers the notification in 5 seconds.
- `androidAllowWhileIdle: true`: Ensures it works even in low-power mode.
- `uiLocalNotificationDateInterpretation.absoluteTime`: Ensures an exact trigger time.

---

## Step 7: Full Example Code

```dart
import 'package:flutter/material.dart';
import 'package:flutter_local_notifications/flutter_local_notifications.dart';

final FlutterLocalNotificationsPlugin flutterLocalNotificationsPlugin =
    FlutterLocalNotificationsPlugin();

void main() async {
  WidgetsFlutterBinding.ensureInitialized();

  const AndroidInitializationSettings androidInitializationSettings =
      AndroidInitializationSettings('@mipmap/ic_launcher');

  final InitializationSettings initializationSettings =
      InitializationSettings(android: androidInitializationSettings);

  await flutterLocalNotificationsPlugin.initialize(initializationSettings);

  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: NotificationScreen(),
    );
  }
}

class NotificationScreen extends StatelessWidget {
  Future<void> showNotification() async {
    const AndroidNotificationDetails androidDetails = AndroidNotificationDetails(
        'channel_id', 'channel_name',
        importance: Importance.high, priority: Priority.high);

    const NotificationDetails notificationDetails =
        NotificationDetails(android: androidDetails);

    await flutterLocalNotificationsPlugin.show(
        0, 'Test Notification', 'This is a simple notification', notificationDetails);
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text("Local Notifications")),
      body: Center(
        child: ElevatedButton(
          onPressed: showNotification,
          child: Text("Show Notification"),
        ),
      ),
    );
  }
}
```

---

## Conclusion
This guide covers everything needed to implement `flutter_local_notifications`, from setup to scheduling notifications. You can now customize notifications with sounds, actions, and styles to enhance your Flutter app!

