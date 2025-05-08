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
```dart
ListView.separated(
  itemCount: 10,
  itemBuilder: (context, index) {
    return ListTile(title: Text('Item \$index'));
  },
  separatorBuilder: (context, index) {
    return Divider(); // Or any widget like SizedBox(height: 10)
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
### FloatingActionButton
A circular button used for primary actions.

```dart
FloatingActionButton(
  onPressed: () {},
  child: Icon(Icons.add),
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
## 🏠 Scaffold & AppBar
The `Scaffold` widget provides a structure for the visual interface, including an `AppBar`.

```dart
Scaffold(
  appBar: AppBar(title: Text('Flutter App')),
  body: Center(child: Text('Hello, World!')),
)
```

---

## 📌 BottomNavigationBar Widget
The `BottomNavigationBar` allows users to navigate between different sections of the app.

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

## 🏷️ TabBar Widget
The `TabBar` widget allows navigation between different pages.

```dart
DefaultTabController(
  length: 3,
  child: Scaffold(
    appBar: AppBar(
      bottom: TabBar(
        tabs: [
          Tab(text: 'Tab 1'),
          Tab(text: 'Tab 2'),
          Tab(text: 'Tab 3'),
        ],
      ),
    ),
    body: TabBarView(
      children: [
        Center(child: Text('Content 1')),
        Center(child: Text('Content 2')),
        Center(child: Text('Content 3')),
      ],
    ),
  ),
)
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
## ✅ Additional Widgets

### ✅ Checkbox Widget
The `Checkbox` widget allows users to toggle between checked and unchecked states.

```dart
Checkbox(
  value: true,
  onChanged: (bool? newValue) {},
)
```

---

### 🔄 Switch Widget
The `Switch` widget is used to toggle between ON and OFF states.

```dart
Switch(
  value: true,
  onChanged: (bool newValue) {},
)
```

---

### 🎚️ Slider Widget
The `Slider` widget allows users to select a value from a range.

```dart
Slider(
  value: 50,
  min: 0,
  max: 100,
  onChanged: (double newValue) {},
)
```

---

### 🎯 Radio Widget
The `Radio` widget allows users to select a single option from multiple choices.

```dart
Radio(
  value: 1,
  groupValue: 1,
  onChanged: (int? newValue) {},
)
```

---

### 🔽 DropdownButton Widget
The `DropdownButton` widget provides a dropdown list of selectable items.

```dart
DropdownButton(
  value: 'Option 1',
  items: [
    DropdownMenuItem(value: 'Option 1', child: Text('Option 1')),
    DropdownMenuItem(value: 'Option 2', child: Text('Option 2')),
  ],
  onChanged: (String? newValue) {},
)
```

---

### 🏷️ Card Widget
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

### 🎭 Chip Widget
The `Chip` widget is used to display a small piece of information.

```dart
Chip(
  label: Text('Flutter'),
  avatar: Icon(Icons.tag),
)
```

---

### 🔄 Divider Widget
The `Divider` widget creates a horizontal separator.

```dart
Divider(color: Colors.grey)
```

---

### 📂 ExpansionTile Widget
The `ExpansionTile` widget is used to create expandable sections.

```dart
ExpansionTile(
  title: Text('Tap to Expand'),
  children: [
    ListTile(title: Text('Option 1')),
    ListTile(title: Text('Option 2')),
  ],
)
```

---

### 🏷️ Tooltip Widget
The `Tooltip` widget displays a message when a user long-presses on a widget.

```dart
Tooltip(
  message: 'This is a tooltip',
  child: Icon(Icons.info),
)
```

---

### 📏 Padding Widget
The `Padding` widget adds spacing around a child widget.

```dart
Padding(
  padding: EdgeInsets.all(16.0),
  child: Text('Padded Text'),
)
```

---

### 📍 Align Widget
The `Align` widget positions its child within itself.

```dart
Align(
  alignment: Alignment.center,
  child: Text('Centered Text'),
)
```

---

### 🎯 Center Widget
The `Center` widget aligns a child in the middle of its parent.

```dart
Center(
  child: Text('Centered Text'),
)
```

---

### 👁️ Visibility Widget
The `Visibility` widget controls whether a widget is visible.

```dart
Visibility(
  visible: true,
  child: Text('Visible Text'),
)
```

---

### 🔄 Wrap Widget
The `Wrap` widget wraps its children to avoid overflow.

```dart
Wrap(
  children: [
    Chip(label: Text('Chip 1')),
    Chip(label: Text('Chip 2')),
  ],
)
```

---

### 🎯 GestureDetector Widget
The `GestureDetector` widget detects gestures like taps, swipes, and long presses.

```dart
GestureDetector(
  onTap: () {
    print('Tapped!');
  },
  child: Container(width: 100, height: 100, color: Colors.blue),
)
```

---

### 🔲 ClipRRect Widget
The `ClipRRect` widget applies rounded corners to its child.

```dart
ClipRRect(
  borderRadius: BorderRadius.circular(10),
  child: Image.network('https://flutter.dev/images/flutter-logo-sharing.png'),
)
```

---
## ✅ Summary
- Understanding these widgets will help in developing fully functional Flutter applications.

---

📚 Happy coding! 🚀
