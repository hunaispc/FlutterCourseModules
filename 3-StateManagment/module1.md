# 📌 State Management in Flutter

## 🚀 Introduction
State management is one of the most important concepts in Flutter. It helps in maintaining and updating the **state** (data) of an app efficiently.

In simple terms, **state** is any piece of data that changes over time in your app. For example:
- A counter value increasing when a button is pressed.
- A user’s login status (logged in or logged out).
- A shopping cart that updates when a product is added.

This guide will cover different **state management techniques** in Flutter, making it easy for beginners to understand.

---

## 🎯 What is State?
State in Flutter can be categorized into two types:

1️⃣ **Ephemeral State (Local State)**
   - State that belongs to a single widget.
   - Example: TextField input, toggling a switch, animations.
   - Managed using `setState()`.

2️⃣ **App State (Global State)**
   - State that needs to be shared across multiple widgets/screens.
   - Example: User authentication, cart items, theme settings.
   - Requires state management solutions like **Provider**, **Riverpod**, **GetX**, or **Bloc**.

---

## 🔹 1. Using `setState()` (Basic State Management)
### 📌 When to Use It:
- When state is **local to a single widget**.
- When there are **no complex dependencies**.

### ✅ Example: Counter App Using `setState()`
```dart
import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: CounterScreen(),
    );
  }
}

class CounterScreen extends StatefulWidget {
  @override
  _CounterScreenState createState() => _CounterScreenState();
}

class _CounterScreenState extends State<CounterScreen> {
  int _counter = 0;

  void _incrementCounter() {
    setState(() {
      _counter++;
    });
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('Counter App')),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            Text('Counter: $_counter', style: TextStyle(fontSize: 24)),
            ElevatedButton(
              onPressed: _incrementCounter,
              child: Text('Increase Counter'),
            ),
          ],
        ),
      ),
    );
  }
}
```
**📌 Explanation:**
- `setState()` updates `_counter` when the button is pressed.
- Works well for small, simple apps.

---

## 🔹 2. Using `Provider` (Recommended for Large Apps)
### 📌 When to Use It:
- When you need to **share state across multiple widgets**.
- When you want a **cleaner and more scalable** approach.

### ✅ Example: Counter App Using `Provider`
```dart
import 'package:flutter/material.dart';
import 'package:provider/provider.dart';

void main() {
  runApp(
    ChangeNotifierProvider(
      create: (context) => CounterProvider(),
      child: MyApp(),
    ),
  );
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: CounterScreen(),
    );
  }
}

class CounterProvider extends ChangeNotifier {
  int _counter = 0;

  int get counter => _counter;

  void increment() {
    _counter++;
    notifyListeners();
  }
}

class CounterScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    final counterProvider = Provider.of<CounterProvider>(context);

    return Scaffold(
      appBar: AppBar(title: Text('Counter with Provider')),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            Text('Counter: ${counterProvider.counter}', style: TextStyle(fontSize: 24)),
            ElevatedButton(
              onPressed: counterProvider.increment,
              child: Text('Increase Counter'),
            ),
          ],
        ),
      ),
    );
  }
}
```
**📌 Explanation:**
- `ChangeNotifierProvider` provides `CounterProvider` to the entire app.
- `notifyListeners()` updates UI whenever `_counter` changes.
- Cleaner and more scalable than `setState()`.

---

## 🔹 3. Using `Bloc` (For Complex State Management)
### 📌 When to Use It:
- When managing **complex state logic**.
- When needing **structured event-based state management**.

## **Implementing BLoC Step-by-Step**

### **Step 1: Install Dependencies**

Run the following command to install `flutter_bloc`:
```bash
flutter pub add flutter_bloc
```

### **Step 2: Create a Simple Counter Example**

#### **Event (Define actions)**
```dart
abstract class CounterEvent {}

class Increment extends CounterEvent {}

class Decrement extends CounterEvent {}
```

#### **State (Define different states)**
```dart
class CounterState {
  final int count;
  CounterState(this.count);
}
```

#### **Bloc Class (Handle logic)**
```dart
import 'package:flutter_bloc/flutter_bloc.dart';

class CounterBloc extends Bloc<CounterEvent, CounterState> {
  CounterBloc() : super(CounterState(0)) {
    on<Increment>((event, emit) => emit(CounterState(state.count + 1)));
    on<Decrement>((event, emit) => emit(CounterState(state.count - 1)));
  }
}
```

#### **UI Implementation (Use BlocProvider and BlocBuilder)**
```dart
import 'package:flutter/material.dart';
import 'package:flutter_bloc/flutter_bloc.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: BlocProvider(
        create: (context) => CounterBloc(),
        child: CounterScreen(),
      ),
    );
  }
}

class CounterScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('Counter BLoC Example')),
      body: BlocBuilder<CounterBloc, CounterState>(
        builder: (context, state) {
          return Center(
            child: Column(
              mainAxisAlignment: MainAxisAlignment.center,
              children: [
                Text('Count: ${state.count}', style: TextStyle(fontSize: 24)),
                Row(
                  mainAxisAlignment: MainAxisAlignment.center,
                  children: [
                    IconButton(
                      icon: Icon(Icons.add),
                      onPressed: () => context.read<CounterBloc>().add(Increment()),
                    ),
                    IconButton(
                      icon: Icon(Icons.remove),
                      onPressed: () => context.read<CounterBloc>().add(Decrement()),
                    ),
                  ],
                ),
              ],
            ),
          );
        },
      ),
    );
  }
}

```
## ✅ Summary
| Method | Use Case |
|--------|---------|
| `setState()` | Best for local UI state in small apps |
| `Provider` | Best for global state in scalable apps |
| `Bloc` | Best for complex apps with structured state handling |

---

📚 **Happy Coding!** 
