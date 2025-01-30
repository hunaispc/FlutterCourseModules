# Basic UI Widgets in Flutter

## 📌 Introduction
Flutter provides a rich set of widgets to create beautiful UIs. These widgets form the building blocks of any Flutter application. In this section, we will explore fundamental UI widgets such as **Text, Image, Icon, Container, Row, Column, ListView, GridView, Stack, ElevatedButton, TextField, Checkbox, and Switch**.

Each of these widgets plays a crucial role in UI design, and understanding them will help you build interactive and visually appealing applications.

---

## 📝 Text Widget
The `Text` widget is used to display simple text on the screen.

### 🔹 Important Parameters:
- `data`: The actual text to be displayed.
- `style`: Defines the text appearance (e.g., font size, color, weight).
- `textAlign`: Aligns text (`left`, `center`, `right`).
- `overflow`: Handles text overflow (`ellipsis`, `fade`, `clip`).

### 🔹 Example:
```dart
Text(
  'Hello, Flutter!',
  style: TextStyle(fontSize: 24, fontWeight: FontWeight.bold),
  textAlign: TextAlign.center,
  overflow: TextOverflow.ellipsis,
)
```

---

## 🖼️ Image Widget
The `Image` widget allows you to display images from various sources like assets, network, or memory.

### 🔹 Important Parameters:
- `image`: The image source (`AssetImage`, `NetworkImage`).
- `width` & `height`: Define image dimensions.
- `fit`: Adjusts how the image fits in the container (`BoxFit.cover`, `BoxFit.contain`).
- `alignment`: Positions the image inside the widget.

### 🔹 Example:
```dart
Image.network(
  'https://flutter.dev/images/flutter-logo-sharing.png',
  width: 100,
  height: 100,
  fit: BoxFit.cover,
)
```

---

## 🔘 Icon Widget
The `Icon` widget is used to display icons from Flutter’s built-in icon library.

### 🔹 Important Parameters:
- `icon`: The actual icon (e.g., `Icons.favorite`).
- `size`: Controls the size of the icon.
- `color`: Defines the color of the icon.

### 🔹 Example:
```dart
Icon(
  Icons.favorite,
  color: Colors.red,
  size: 50,
)
```

---

## 📦 Container Widget
The `Container` widget is used for styling and layout, allowing you to set padding, margins, colors, and decoration.

### 🔹 Important Parameters:
- `width` & `height`: Define the size of the container.
- `color`: Sets the background color.
- `padding` & `margin`: Defines inner and outer spacing.
- `decoration`: Adds borders, shadows, gradients.

### 🔹 Example:
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
The `Row` and `Column` widgets are used to arrange widgets **horizontally** and **vertically**, respectively.

### 🔹 Important Parameters:
- `mainAxisAlignment`: Controls alignment along the main axis.
- `crossAxisAlignment`: Defines alignment along the cross axis.
- `children`: Holds the list of child widgets.

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

### 🔹 Types of ListView:
1. **ListView()** - Default constructor for a simple list.
2. **ListView.builder()** - Uses lazy loading for efficient performance.
3. **ListView.separated()** - Adds separators between list items.
4. **ListView.custom()** - Allows custom implementations.

### 🔹 Example:
```dart
ListView.builder(
  itemCount: 5,
  itemBuilder: (context, index) {
    return ListTile(title: Text('Item \$index'));
  },
)
```

---

## 🔲 GridView Widget
The `GridView` widget arranges items in a grid pattern.

### 🔹 Types of GridView:
1. **GridView.count()** - Creates a grid with a fixed number of columns.
2. **GridView.extent()** - Defines grid size using a max extent.
3. **GridView.builder()** - Uses lazy loading for better performance.
4. **GridView.custom()** - Allows customized grid structures.

### 🔹 Example:
```dart
GridView.builder(
  gridDelegate: SliverGridDelegateWithFixedCrossAxisCount(
    crossAxisCount: 2,
    crossAxisSpacing: 10,
    mainAxisSpacing: 10,
  ),
  itemCount: 4,
  itemBuilder: (context, index) {
    return Container(color: Colors.blue);
  },
)
```

---

## ✅ Summary
- `Text`, `Image`, and `Icon` are used to display content.
- `Container` is a flexible layout container.
- `Row` and `Column` help in arranging widgets.
- `ListView` and `GridView` are used for lists and grids with multiple types.
- `Stack` allows overlaying widgets.
- `ElevatedButton`, `TextField`, `Checkbox`, and `Switch` add interactivity.

---

📚 Happy coding! 🚀
