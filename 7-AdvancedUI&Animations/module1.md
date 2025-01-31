# Advanced UI & Animations in Flutter

This study module is designed for beginner Flutter developers to understand and implement advanced UI animations. The module covers:

- **Hero Animations & Lottie**
- **Page Transitions**
- **Rive Animation**

Each section includes step-by-step integration guides with example codes. At the end, a full code example is provided.

## 1. Hero Animations

Hero animations enable smooth transitions between screens while maintaining visual continuity.

### Steps to Implement:

1. Wrap the widget you want to animate with `Hero`.
2. Assign a unique `tag` to identify the hero.
3. Ensure the destination screen also has a `Hero` widget with the same `tag`.

### Example Code:

```dart
import 'package:flutter/material.dart';

void main() {
  runApp(MaterialApp(
    home: FirstScreen(),
  ));
}

class FirstScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text("Hero Animation")),
      body: Center(
        child: GestureDetector(
          onTap: () {
            Navigator.push(
              context,
              MaterialPageRoute(builder: (context) => SecondScreen()),
            );
          },
          child: Hero(
            tag: 'hero-tag',
            child: Image.asset('assets/flutter_logo.png', width: 100),
          ),
        ),
      ),
    );
  }
}

class SecondScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text("Second Screen")),
      body: Center(
        child: Hero(
          tag: 'hero-tag',
          child: Image.asset('assets/flutter_logo.png', width: 200),
        ),
      ),
    );
  }
}
```

## 2. Lottie Animations

Lottie allows adding high-quality vector animations to Flutter apps.

### Steps to Implement:

1. Add `lottie` package to `pubspec.yaml`:

```yaml
dependencies:
  lottie: ^2.3.2
```

2. Load and display a Lottie animation.

### Example Code:

```dart
import 'package:flutter/material.dart';
import 'package:lottie/lottie.dart';

void main() {
  runApp(MaterialApp(
    home: LottieScreen(),
  ));
}

class LottieScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text("Lottie Animation")),
      body: Center(
        child: Lottie.asset('assets/animation.json'),
      ),
    );
  }
}
```

## 3. Page Transitions

Custom page transitions enhance user experience.

### Steps to Implement:

1. Create a custom page transition.
2. Use `PageRouteBuilder` to define transition animations.

### Example Code:

```dart
import 'package:flutter/material.dart';

void main() {
  runApp(MaterialApp(
    home: FirstPage(),
  ));
}

class FirstPage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text("Custom Transition")),
      body: Center(
        child: ElevatedButton(
          onPressed: () {
            Navigator.push(context, CustomPageRoute(SecondPage()));
          },
          child: Text("Go to Second Page"),
        ),
      ),
    );
  }
}

class SecondPage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text("Second Page")),
      body: Center(child: Text("Welcome to Second Page")),
    );
  }
}

class CustomPageRoute extends PageRouteBuilder {
  final Widget page;
  CustomPageRoute(this.page)
      : super(
          pageBuilder: (context, animation, secondaryAnimation) => page,
          transitionsBuilder: (context, animation, secondaryAnimation, child) {
            return FadeTransition(opacity: animation, child: child);
          },
        );
}
```

## 4. Rive Animation

Rive is used for interactive and smooth animations in Flutter.

### Steps to Implement:

1. Add `rive` dependency:

```yaml
dependencies:
  rive: ^0.11.1
```

2. Load and play a Rive animation.

### Example Code:

```dart
import 'package:flutter/material.dart';
import 'package:rive/rive.dart';

void main() {
  runApp(MaterialApp(
    home: RiveScreen(),
  ));
}

class RiveScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text("Rive Animation")),
      body: Center(
        child: RiveAnimation.asset('assets/animation.riv'),
      ),
    );
  }
}
```

## Conclusion

This study module provides a beginner-friendly approach to understanding and integrating advanced UI animations in Flutter. Keep experimenting and enhancing your animations!
