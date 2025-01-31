# Flutter Firebase E-Commerce Project

## Project Overview
This project is designed to help beginners understand Firebase integration in a Flutter e-commerce application. The project will include three main features:
- **Authentication**: Users should be able to register, log in, and log out using Firebase Authentication.
- **Database**: Store and retrieve product details and user-related data using Firebase Firestore.
- **Push Notifications**: Implement Firebase Cloud Messaging (FCM) to send notifications about new products or offers.

---

## Practical Task
### Task: Build a Simple Flutter Firebase E-Commerce App

### **Requirements**

1. **Authentication**:
   - Implement Firebase Authentication.
   - Allow users to register using email and password.
   - Implement a login system.
   - Provide a logout button.
   
2. **Database (Firestore)**:
   - Store product details (e.g., name, price, image URL, description) in Firebase Firestore.
   - Fetch and display product listings.
   - Allow users to add products to a shopping cart.

3. **Push Notifications**:
   - Integrate Firebase Cloud Messaging (FCM).
   - Allow the app to receive notifications about new product arrivals and special offers.
   - Send a test notification to all users.

---

## **Project Setup Instructions**
### **Step 1: Firebase Setup**
1. Create a new Firebase project at [Firebase Console](https://console.firebase.google.com/).
2. Enable **Email/Password Authentication** in Firebase Authentication.
3. Enable **Firestore Database** and set up basic rules (`allow read, write: if request.auth != null;` for testing).
4. Set up **Firebase Cloud Messaging (FCM)** for push notifications.

### **Step 2: Project Implementation**
- Initialize Firebase in your Flutter project.
- Implement authentication logic.
- Set up Firestore to store and retrieve product data.
- Implement push notifications using FCM.
- 
## **Project Submission**
Once you complete the project:
1. Push your code to a GitHub repository.
2. Share the GitHub link in the classroom.

---

Happy coding! 🚀

