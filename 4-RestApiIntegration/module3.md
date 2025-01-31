# API Integration with BLoC Listener in Flutter

This guide provides a **step-by-step** tutorial on integrating an API using **Flutter BLoC Listener** for state management. The **sign-in API** will be triggered **on button click**, and BLoC will manage the API request-response cycle.

---

## 🚀 **Steps to Implement API Call using BLoC Listener**
1. **Setup Dependencies**
2. **Create Project Structure**
3. **Create API Client**
4. **Create API Repository**
5. **Define BLoC Events & States**
6. **Implement BLoC Logic**
7. **Use BLoC Listener in UI**
8. **Call API on Button Click**

---

## 1️⃣ **Setup Dependencies**
Add the following dependencies in `pubspec.yaml`:
```yaml
dependencies:
  flutter:
    sdk: flutter
  flutter_bloc: ^8.1.3
  http: ^0.13.6
```
Run:
```sh
flutter pub get
```

---

## 2️⃣ **Project Structure**
```
/lib
  ├── /bloc             # BLoC files (events, states, bloc class)
  ├── /models           # Data models
  ├── /repositories     # API interactions
  ├── /screens          # UI Screens
  ├── main.dart         # Entry point
```

---

## **3. Create API Client Class**
Create `repositories/api_client.dart`:
```dart
import 'dart:convert';
import 'dart:developer';
import 'package:http/http.dart';

import 'api_exception.dart';

class ApiClient {
  Future<Response> invokeAPI(String path, String method, Object? body) async {
    Map<String, String> headerParams = {};
    Response response;

    String url = path;
    print(url);

    final nullableHeaderParams = (headerParams.isEmpty) ? null : headerParams;
    print(body);
    switch (method) {
      case "POST":
        response = await post(Uri.parse(url),
            headers: {
              'content-Type': 'application/x-www-form-urlencoded',
            },
            body: body);

        break;
      case "PUT":
        response = await put(Uri.parse(url),
            headers: {
              'content-Type': 'application/json',
            },
            body: body);
        break;
      case "DELETE":
        response = await delete(Uri.parse(url), headers: {}, body: body);
        break;
      case "POST_":
        response = await post(
          Uri.parse(url),
          headers: {'content-Type': 'application/json'},
          body: body,
        );
        break;
      case "GET_":
        response = await post(
          Uri.parse(url),
          headers: {},
          body: body,
        );
        break;
      case "GET":
        response = await get(
          Uri.parse(url),
          headers: {
           'X-RapidAPI-Key': 'YOUR_API_KEY',
            'X-RapidAPI-Host': 'anime-db.p.rapidapi.com',
            'Accept': 'application/json',
            'Content-Type': 'application/json'
          },
        );

        break;
      case "PATCH":
        response = await patch(
          Uri.parse(url),
          headers: {'Content-Type': 'application/json'},
          body: body,
        );
        break;
      case "PATCH1":
        response = await patch(
          Uri.parse(url),
          headers: {},
          body: body,
        );
        break;
      default:
        response = await get(Uri.parse(url), headers: {
          'Accept': 'application/json',
          'Content-Type': 'application/json'
        });
    }

    print('status of $path =>' + (response.statusCode).toString());
    print(response.body);
    if (response.statusCode >= 400) {
      log(path +
          ' : ' +
          response.statusCode.toString() +
          ' : ' +
          response.body);

      throw ApiException(_decodeBodyBytes(response), response.statusCode);
    }
    return response;
  }

  String _decodeBodyBytes(Response response) {
    var contentType = response.headers['content-type'];
    if (contentType != null && contentType.contains("application/json")) {
      return jsonDecode(response.body)['message'];
    } else {
      return response.body;
    }
  }
}
```

## **4. Create API Exception Class**
Create `repositories/api_exception.dart`:
```dart
class ApiException implements Exception {
  final String message;
  final int statusCode;
  ApiException(this.message, this.statusCode);
}
```


---

## 4️⃣ **Create API Repository**
Create `repositories/auth_repository.dart`:
```dart
import 'dart:convert';
import '../models/auth_model.dart';
import 'api_client.dart';
import 'package:http/http.dart';

class AuthRepository {
  final ApiClient apiClient = ApiClient();

  Future<AuthModel> signIn(String email, String password) async {
    String url = "http://45.159.221.50:9890/api/signin";
        var body = {
      "email": email,
      "password": password,
    };
    Response response = await apiClient.invokeAPI(url,body);

    return AuthModel.fromJson(jsonDecode(response.body));
  }
}
```

---

## 5️⃣ **Define BLoC Events & States**

### 📌 **Create BLoC Events**
Create `bloc/auth_event.dart`:
```dart
abstract class AuthEvent {}

class SignInEvent extends AuthEvent {
  final String email;
  final String password;
  
  SignInEvent({required this.email, required this.password});
}
```

### 📌 **Create BLoC States**
Create `bloc/auth_state.dart`:
```dart
import '../models/auth_model.dart';

abstract class AuthState {}

class AuthInitial extends AuthState {}

class AuthLoading extends AuthState {}

class AuthSuccess extends AuthState {}

class AuthFailure extends AuthState {}
```

---

## 6️⃣ **Implement BLoC Logic**
Create `bloc/auth_bloc.dart`:
```dart
import 'package:flutter_bloc/flutter_bloc.dart';
import '../repositories/auth_repository.dart';
import 'auth_event.dart';
import 'auth_state.dart';

class AuthBloc extends Bloc<AuthEvent, AuthState> {
  final AuthRepository authRepository;
 final AuthModel authModel;
  AuthBloc({required this.authRepository}) : super(AuthInitial()) {
    on<SignInEvent>((event, emit) async {
      emit(AuthLoading());
      try {
         authModel = await authRepository.signIn(event.email, event.password);
        emit(AuthSuccess());
      } catch (e) {
        emit(AuthFailure());
      }
    });
  }
}
```

---
## **7. Initialize the BLoC in main.dart**
```dart
void main() {
  runApp(BlocProvider(
    create: (context) => AuthBloc(),
    child: MaterialApp(home: HomeScreen()),
  ));
}
```
## 8 **Use BLoC Listener in UI**
Create `screens/login_screen.dart`:
```dart
import 'package:flutter/material.dart';
import 'package:flutter_bloc/flutter_bloc.dart';
import '../bloc/auth_bloc.dart';
import '../bloc/auth_event.dart';
import '../bloc/auth_state.dart';

class LoginScreen extends StatelessWidget {
  final TextEditingController emailController = TextEditingController();
  final TextEditingController passwordController = TextEditingController();

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text("Login")),
      body: Padding(
        padding: EdgeInsets.all(16.0),
        child: Column(
          children: [
            TextField(
              controller: emailController,
              decoration: InputDecoration(labelText: "Email"),
            ),
            TextField(
              controller: passwordController,
              decoration: InputDecoration(labelText: "Password"),
              obscureText: true,
            ),
            SizedBox(height: 20),
            BlocListener<AuthBloc, AuthState>(
              listener: (context, state) {
                if (state is AuthLoading) {
                  ScaffoldMessenger.of(context).showSnackBar(
                    SnackBar(content: Text("Logging in..."))
                  );
                } else if (state is AuthSuccess) {
                  ScaffoldMessenger.of(context).showSnackBar(
                    SnackBar(content: Text("Login Successful"))
                  );
                } else if (state is AuthFailure) {
                  ScaffoldMessenger.of(context).showSnackBar(
                    SnackBar(content: Text("Error: ${state.error}"))
                  );
                }
              },
              child: ElevatedButton(
                onPressed: () {
                  final email = emailController.text;
                  final password = passwordController.text;
                  context.read<AuthBloc>().add(SignInEvent(email: email, password: password));
                },
                child: Text("Login"),
              ),
            ),
          ],
        ),
      ),
    );
  }
}
```

🎉 **Your API integration using BLoC Listener is now complete!** 🚀

