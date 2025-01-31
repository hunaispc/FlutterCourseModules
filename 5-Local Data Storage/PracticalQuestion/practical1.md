# Flutter Storage Methods - Practical Questions

This repository contains practical questions to help Flutter beginners understand different storage methods: Shared Preferences, SQLite, and Hive.

## 1. Shared Preferences (Key-Value Storage)

**Question:**

You are developing a Flutter app that requires a toggle switch for dark mode. The app should remember the user's dark mode preference, even after restarting.

### Task:
- Create a toggle switch in Flutter to enable or disable dark mode.
- Use Shared Preferences to store the dark mode preference (`true` for enabled, `false` for disabled).
- Ensure that when the app restarts, it retains the user's last selected mode.

## 2. SQLite (Local Database)

**Question:**

You are building a simple note-taking app that allows users to add, edit, and delete notes. The notes should persist after the app is closed.

### Task:
- Use SQLite to create a local database table named `notes` with the columns:
  - `id` (integer, primary key, auto-increment)
  - `title` (text)
  - `content` (text)
- Implement functions to:
  - Add a new note
  - Retrieve all notes
  - Update a note
  - Delete a note
- Display the notes in a `ListView`.

## 3. Hive (NoSQL Storage)

**Question:**

You are developing a to-do list app that needs to store tasks efficiently. The app should support adding, marking tasks as completed, and deleting tasks.

### Task:
- Use Hive to store a list of tasks.
- Each task should have:
  - `id` (unique identifier)
  - `title` (task name)
  - `isCompleted` (boolean to indicate completion status)
- Implement functionalities to:
  - Add a task
  - Mark a task as completed/uncompleted
  - Delete a task
- Display tasks in a `ListView` and persist the data after restarting the app.

### Happy Coding! 🚀
