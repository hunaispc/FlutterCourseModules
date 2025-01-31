# API Integration Using BLoC in Flutter

This guide provides a step-by-step tutorial on integrating an API using **Flutter BLoC** for state management. It uses **Rapid API** for fetching data, **Postman** for testing API responses, and **JSON to Dart** for creating models.

---

## **Project Setup**

### 1. **Create a New Flutter Project**
```sh
flutter create bloc_api_demo
```
Change directory:
```sh
cd bloc_api_demo
```

### 2. **Install Dependencies**
Edit `pubspec.yaml` and add:
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

## **Project Structure**

```
/lib
  ├── /bloc         # BLoC files (events, states, bloc classes)
  ├── /models       # Data models
  ├── /repositories # API interactions
  ├── /screens      # UI Screens
  ├── /widgets      # Reusable components
  ├── main.dart     # Entry point
```

---

## **Creating the API Model**

### **1. Fetch API Response in Postman**
Use Postman to test this API:
```
https://anime-db.p.rapidapi.com/anime?page=1&size=10&search=Fullmetal&genres=Fantasy,Drama&sortBy=ranking&sortOrder=asc
```
Headers:
```json
{
  "X-RapidAPI-Key": "YOUR_API_KEY",
  "X-RapidAPI-Host": "anime-db.p.rapidapi.com",
  "Accept": "application/json",
  "Content-Type": "application/json"
}
```

### **2. Convert JSON to Dart Model**
Use [json-to-dart](https://jsontodart.zariman.dev/) to generate the model. Create `models/anime_model.dart`:
```dart
class AnimeModel {
  List<Data>? data;
  Meta? meta;

  AnimeModel({this.data, this.meta});

  AnimeModel.fromJson(Map<String, dynamic> json) {
    data = json['data']?.map((v) => Data.fromJson(v)).toList();
    meta = json['meta'] != null ? Meta.fromJson(json['meta']) : null;
  }
}

class Meta {
  int? page, size, totalData, totalPage;
  Meta({this.page, this.size, this.totalData, this.totalPage});
}

class Data {
  String? id, title, image;
  Data({this.id, this.title, this.image});
}
```

---

## **3. Create API Client Class**
Create `repositories/api_client.dart`:
```dart
import 'dart:convert';
import 'package:http/http.dart' as http;
import 'api_exception.dart';

class ApiClient {
  Future<http.Response> invokeAPI(String url, String method) async {
    final headers = {
      'X-RapidAPI-Key': 'YOUR_API_KEY',
      'X-RapidAPI-Host': 'anime-db.p.rapidapi.com',
      'Accept': 'application/json',
      'Content-Type': 'application/json',
    };

    if (method == "GET") {
      final response = await http.get(Uri.parse(url), headers: headers);
      if (response.statusCode >= 400) {
        throw ApiException(response.body, response.statusCode);
      }
      return response;
    } else {
      throw ApiException("Invalid HTTP method", 405);
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
## **4. Create API Class**
Create `repositories/anime_repository.dart`:
```dart
import 'dart:convert';
import 'package:http/http.dart';
import '../models/anime_model.dart';
import 'api_client.dart';

class AnimeRepository {
  ApiClient apiClient = ApiClient();
  Future<AnimeModel> getAnime() async {
    String url = 'https://anime-db.p.rapidapi.com/anime?page=1&size=10&search=Fullmetal&genres=Fantasy,Drama&sortBy=ranking&sortOrder=asc';
    Response response = await apiClient.invokeAPI(url, 'GET');
    return AnimeModel.fromJson(jsonDecode(response.body));
  }
}
```

---

## **5. Create BLoC for State Management**

Create `bloc/anime_event.dart`:
```dart
abstract class AnimeEvent {}
class FetchAnimeEvent extends AnimeEvent {}
```

Create `bloc/anime_state.dart`:
```dart
import '../models/anime_model.dart';
abstract class AnimeState {}
class AnimeblocInitial extends AnimeState {}
class AnimeblocLoading extends AnimeState {}
class AnimeblocLoaded extends AnimeState {
  final AnimeModel animeModel;
  AnimeblocLoaded(this.animeModel);
}
class AnimeblocError extends AnimeState {
  final String error;
  AnimeblocError(this.error);
}
```

Create `bloc/anime_bloc.dart`:
```dart
import 'package:flutter_bloc/flutter_bloc.dart';
import '../repositories/anime_repository.dart';
import 'anime_event.dart';
import 'anime_state.dart';

class AnimeBloc extends Bloc<AnimeEvent, AnimeState> {
  final AnimeRepository animeRepository;
  AnimeBloc({required this.animeRepository}) : super(AnimeblocInitial()) {
    on<FetchAnimeEvent>((event, emit) async {
      emit(AnimeblocLoading());
      try {
        final animeModel = await animeRepository.getAnime();
        emit(AnimeblocLoaded(animeModel));
      } catch (e) {
        emit(AnimeblocError(e.toString()));
      }
    });
  }
}
```

---
---

## **6. Initialize the bloc in main**
Update `main.dart`:
```dart
void main() {
  runApp(BlocProvider(
    create: (context) => AnimeBloc(animeRepository: AnimeRepository()),
    child: MaterialApp(home: HomeScreen()),
  ));
}
```
## **7. Integrate BLoC in UI**
Create `screens/home_screen.dart`:
```dart
import 'package:flutter/material.dart';
import 'package:flutter_bloc/flutter_bloc.dart';
import '../bloc/anime_bloc.dart';
import '../bloc/anime_event.dart';
import '../bloc/anime_state.dart';

class HomeScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text("Anime List")),
      body: BlocBuilder<AnimeBloc, AnimeState>(
        builder: (context, state) {
          if (state is AnimeblocLoading) return Center(child: CircularProgressIndicator());
          if (state is AnimeblocError) return Center(child: Text("Error: ${state.error}"));
          if (state is AnimeblocLoaded) {
            return ListView.builder(
              itemCount: state.animeModel.data?.length ?? 0,
              itemBuilder: (context, index) {
                final anime = state.animeModel.data![index];
                return ListTile(
                  leading: Image.network(anime.image ?? ''),
                  title: Text(anime.title ?? ''),
                );
              },
            );
          }
          return Center(child: Text("Press button to fetch data"));
        },
      ),
      floatingActionButton: FloatingActionButton(
        onPressed: () => context.read<AnimeBloc>().add(FetchAnimeEvent()),
        child: Icon(Icons.download),
      ),
    );
  }
}
```
Run:
```sh
flutter run
```
🎉 **Your API integration using BLoC is complete!**

