# Basic UI Widgets in Flutter

## 📌 Introduction
Flutter provides a rich set of widgets to create beautiful UIs. These widgets form the building blocks of any Flutter application. In this section, we will explore fundamental UI widgets such as **Text, Image, Icon, Container, Row, Column, ListView, GridView, Stack, ElevatedButton, TextField, Checkbox, and Switch**.

Each of these widgets plays a crucial role in UI design, and understanding them will help you build interactive and visually appealing applications.

---

## 📝 Text Widget
The `Text` widget is used to display simple text on the screen.

### 🔹 Example:
```dart
Text(
  'Hello, Flutter!',
  style: TextStyle(fontSize: 24, fontWeight: FontWeight.bold),
)
```
### 🖼️ Output:
![Text Widget](https://raw.githubusercontent.com/flutter/assets-for-api-docs/main/assets/widgets/text_widget.png)

---

## 🖼️ Image Widget
The `Image` widget allows you to display images from various sources like assets, network, or memory.

### 🔹 Example:
```dart
Image.network('https://flutter.dev/images/flutter-logo-sharing.png')
```
### 🖼️ Output:
![Image Widget](https://raw.githubusercontent.com/flutter/assets-for-api-docs/main/assets/widgets/image_widget.png)

---

## 🔘 Icon Widget
The `Icon` widget is used to display icons from Flutter’s built-in icon library.

### 🔹 Example:
```dart
Icon(Icons.favorite, color: Colors.red, size: 50)
```
### 🖼️ Output:
![Icon Widget](https://raw.githubusercontent.com/flutter/assets-for-api-docs/main/assets/widgets/icon_widget.png)

---

## 📦 Container Widget
The `Container` widget is used for styling and layout, allowing you to set padding, margins, colors, and decoration.

### 🔹 Example:
```dart
Container(
  width: 100,
  height: 100,
  color: Colors.blue,
)
```
### 🖼️ Output:
![Container Widget](https://raw.githubusercontent.com/flutter/assets-for-api-docs/main/assets/widgets/container_widget.png)

---

## 📏 Row & Column Widgets
The `Row` and `Column` widgets are used to arrange widgets **horizontally** and **vertically**, respectively.

### 🔹 Example:
```dart
Row(
  mainAxisAlignment: MainAxisAlignment.center,
  children: [
    Icon(Icons.star, color: Colors.yellow),
    Text('Flutter'),
  ],
)
```

---

## 📋 ListView Widget
The `ListView` widget is a scrollable list of widgets.

### 🔹 Example:
```dart
ListView(
  children: [
    ListTile(title: Text('Item 1')),
    ListTile(title: Text('Item 2')),
  ],
)
```

---

## 🔲 GridView Widget
The `GridView` widget arranges items in a grid pattern.

### 🔹 Example:
```dart
GridView.count(
  crossAxisCount: 2,
  children: [
    Container(color: Colors.red),
    Container(color: Colors.blue),
  ],
)
```

---

## 🏗️ Stack Widget
The `Stack` widget places widgets on top of each other.

### 🔹 Example:
```dart
Stack(
  children: [
    Container(width: 100, height: 100, color: Colors.green),
    Positioned(bottom: 10, right: 10, child: Icon(Icons.star, color: Colors.white)),
  ],
)
```

---

## 🔘 ElevatedButton Widget
The `ElevatedButton` is a material design button.

### 🔹 Example:
```dart
ElevatedButton(
  onPressed: () {},
  child: Text('Click Me'),
)
```

---

## ⌨️ TextField Widget
The `TextField` widget is used to accept text input from users.

### 🔹 Example:
```dart
TextField(
  decoration: InputDecoration(labelText: 'Enter your name'),
)
```

---

## ✅ Checkbox Widget
The `Checkbox` widget allows users to select an option.

### 🔹 Example:
```dart
Checkbox(value: true, onChanged: (newValue) {})
```

---

## 🔄 Switch Widget
The `Switch` widget is used to toggle between ON and OFF states.

### 🔹 Example:
```dart
Switch(value: true, onChanged: (newValue) {})
```

---

## ✅ Summary
- `Text`, `Image`, and `Icon` are used to display content.
- `Container` is a flexible layout container.
- `Row` and `Column` help in arranging widgets.
- `ListView` and `GridView` are used for lists and grids.
- `Stack` allows overlaying widgets.
- `ElevatedButton`, `TextField`, `Checkbox`, and `Switch` add interactivity.

---
📚 Happy coding! 🚀
