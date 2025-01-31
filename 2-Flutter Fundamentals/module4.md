# 📌 Navigation & Routes in Flutter

## 🚀 Introduction
Navigation in Flutter allows users to move between different screens (pages). Flutter provides multiple ways to navigate, including **push**, **pop**, and **named routes**.

Understanding navigation is crucial for building multi-screen apps. This guide will explain navigation in a beginner-friendly way with diagrams and examples.

---

## 🗺️ What is Navigation in Flutter?
Navigation in Flutter works like a **stack of pages**. When you move to a new screen, it is **pushed** onto the stack. When you go back, the screen is **popped** from the stack.

📌 **Stack Concept:**
```
Home Screen  →  Profile Screen  →  Settings Screen
  (Push)             (Push)            (Push)
```
Going back follows the **pop** operation:
```
Home Screen  ←  Profile Screen  ←  Settings Screen
  (Pop)            (Pop)            (Pop)
```

Flutter provides two main navigation methods:
1. **push() and pop()** (Basic navigation)
2. **Named Routes** (Organized navigation)

Let's explore them one by one! 🚀

---

## 🔹 1. Using `push()` and `pop()` (Basic Navigation)

This method manually moves between screens.

### ✨ Example: Navigate to a New Screen using push and pop
```dart
import 'package:flutter/material.dart';

void main() {
  runApp(MaterialApp(
    home: FirstScreen(),
  ));
}

class FirstScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('First Screen')),
      body: Center(
        child: ElevatedButton(
          onPressed: () {
            Navigator.push(
              context,
              MaterialPageRoute(builder: (context) => SecondScreen()),
            );
          },
          child: Text('Go to Second Screen'),
        ),
      ),
    );
  }
}

class SecondScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('Second Screen')),
      body: Center(
        child: ElevatedButton(
          onPressed: () {
            Navigator.pop(context);
          },
          child: Text('Go Back'),
        ),
      ),
    );
  }
}
```

### 📌 Explanation:
- `Navigator.push()` → Moves to `SecondScreen`.
- `Navigator.pop()` → Goes back to `FirstScreen`.

📍 **Other push/pop methods:**
- `Navigator.pushReplacement()` → Replaces the current screen with a new one.
- `Navigator.pushAndRemoveUntil()` → Removes all previous routes until a specific condition is met.

Example for `pushReplacement()`:
```dart
Navigator.pushReplacement(
  context,
  MaterialPageRoute(builder: (context) => NewScreen()),
);
```

Example for `pushAndRemoveUntil()`:
```dart
Navigator.pushAndRemoveUntil(
  context,
  MaterialPageRoute(builder: (context) => NewScreen()),
  (Route<dynamic> route) => false, // Removes all previous screens
);
```

---

## 🔹 2. Using Named Routes (Better Structure)
Named routes help manage multiple screens in large apps by defining routes globally.

### ✨ Example: Named Route Navigation
```dart
import 'package:flutter/material.dart';

void main() {
  runApp(MaterialApp(
    initialRoute: '/',
    routes: {
      '/': (context) => HomeScreen(),
      '/second': (context) => SecondScreen(),
    },
  ));
}

class HomeScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('Home Screen')),
      body: Center(
        child: ElevatedButton(
          onPressed: () {
            Navigator.pushNamed(context, '/second');
          },
          child: Text('Go to Second Screen'),
        ),
      ),
    );
  }
}

class SecondScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('Second Screen')),
      body: Center(
        child: ElevatedButton(
          onPressed: () {
            Navigator.pop(context);
          },
          child: Text('Go Back'),
        ),
      ),
    );
  }
}
```

### 📌 Explanation:
- `initialRoute: '/'` → Sets the first screen.
- `routes: { '/': (context) => HomeScreen(), '/second': (context) => SecondScreen() }` → Defines routes.
- `Navigator.pushNamed(context, '/second');` → Navigates using a route name.
- `Navigator.pop(context);` → Returns to the previous screen.

📍 **Other Named Route methods:**
- `Navigator.pushReplacementNamed(context, '/newScreen')` → Replaces the current screen with another.
- `Navigator.pushNamedAndRemoveUntil(context, '/newScreen', (route) => false)` → Removes all previous routes before navigating.

---

## ✅ Summary
| Navigation Type | Description |
|---------------|-------------|
| `push() / pop()` | Basic navigation between screens |
| `pushReplacement()` | Replaces the current screen with a new one |
| `pushAndRemoveUntil()` | Removes all previous routes until a condition is met |
| Named Routes | Organized navigation using route names |
| `pushReplacementNamed()` | Replaces a named route |
| `pushNamedAndRemoveUntil()` | Removes all previous named routes before navigating |

🔹 **For small apps**, `push` and `pop` are easy.
🔹 **For large apps**, **Named Routes** provide better structure.

---

📚 Happy coding! 😊
