# Flutter BLoC Architecture Guide for Beginners

## Introduction to Flutter File Architecture

When building Flutter applications, having a **structured file architecture** is important for **maintainability, scalability, and readability**. Without a proper structure, the code can become unmanageable as the project grows.

### **Unstructured Project (Bad Practice)**
```
/lib
  ├── main.dart
  ├── home_screen.dart
  ├── counter_bloc.dart
  ├── counter_event.dart
  ├── counter_state.dart
  ├── some_api_calls.dart
  ├── another_screen.dart
```
- Files are scattered and difficult to manage.
- Business logic is mixed with UI code.
- Difficult to scale and maintain.

### **Structured Project (Good Practice)**
```
/lib
  ├── /bloc         # BLoC files (events, states, bloc classes)
  ├── /models       # Data models
  ├── /repositories # API or database interactions
  ├── /screens      # UI Screens
  ├── /widgets      # Reusable components
  ├── main.dart
```
- Organized structure for better maintainability.
- Separates business logic from UI.
- Easier to scale and collaborate.

## **What is BLoC?**

BLoC (**Business Logic Component**) is a state management solution in Flutter. It **separates business logic from UI**, making the app **more scalable, testable, and maintainable**.

### **Why BLoC?**
✅ **Separates UI & Logic** – Helps in clean code architecture.
✅ **Scalable** – Suitable for large applications.
✅ **Testable** – Easy to test business logic independently.
✅ **Reusability** – Use the same logic in multiple places.

## **Understanding the BLoC Architecture Layers**

### **Folder Structure Overview**

```
/lib
  ├── /bloc         # BLoC files (events, states, bloc classes)
  ├── /models       # Data models
  ├── /repositories # API or database interactions
  ├── /screens      # UI Screens
  ├── /widgets      # Reusable components
  ├── main.dart
```

### **Folder Explanations**
- **/bloc** → Handles business logic (events, states, bloc classes)
- **/models** → Defines data models used in the app
- **/repositories** → Manages API calls and data handling
- **/screens** → Contains UI screens
- **/widgets** → Stores reusable UI components

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
Happy coding! 🚀

