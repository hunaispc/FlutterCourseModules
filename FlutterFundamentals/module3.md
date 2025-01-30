# Basic UI Widgets in Flutter

## 📌 Introduction
Flutter provides a rich set of widgets to create beautiful UIs. These widgets form the building blocks of any Flutter application. In this section, we will explore fundamental UI widgets such as **Text, Image, Icon, Container, Row, Column, ListView, GridView, Stack, ElevatedButton, TextField, Checkbox, Switch, Slider, Radio, DropdownButton, Card, AppBar, Scaffold, BottomNavigationBar, Drawer, and FloatingActionButton**.

Each of these widgets plays a crucial role in UI design, and understanding them will help you build interactive and visually appealing applications.

---

## 📝 Text Widget
The `Text` widget is used to display simple text on the screen.

```dart
Text(
  'Hello, Flutter!',
  style: TextStyle(fontSize: 24, fontWeight: FontWeight.bold),
  textAlign: TextAlign.center,
)
```

---

## 🖼️ Image Widget
The `Image` widget allows displaying images from assets or network.

```dart
Image.network(
  'https://flutter.dev/images/flutter-logo-sharing.png',
  width: 100,
  height: 100,
)
```

---

## 🔘 Icon Widget
The `Icon` widget is used to display icons.

```dart
Icon(
  Icons.favorite,
  color: Colors.red,
  size: 50,
)
```

---

## 📦 Container Widget
The `Container` widget is used for styling and layout.

```dart
Container(
  width: 100,
  height: 100,
  color: Colors.blue,
  padding: EdgeInsets.all(10),
)
```

---

## 📏 Row & Column Widgets
These widgets arrange elements horizontally and vertically.

```dart
Row(
  children: [
    Icon(Icons.star, color: Colors.yellow),
    Text('Flutter'),
  ],
)
```

---

## 🎚️ Slider Widget
The `Slider` widget allows users to select a value from a range.

```dart
Slider(
  value: 50,
  min: 0,
  max: 100,
  onChanged: (value) {},
)
```

---

## 🔘 Radio Button Widget
The `Radio` widget allows users to select a single option.

```dart
Radio(
  value: 1,
  groupValue: 1,
  onChanged: (value) {},
)
```

---

## 🔽 DropdownButton Widget
The `DropdownButton` widget provides a dropdown list of selectable items.

```dart
DropdownButton(
  value: 'Option 1',
  items: [
    DropdownMenuItem(value: 'Option 1', child: Text('Option 1')),
    DropdownMenuItem(value: 'Option 2', child: Text('Option 2')),
  ],
  onChanged: (value) {},
)
```

---

## 🃏 Card Widget
The `Card` widget is used for displaying content in a structured format.

```dart
Card(
  child: Padding(
    padding: EdgeInsets.all(10),
    child: Text('This is a card'),
  ),
)
```

---

## 🏠 Scaffold & AppBar Widgets
The `Scaffold` provides a layout structure with an `AppBar`.

```dart
Scaffold(
  appBar: AppBar(title: Text('Flutter App')),
  body: Center(child: Text('Hello, World!')),
)
```

---

## 📌 BottomNavigationBar Widget
The `BottomNavigationBar` allows switching between different pages.

```dart
BottomNavigationBar(
  items: [
    BottomNavigationBarItem(icon: Icon(Icons.home), label: 'Home'),
    BottomNavigationBarItem(icon: Icon(Icons.settings), label: 'Settings'),
  ],
  currentIndex: 0,
  onTap: (index) {},
)
```

---

## 📂 Drawer Widget
The `Drawer` widget provides a sidebar navigation menu.

```dart
Drawer(
  child: ListView(
    children: [
      ListTile(title: Text('Home')),
      ListTile(title: Text('Settings')),
    ],
  ),
)
```

---

## 🚀 FloatingActionButton Widget
The `FloatingActionButton` widget provides a floating button for quick actions.

```dart
FloatingActionButton(
  onPressed: () {},
  child: Icon(Icons.add),
)
```

---

## ✅ Summary
- This section includes essential widgets like `Text`, `Image`, `Icon`, `Container`, `ListView`, `GridView`, `Scaffold`, `AppBar`, `BottomNavigationBar`, `Drawer`, and `FloatingActionButton`.
- Understanding these widgets helps in building complete Flutter applications.

---

📚 Happy coding! 🚀
