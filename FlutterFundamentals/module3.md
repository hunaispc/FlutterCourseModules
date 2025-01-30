# Basic UI Widgets in Flutter

## 📌 Introduction
Flutter provides a rich set of widgets to create beautiful UIs. These widgets form the building blocks of any Flutter application. In this section, we will explore fundamental UI widgets such as **Text, Image, Icon, Container, Row, Column, ListView, GridView, Stack, ElevatedButton, OutlinedButton, TextButton, TextField, Checkbox, Switch, Slider, Radio, DropdownButton, Card, AppBar, Scaffold, BottomNavigationBar, Drawer, FloatingActionButton, AlertDialog, Snackbar, ProgressIndicator, Chip, Divider, ExpansionTile, Tooltip, SizedBox, Padding, Align, Center, Visibility, Wrap, GestureDetector, ClipRRect, Stepper, TabBar, DatePicker, TimePicker**.

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

## 📋 ListView & GridView Widgets
### ListView Types

```dart
ListView(
  children: [
    ListTile(title: Text('Item 1')),
    ListTile(title: Text('Item 2')),
    ListTile(title: Text('Item 3')),
  ],
)
```

```dart
ListView.builder(
  itemCount: 10,
  itemBuilder: (context, index) {
    return ListTile(title: Text('Item \$index'));
  },
)
```

### GridView Types

```dart
GridView.count(
  crossAxisCount: 2,
  children: [
    Container(color: Colors.red),
    Container(color: Colors.blue),
    Container(color: Colors.green),
    Container(color: Colors.yellow),
  ],
)
```

```dart
GridView.builder(
  gridDelegate: SliverGridDelegateWithFixedCrossAxisCount(
    crossAxisCount: 2,
    crossAxisSpacing: 10,
    mainAxisSpacing: 10,
  ),
  itemCount: 6,
  itemBuilder: (context, index) {
    return Container(color: Colors.blue);
  },
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

## 📅 DatePicker & TimePicker
These widgets allow users to select a date or time.

```dart
showDatePicker(
  context: context,
  initialDate: DateTime.now(),
  firstDate: DateTime(2000),
  lastDate: DateTime(2101),
);
```

```dart
showTimePicker(
  context: context,
  initialTime: TimeOfDay.now(),
);
```

---

## 🏗️ Stepper Widget
The `Stepper` widget allows users to navigate through a sequence of steps.

```dart
Stepper(
  steps: [
    Step(title: Text('Step 1'), content: Text('This is the first step')),
    Step(title: Text('Step 2'), content: Text('This is the second step')),
  ],
)
```

---
## 📝 TextField Widget
The `TextField` widget allows users to enter text.

```dart
TextField(
  decoration: InputDecoration(
    labelText: 'Enter your name',
    border: OutlineInputBorder(),
  ),
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

## 📏 SizedBox Widget
The `SizedBox` widget is used to create a box with a specific height and width.

```dart
SizedBox(
  width: 100,
  height: 50,
  child: ElevatedButton(
    onPressed: () {},
    child: Text('Click Me'),
  ),
)
```

---

## 🔘 Different Button Widgets
### ElevatedButton
A material design button that elevates when pressed.

```dart
ElevatedButton(
  onPressed: () {},
  child: Text('Elevated Button'),
)
```

### OutlinedButton
A button with an outlined border.

```dart
OutlinedButton(
  onPressed: () {},
  child: Text('Outlined Button'),
)
```

### TextButton
A button with no elevation or border, used for text-based actions.

```dart
TextButton(
  onPressed: () {},
  child: Text('Text Button'),
)
```

### FloatingActionButton
A circular button used for primary actions.

```dart
FloatingActionButton(
  onPressed: () {},
  child: Icon(Icons.add),
)
```

---

## 📢 Dialog Box (AlertDialog)
The `AlertDialog` widget is used to display pop-up messages.

```dart
showDialog(
  context: context,
  builder: (context) => AlertDialog(
    title: Text('Alert'),
    content: Text('This is an alert dialog'),
    actions: [
      TextButton(
        onPressed: () {},
        child: Text('OK'),
      ),
    ],
  ),
);
```

---

## 🍞 Snackbar Widget
The `Snackbar` widget is used to show temporary pop-up messages at the bottom of the screen.

```dart
ScaffoldMessenger.of(context).showSnackBar(
  SnackBar(
    content: Text('This is a Snackbar!'),
    duration: Duration(seconds: 2),
  ),
);
```

---

## ✅ Summary
- This section includes essential widgets like `Text`, `Image`, `Icon`, `Container`, `ListView`, `GridView`, `Scaffold`, `AppBar`, `BottomNavigationBar`, `Drawer`, `FloatingActionButton`, `DatePicker`, `TimePicker`, `Stepper`, `TabBar`, and `ProgressIndicator`.
- Understanding these widgets will help in developing fully functional Flutter applications.

---

📚 Happy coding! 🚀
