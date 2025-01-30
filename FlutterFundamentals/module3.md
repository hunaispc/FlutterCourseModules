# Basic UI Widgets in Flutter

## 📌 Introduction
Flutter provides a rich set of widgets to create beautiful UIs. These widgets form the building blocks of any Flutter application. In this section, we will explore fundamental UI widgets such as **Text, Image, Icon, Container, Row, Column, ListView, GridView, Stack, ElevatedButton, OutlinedButton, TextButton, TextField, Checkbox, Switch, Slider, Radio, DropdownButton, Card, AppBar, Scaffold, BottomNavigationBar, Drawer, FloatingActionButton, AlertDialog, Snackbar, ProgressIndicator, Chip, Divider, ExpansionTile, Tooltip, SizedBox, Padding, Align, Center, Visibility, Wrap, GestureDetector, and ClipRRect**.

Each of these widgets plays a crucial role in UI design, and understanding them will help you build interactive and visually appealing applications.

---

## 📋 ListView Widget
The `ListView` widget is a scrollable list of widgets.

### 🔹 Types of ListView:

#### 1️⃣ ListView()
A simple list that displays all its children at once.

```dart
ListView(
  children: [
    ListTile(title: Text('Item 1')),
    ListTile(title: Text('Item 2')),
    ListTile(title: Text('Item 3')),
  ],
)
```

#### 2️⃣ ListView.builder()
Creates list items lazily as they scroll into view, optimizing performance.

```dart
ListView.builder(
  itemCount: 10,
  itemBuilder: (context, index) {
    return ListTile(title: Text('Item \$index'));
  },
)
```

#### 3️⃣ ListView.separated()
Adds dividers between list items.

```dart
ListView.separated(
  itemCount: 5,
  separatorBuilder: (context, index) => Divider(),
  itemBuilder: (context, index) {
    return ListTile(title: Text('Item \$index'));
  },
)
```

#### 4️⃣ ListView.custom()
Allows for a completely customizable list layout.

```dart
ListView.custom(
  childrenDelegate: SliverChildBuilderDelegate(
    (context, index) => ListTile(title: Text('Custom Item \$index')),
    childCount: 5,
  ),
)
```

---

## 🔲 GridView Widget
The `GridView` widget arranges items in a grid pattern.

### 🔹 Types of GridView:

#### 1️⃣ GridView.count()
Creates a grid with a fixed number of columns.

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

#### 2️⃣ GridView.extent()
Creates a grid where each item has a maximum cross-axis extent.

```dart
GridView.extent(
  maxCrossAxisExtent: 100,
  children: [
    Container(color: Colors.purple),
    Container(color: Colors.orange),
    Container(color: Colors.pink),
    Container(color: Colors.cyan),
  ],
)
```

#### 3️⃣ GridView.builder()
Creates grid items dynamically as they scroll into view.

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

#### 4️⃣ GridView.custom()
Allows for a completely customizable grid layout.

```dart
GridView.custom(
  gridDelegate: SliverGridDelegateWithFixedCrossAxisCount(
    crossAxisCount: 3,
  ),
  childrenDelegate: SliverChildBuilderDelegate(
    (context, index) => Container(color: Colors.grey),
    childCount: 6,
  ),
)
```

---

## ✅ Summary
- `ListView` has four types: `ListView()`, `ListView.builder()`, `ListView.separated()`, and `ListView.custom()`.
- `GridView` has four types: `GridView.count()`, `GridView.extent()`, `GridView.builder()`, and `GridView.custom()`.
- Using `builder()` versions helps improve performance in large lists and grids.

---

📚 Happy coding! 🚀
