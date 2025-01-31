# Feedback API Integration Using BLoC

## Overview
This project demonstrates how to integrate a **feedback system** using the **BLoC architecture** in Flutter. Users can submit feedback, view all feedback, update their previous feedback, and delete feedback through API calls.

## API Endpoints

### 1. Create Feedback (POST)
**Endpoint:** `http://45.159.221.50:8868/api/feedback`

**Request Body:**
```json
{
  "user": "66ceb30f2dc300b0b85f6244",
  "experience": "Renting",
  "rating": 5,
  "comments": "The rental process was excellent!"
}
```

### 2. Get All Feedback (GET)
**Endpoint:** `http://45.159.221.50:8868/api/feedback`

### 3. Update Feedback (PUT)
**Endpoint:** `http://45.159.221.50:8868/api/feedback/66f240a2fd798d8701d00031`

**Request Body:**
```json
{
  "rating": 4,
  "comments": "The rental experience was good, but the car had a minor issue."
}
```

### 4. Delete Feedback (DELETE)
**Endpoint:** `http://45.159.221.50:8868/api/feedback/66f240a2fd798d8701d00031`

## Task
### Implement a Feedback System Using BLoC
Your task is to build a **Feedback Feature** using Flutter and BLoC that supports the following:
1. **Fetch all feedback** and display it in a list.
2. **Allow users to submit feedback** by providing a rating, experience type, and comments.
3. **Enable users to update their feedback** by modifying the rating and comments.
4. **Give users the ability to delete feedback.**

## Steps to Implement

### 1. Define BLoC Events & States
- Create a `FeedbackEvent` class to handle various API operations.
- Create a `FeedbackState` class to represent different states such as loading, success, and failure.

### 2. Create a Repository Layer
- Implement a `FeedbackRepository` class that interacts with the API.
- Use the `http` package to perform **GET, POST, PUT, and DELETE** requests.

### 3. Implement FeedbackBloc
- Develop a `FeedbackBloc` class to manage state changes.
- Handle API calls and emit different states based on success or failure.

### 4. Build the Flutter UI
- Use `BlocBuilder` to display the feedback list.
- Use `BlocListener` to handle API responses such as success messages or errors.
- Implement buttons for **submitting, updating, and deleting feedback.**

## Challenge
### Optimize API Calls & State Management
- Implement caching strategies to reduce unnecessary API calls.
- Use **debouncing** for handling user input efficiently.
- Ensure **error handling** and **loading indicators** are correctly displayed.

## Bonus
How would you implement **pagination** if there were a large number of feedback entries?

---
This README serves as a guide to structuring your **BLoC-based API integration project** in Flutter.
