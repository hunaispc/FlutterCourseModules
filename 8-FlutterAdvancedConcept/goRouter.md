# GoRouter Study Material for Flutter Beginners

## **Introduction to GoRouter**

### **What is GoRouter?**
GoRouter is a declarative routing package for Flutter that simplifies navigation for mobile and web applications. It helps manage navigation using a structured route table and supports deep linking, named routes, and URL-based navigation.

### **Why use GoRouter instead of Navigator?**
Flutter's built-in `Navigator` uses an imperative approach (`push` and `pop`), which can become complex when managing deep links, web navigation, and URL synchronization. GoRouter offers a **declarative approach**, making navigation easier, especially for Flutter Web and large applications.

### **Benefits of Using GoRouter**
- **Declarative navigation:** Define routes in one place.
- **Deep linking support:** Handles web URLs and mobile deep links seamlessly.
- **Named routes:** Makes navigation more readable.
- **Supports query parameters and path parameters.**
- **Simplifies state management in navigation.**
- **Works well with bottom navigation and tab-based apps.**

---

## **1. Installing and Setting Up GoRouter**

### **Step 1: Add the GoRouter Dependency**
In your `pubspec.yaml` file, add:
```yaml
dependencies:
  flutter:
    sdk: flutter
  go_router: ^13.1.0  # Use the latest version
```
Then, run:
```sh
flutter pub get
```

---

## **2. Basic Navigation Using GoRouter**
GoRouter simplifies navigation using a **route table**.

### **Step 2: Create a Simple Router**
In `main.dart`, define the **router configuration**:
```dart
import 'package:flutter/material.dart';
import 'package:go_router/go_router.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  MyApp({super.key});

  final GoRouter _router = GoRouter(
    routes: [
      GoRoute(path: '/', builder: (context, state) => HomeScreen()),
      GoRoute(path: '/details', builder: (context, state) => DetailScreen()),
    ],
  );

  @override
  Widget build(BuildContext context) {
    return MaterialApp.router(
      routerConfig: _router,
      debugShowCheckedModeBanner: false,
    );
  }
}
```

### **Step 3: Navigate Between Screens**
```dart
// Navigate to Details Screen
onPressed: () => context.go('/details');
```

---

## **3. Passing Parameters in Navigation**

### **Step 4: Define Routes with Parameters**
```dart
GoRouter(
  routes: [
    GoRoute(path: '/details/:id', builder: (context, state) {
      final id = state.pathParameters['id'];
      return DetailScreen(id: id!);
    }),
  ],
);
```

### **Step 5: Navigate with Parameters**
```dart
onPressed: () => context.go('/details/42'); // Passing ID=42
```

### **Step 6: Retrieve Parameters in the Destination Screen**
```dart
class DetailScreen extends StatelessWidget {
  final String id;
  DetailScreen({required this.id});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text("Details - ID: $id")),
      body: Center(child: Text("Received ID: $id")),
    );
  }
}
```

---

## **4. Named Routes in GoRouter**
### **Step 7: Define Named Routes**
```dart
GoRouter(
  routes: [
    GoRoute(name: 'home', path: '/', builder: (context, state) => HomeScreen()),
    GoRoute(name: 'details', path: '/details/:id', builder: (context, state) {
      final id = state.pathParameters['id'];
      return DetailScreen(id: id!);
    }),
  ],
);
```

### **Step 8: Navigate Using Named Routes**
```dart
context.goNamed('details', pathParameters: {'id': '42'});
```

---

## **5. Handling Nested Navigation (Shell Route)**
For apps with bottom navigation, use `ShellRoute`:

### **Step 9: Implement Bottom Navigation Using ShellRoute**
```dart
GoRouter(
  routes: [
    ShellRoute(
      builder: (context, state, child) {
        return Scaffold(
          body: child,
          bottomNavigationBar: BottomNavigationBar(
            items: [
              BottomNavigationBarItem(icon: Icon(Icons.home), label: 'Home'),
              BottomNavigationBarItem(icon: Icon(Icons.settings), label: 'Settings'),
            ],
            onTap: (index) {
              if (index == 0) context.go('/home');
              if (index == 1) context.go('/settings');
            },
          ),
        );
      },
      routes: [
        GoRoute(path: '/home', builder: (context, state) => HomeScreen()),
        GoRoute(path: '/settings', builder: (context, state) => SettingsScreen()),
      ],
    ),
  ],
);
```

---

## **6. Full Code Example**
```dart
import 'package:flutter/material.dart';
import 'package:go_router/go_router.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  MyApp({super.key});

  final GoRouter _router = GoRouter(
    routes: [
      GoRoute(name: 'home', path: '/', builder: (context, state) => HomeScreen()),
      GoRoute(name: 'details', path: '/details/:id', builder: (context, state) {
        final id = state.pathParameters['id'];
        return DetailScreen(id: id!);
      }),
    ],
  );

  @override
  Widget build(BuildContext context) {
    return MaterialApp.router(
      routerConfig: _router,
      debugShowCheckedModeBanner: false,
    );
  }
}

class HomeScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text("Home")),
      body: Center(
        child: ElevatedButton(
          onPressed: () => context.goNamed('details', pathParameters: {'id': '42'}),
          child: Text("Go to Details with ID 42"),
        ),
      ),
    );
  }
}

class DetailScreen extends StatelessWidget {
  final String id;
  DetailScreen({required this.id});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text("Details - ID: $id")),
      body: Center(child: Text("Received ID: $id")),
    );
  }
}
```

---

## **7. Summary**
- **GoRouter** simplifies navigation.
- Supports **deep linking, named routes, and query parameters**.
- Works well for **mobile and web apps**.
- Ideal for **large-scale applications**.

This guide helps **Flutter beginners** understand GoRouter for navigation. 

