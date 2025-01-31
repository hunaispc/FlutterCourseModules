# Firebase Integration in Flutter

## Introduction

Firebase is a backend-as-a-service (BaaS) provided by Google, allowing developers to integrate various backend services like authentication, real-time databases, cloud functions, and more. This guide will walk you through integrating Firebase Authentication (Email, Google, OTP).

## Prerequisites

- Basic knowledge of Flutter
- Flutter SDK installed
- Firebase account setup
- Android/iOS emulator or a physical device

## Step 1: Create a Firebase Project

1. Go to [Firebase Console](https://console.firebase.google.com/).
2. Click on "Add Project" and follow the instructions.
3. Register the app (Android & iOS) and download the `google-services.json` (Android) or `GoogleService-Info.plist` (iOS).
4. Add the downloaded file to the respective platform folders in your Flutter project.

## Step 2: Add Firebase to Your Flutter App

Run the following command to install required dependencies:

```sh
flutter pub add firebase_core firebase_auth google_sign_in
```

Update the `main.dart` file to initialize Firebase:

```dart
import 'package:firebase_core/firebase_core.dart';
import 'package:flutter/material.dart';

void main() async {
  WidgetsFlutterBinding.ensureInitialized();
  await Firebase.initializeApp();
  runApp(MyApp());
}
```

## Step 3: Firebase Authentication Setup

### Getting SHA-1 and SHA-256 Keys

For Google and Phone Authentication, add the SHA keys to Firebase:

```sh
# Run this command in the terminal
keytool -list -v -alias androiddebugkey -keystore ~/.android/debug.keystore -storepass android -keypass android
```

Copy the SHA-1 and SHA-256 keys and add them to the Firebase project settings under "SHA Certificate Fingerprints".

### Email/Password Authentication

Enable email authentication in Firebase Console:

1. Go to Authentication > Sign-in method.
2. Enable Email/Password sign-in.

#### Register User with Email/Password

```dart
import 'package:firebase_auth/firebase_auth.dart';

Future<void> signUpWithEmail(String email, String password) async {
  try {
    UserCredential userCredential = await FirebaseAuth.instance.createUserWithEmailAndPassword(
      email: email,
      password: password,
    );
    print("User Registered: ${userCredential.user?.email}");
  } catch (e) {
    print("Error: $e");
  }
}
```

#### Login with Email/Password

```dart
Future<void> loginWithEmail(String email, String password) async {
  try {
    UserCredential userCredential = await FirebaseAuth.instance.signInWithEmailAndPassword(
      email: email,
      password: password,
    );
    print("User Logged In: ${userCredential.user?.email}");
  } catch (e) {
    print("Error: $e");
  }
}
```

### Google Authentication

Enable Google sign-in in Firebase Console.

#### Integrate Google Sign-In

```dart
import 'package:firebase_auth/firebase_auth.dart';
import 'package:google_sign_in/google_sign_in.dart';

Future<void> signInWithGoogle() async {
  final GoogleSignInAccount? googleUser = await GoogleSignIn().signIn();
  final GoogleSignInAuthentication? googleAuth = await googleUser?.authentication;
  final AuthCredential credential = GoogleAuthProvider.credential(
    accessToken: googleAuth?.accessToken,
    idToken: googleAuth?.idToken,
  );
  await FirebaseAuth.instance.signInWithCredential(credential);
  print("User Signed In with Google");
}
```

### OTP Authentication

Enable Phone authentication in Firebase Console.

#### Sending OTP

```dart
import 'package:firebase_auth/firebase_auth.dart';

Future<void> sendOTP(String phoneNumber) async {
  await FirebaseAuth.instance.verifyPhoneNumber(
    phoneNumber: phoneNumber,
    verificationCompleted: (PhoneAuthCredential credential) async {
      await FirebaseAuth.instance.signInWithCredential(credential);
    },
    verificationFailed: (FirebaseAuthException e) {
      print("Error: $e");
    },
    codeSent: (String verificationId, int? resendToken) {
      print("Code Sent: $verificationId");
    },
    codeAutoRetrievalTimeout: (String verificationId) {},
  );
}
```

#### Verifying OTP

```dart
Future<void> verifyOTP(String verificationId, String smsCode) async {
  PhoneAuthCredential credential = PhoneAuthProvider.credential(
    verificationId: verificationId,
    smsCode: smsCode,
  );
  await FirebaseAuth.instance.signInWithCredential(credential);
  print("OTP Verified and User Logged In");
}
```

## Full Example Code

```dart
import 'package:flutter/material.dart';
import 'package:firebase_core/firebase_core.dart';
import 'package:firebase_auth/firebase_auth.dart';
import 'package:google_sign_in/google_sign_in.dart';

void main() async {
  WidgetsFlutterBinding.ensureInitialized();
  await Firebase.initializeApp();
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: AuthScreen(),
    );
  }
}

class AuthScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('Firebase Authentication')),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            ElevatedButton(
              onPressed: () async {
                await signUpWithEmail("test@example.com", "password123");
              },
              child: Text("Sign Up with Email"),
            ),
            ElevatedButton(
              onPressed: () async {
                await loginWithEmail("test@example.com", "password123");
              },
              child: Text("Login with Email"),
            ),
            ElevatedButton(
              onPressed: () async {
                await signInWithGoogle();
              },
              child: Text("Sign in with Google"),
            ),
            ElevatedButton(
              onPressed: () async {
                await sendOTP("+1234567890");
              },
              child: Text("Send OTP"),
            ),
          ],
        ),
      ),
    );
  }
}
```

## Conclusion

This guide covered Firebase Authentication (Email, Google, OTP) with Flutter. With this knowledge, you can build authentication features for your app.
