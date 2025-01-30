# Basic UI Widgets in Flutter

## 📌 Introduction
Flutter provides a rich set of widgets to create beautiful UIs. These widgets form the building blocks of any Flutter application. In this section, we will explore fundamental UI widgets such as **Text, Image, Icon, Container, Row, Column, ListView, GridView, Stack, ElevatedButton, OutlinedButton, TextButton, TextField, Checkbox, Switch, Slider, Radio, DropdownButton, Card, AppBar, Scaffold, BottomNavigationBar, Drawer, FloatingActionButton, AlertDialog, Snackbar, ProgressIndicator, Chip, Divider, ExpansionTile, Tooltip, SizedBox, Padding, Align, Center, Visibility, Wrap, GestureDetector, and ClipRRect**.

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
Column(
  children: [
    Text('First Item'),
    Text('Second Item'),
  ],
)
```

```dart
Row(
  children: [
    Icon(Icons.star, color: Colors.yellow),
    Text('Flutter'),
  ],
)
```

---

## 🔘 ElevatedButton, OutlinedButton, and TextButton
These buttons allow users to interact with the app.

```dart
ElevatedButton(
  onPressed: () {},
  child: Text('Click Me'),
)
```

```dart
OutlinedButton(
  onPressed: () {},
  child: Text('Outlined Button'),
)
```

```dart
TextButton(
  onPressed: () {},
  child: Text('Text Button'),
)
```

---

## 🏗️ Stack Widget
The `Stack` widget overlays widgets on top of each other.

```dart
Stack(
  children: [
    Container(width: 100, height: 100, color: Colors.blue),
    Positioned(bottom: 10, right: 10, child: Icon(Icons.star, color: Colors.white)),
  ],
)
```

---

## 📌 AlertDialog & Snackbar
The `AlertDialog` and `Snackbar` widgets show messages to users.

```dart
showDialog(
  context: context,
  builder: (context) => AlertDialog(
    title: Text('Alert'),
    content: Text('This is an alert dialog'),
    actions: [TextButton(onPressed: () {}, child: Text('OK'))],
  ),
);
```

```dart
ScaffoldMessenger.of(context).showSnackBar(
  SnackBar(content: Text('This is a Snackbar')),
);
```

---

## 🔄 ProgressIndicator
The `CircularProgressIndicator` and `LinearProgressIndicator` show loading states.

```dart
CircularProgressIndicator()
```

```dart
LinearProgressIndicator()
```

---

## 🎭 Visibility & Wrap Widget
These widgets control widget appearance and layout wrapping.

```dart
Visibility(
  visible: true,
  child: Text('Visible Text'),
)
```

```dart
Wrap(
  children: [
    Chip(label: Text('Chip 1')),
    Chip(label: Text('Chip 2')),
  ],
)
```

---

## ✅ Summary
- This section includes additional widgets like `AlertDialog`, `Snackbar`, `ProgressIndicator`, `Chip`, `Divider`, `ExpansionTile`, `Tooltip`, `SizedBox`, `Padding`, `Align`, `Center`, `Wrap`, `GestureDetector`, and `ClipRRect`.
- These widgets help in enhancing UI interactivity, styling, and responsiveness.

---
📚 Happy coding! 🚀
