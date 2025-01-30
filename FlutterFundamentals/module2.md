# Stateless vs Stateful Widgets in Flutter

## 📌 Introduction
Flutter provides two main types of widgets: **Stateless** and **Stateful**. Understanding the difference between these widgets is essential for efficient Flutter development. This section will cover their characteristics, differences, and when to use each.

---

## 🎭 What are Stateless and Stateful Widgets?

### 🟢 Stateless Widgets
A **Stateless Widget** is a widget that does not change once it is built. It remains constant throughout its lifecycle and does not require any state management.

#### 🔹 Key Features:
- **Immutable**: Once built, they do not change.
- **Efficient**: Since they do not update, they require fewer resources.
- **Used for UI elements** that do not need to change dynamically (e.g., `Text`, `Icon`, `Container`).

#### 🔹 Example of a Stateless Widget

```dart
import 'package:flutter/material.dart';

class MyStatelessWidget extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('Stateless Widget Example')),
      body: Center(
        child: Text('I am a Stateless Widget!'),
      ),
    );
  }
}

void main() {
  runApp(MaterialApp(home: MyStatelessWidget()));
}
```

#### 🖼️ Stateless Widget Lifecycle
![Stateless Widget Lifecycle](https://www.google.com/url?sa=i&url=https%3A%2F%2Fvelog.io%2F%40qkr7627%2FFlutter-StatefulWidget%25EC%259D%2598LifeCycle&psig=AOvVaw0lZWsXvool3i-7_ywZEboK&ust=1738325130766000&source=images&cd=vfe&opi=89978449&ved=0CBQQjRxqFwoTCMjAuoC0nYsDFQAAAAAdAAAAABAE)

---

### 🔵 Stateful Widgets
A **Stateful Widget** can change dynamically during the app’s lifecycle. It maintains an internal state and updates the UI when necessary.

#### 🔹 Key Features:
- **Mutable**: It can update during runtime.
- **Requires `setState()`**: Changes to state trigger a rebuild of the widget.
- **Used for interactive components** like text fields, checkboxes, and animations.

#### 🔹 Example of a Stateful Widget

```dart
import 'package:flutter/material.dart';

class MyStatefulWidget extends StatefulWidget {
  @override
  _MyStatefulWidgetState createState() => _MyStatefulWidgetState();
}

class _MyStatefulWidgetState extends State<MyStatefulWidget> {
  int counter = 0;

  void incrementCounter() {
    setState(() {
      counter++;
    });
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('Stateful Widget Example')),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            Text('Counter: \$counter', style: TextStyle(fontSize: 24)),
            SizedBox(height: 20),
            ElevatedButton(
              onPressed: incrementCounter,
              child: Text('Increase Counter'),
            ),
          ],
        ),
      ),
    );
  }
}

void main() {
  runApp(MaterialApp(home: MyStatefulWidget()));
}
```

#### 🖼️ Stateful Widget Lifecycle
![Stateful Widget Lifecycle](https://raw.githubusercontent.com/flutter/assets-for-api-docs/main/assets/widgets/stateful_widget_lifecycle.png)

---

## 🔄 Key Differences Between Stateless and Stateful Widgets

| Feature             | Stateless Widget | Stateful Widget |
|---------------------|----------------|----------------|
| **Mutability**      | Immutable      | Mutable       |
| **State Handling**  | No state       | Has state    |
| **Performance**     | More efficient | Requires rebuilding |
| **Use Case**        | Static UI      | Interactive UI |
| **Rebuild Trigger** | No rebuild     | Uses `setState()` to update |

---

## 🛠️ When to Use Stateless vs Stateful Widgets

| Scenario | Widget Type |
|----------|------------|
| Displaying static text, images, or icons | Stateless Widget |
| Handling form inputs, animations, or user interactions | Stateful Widget |
| Displaying fixed buttons, headers, or cards | Stateless Widget |
| Updating UI based on user input (like a counter or toggle switch) | Stateful Widget |

---

## ✅ Summary
- **Stateless Widgets**: Immutable, lightweight, and efficient for static UI.
- **Stateful Widgets**: Maintain an internal state and can update dynamically.
- Choosing the right type of widget ensures better performance and maintainability in Flutter apps.

---

📚 Happy coding! 🚀
