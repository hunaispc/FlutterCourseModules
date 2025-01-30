# 🚗 Car Rent App UI Design Task

## 🎯 Task Overview
Your task is to design the **Car Rent App UI** based on the provided Figma design. The goal is to create a **pixel-perfect, responsive UI** in Flutter that matches the design layout for different screen sizes (mobile, tablet, and web).

📌 **Figma File:** [Car Rent App UI Design](https://www.figma.com/design/sdtBvHQEoNDpcj6OkIeYcc/Car-Rent-App-(Community)?node-id=0-1&p=f&t=4tboKFQAJ91H27Xj-0)

---

## 📌 Requirements
### 🔹 General Guidelines
- Ensure the UI is **responsive** across different screen sizes.
- Use **clean, reusable widgets** to maintain code quality.
- Follow **Material Design principles** while implementing the UI.
- Maintain **proper spacing, typography, and colors** as per the Figma design.

### 🔹 UI Components to Implement
1. **Splash Screen**
   - Display the app logo and animated loading effect.
2. **Onboarding Screens**
   - Implement a carousel with smooth transitions.
3. **Login & Sign-up Screens**
   - Form validation for email, password, and other inputs.
4. **Home Screen**
   - Display available cars with search & filter functionality.
5. **Car Details Screen**
   - Show car images, price, description, and booking options.
6. **Booking & Payment Screens**
   - Provide date selection, price calculation, and payment options.
7. **User Profile & Settings**
   - Allow users to edit profile and view booking history.

---

## 📐 Development Approach
### ✅ Tools & Packages to Use
- **Flutter** (Framework)
- **flutter_screenutil** (For responsive UI scaling)
- **provider / Riverpod** (State management)
- **cached_network_image** (For optimized image loading)
- **google_fonts** (For custom fonts)

### ✅ Folder Structure Suggestion
```
lib/
|-- main.dart
|-- screens/
|   |-- splash_screen.dart
|   |-- onboarding_screen.dart
|   |-- login_screen.dart
|   |-- home_screen.dart
|   |-- car_details_screen.dart
|   |-- booking_screen.dart
|   |-- profile_screen.dart
|
|-- widgets/
|   |-- custom_button.dart
|   |-- car_card.dart
|   |-- search_bar.dart
|   |-- rating_stars.dart
|
|-- providers/
|   |-- car_provider.dart
|   |-- auth_provider.dart
|
|-- utils/
|   |-- app_colors.dart
|   |-- app_text_styles.dart
|   |-- app_constants.dart
```

---

## 🔥 Deliverables
- **Fully functional Flutter UI matching the Figma design.**
- **Screens should be responsive across all devices.**
- **Push the project to a GitHub repository for review.**

---

## 📅 Deadline
Please complete the UI development within **X days** and submit the GitHub repository link.

🎨 **Happy Designing & Coding! 🚀**
