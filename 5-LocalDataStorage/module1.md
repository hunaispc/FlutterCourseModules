# 📦 Local Data Storage in Flutter

Local data storage refers to saving and retrieving data directly on the device, rather than fetching it from the internet or a remote database. This allows apps to access data even when offline, making them more responsive and efficient.

Flutter provides different ways to store data locally, including:

1. **Shared Preferences** (Key-Value Storage)
2. **SQLite** (Local Database)
3. **Hive** (NoSQL Storage)

Each of these methods serves a different purpose depending on the type and amount of data you want to store.

---

## 🏡 Real-World Example: A To-Do List App
Imagine you are building a **To-Do List** app where users can:
✅ Add new tasks  
✅ Mark tasks as completed  
✅ See their tasks even after restarting the app  

Let’s explore how different types of local storage can be used for this app.

---

### 1️⃣ Shared Preferences (Key-Value Storage)
📌 **What it is**:  
A lightweight storage option used to save small amounts of simple data, such as user settings, preferences, or authentication tokens. Data is stored as key-value pairs (like a dictionary).

📌 **When to use it**:  
- Storing user preferences (dark mode, language settings)
- Keeping login states (whether the user is logged in or not)
- Saving simple data like the last opened page

📌 **Example**:  
In our **To-Do List** app, we can use Shared Preferences to:
- Save whether the user prefers **dark mode** (`"darkMode": true`)
- Store the **last opened tab** (`"lastOpened": "completedTasks"`)

🛠 **Code Example**:
```dart
final prefs = await SharedPreferences.getInstance();
await prefs.setBool('darkMode', true);  // Saving a value
bool? isDarkMode = prefs.getBool('darkMode'); // Retrieving the value
```

---

### 2️⃣ SQLite (Local Database)
📌 **What it is**:  
A structured relational database that allows us to store and manage large amounts of structured data using tables (like an Excel sheet). It supports queries using SQL (Structured Query Language).

📌 **When to use it**:  
- Apps that require complex data storage (like task management, note-taking apps)
- Storing large sets of structured data with relationships (e.g., a list of customers and their orders)
- When we need to **search, sort, filter, and update** records efficiently

📌 **Example**:  
In our **To-Do List** app, we can use SQLite to:
- Store all **tasks** with details like title, description, due date, and status
- Allow users to **edit and delete** tasks
- Fetch tasks using filters (e.g., show only completed tasks)

🛠 **Code Example**:
```dart
await database.execute('''
  CREATE TABLE tasks (
    id INTEGER PRIMARY KEY,
    title TEXT,
    description TEXT,
    isCompleted INTEGER
  )
''');
await database.insert('tasks', {'title': 'Buy groceries', 'isCompleted': 0});
```

---

### 3️⃣ Hive (NoSQL Storage)
📌 **What it is**:  
A fast, lightweight NoSQL database that stores data in key-value format, similar to Shared Preferences, but with better performance and support for complex data types.

📌 **When to use it**:  
- Storing structured data without using SQL
- When performance is important (Hive is much faster than SQLite)
- Storing offline data for apps like chat applications or offline e-commerce

📌 **Example**:  
In our **To-Do List** app, we can use Hive to:
- Store tasks as objects instead of tables
- Quickly retrieve, update, and delete tasks
- Load data instantly when the app starts

🛠 **Code Example**:
```dart
var box = await Hive.openBox('tasks');
await box.put('task1', {'title': 'Read a book', 'isCompleted': false});
Map<String, dynamic>? task = box.get('task1');
```

---

## 🔥 Comparison of Storage Methods
| Feature             | Shared Preferences | SQLite         | Hive          |
|---------------------|-------------------|---------------|--------------|
| Data Type          | Key-Value Pairs    | Structured Tables | Key-Value Pairs |
| Performance       | Fast               | Moderate      | Very Fast    |
| Use Case         | Settings, small data | Large structured data | Complex objects, offline storage |
| Offline Support   | Yes                | Yes           | Yes          |

---

## 🎯 Conclusion
Each storage method has its own advantages:

- **Shared Preferences**: Best for saving small settings and user preferences.
- **SQLite**: Best for storing structured data with complex queries.
- **Hive**: Best for high-speed, NoSQL storage for offline-friendly apps.

Understanding these concepts will help you build **better Flutter applications** with **efficient local storage**. 🚀
