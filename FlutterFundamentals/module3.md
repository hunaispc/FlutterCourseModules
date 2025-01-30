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

### 🔹 Important Parameters:
- `children`: Holds list items.
- `scrollDirection`: Defines horizontal or vertical scrolling.
- `shrinkWrap`: Adjusts size to fit content.

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

### 🔹 Important Parameters:
- `crossAxisCount`: Defines number of columns.
- `children`: Holds grid items.
- `mainAxisSpacing` & `crossAxisSpacing`: Defines spacing.

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

### 🔹 Important Parameters:
- `alignment`: Positions child widgets.
- `children`: Holds stacked widgets.

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

### 🔹 Important Parameters:
- `onPressed`: Callback function when pressed.
- `child`: Defines the button’s content.

### 🔹 Example:
```dart
ElevatedButton(
  onPressed: () {},
  child: Text('Click Me'),
)
```

---

## ✅ Checkbox Widget
The `Checkbox` widget allows users to select an option.

### 🔹 Important Parameters:
- `value`: Holds true/false state.
- `onChanged`: Callback when value changes.

### 🔹 Example:
```dart
Checkbox(value: true, onChanged: (newValue) {})
```

---

## 🔄 Switch Widget
The `Switch` widget is used to toggle between ON and OFF states.

### 🔹 Important Parameters:
- `value`: Boolean state.
- `onChanged`: Callback function.

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
