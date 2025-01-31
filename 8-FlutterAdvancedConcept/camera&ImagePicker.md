# Camera & Image Picker in Flutter - Beginner Guide

## Introduction
In this guide, we will learn how to use the **Camera** and **Image Picker** in Flutter to capture images and select images from the gallery. We will go step-by-step to ensure even absolute beginners can follow along.

## Prerequisites
Before starting, make sure you have:
- Flutter installed
- A basic understanding of Flutter widgets
- A working emulator or a real device

## Step 1: Adding Dependencies
Flutter provides two packages to work with images:

- `image_picker`: Allows selecting images from the gallery and taking pictures with the camera.
- `camera`: Allows full access to the camera for capturing images and videos.

Add the dependencies in your **pubspec.yaml** file:

```yaml
dependencies:
  flutter:
    sdk: flutter
  image_picker: ^1.0.4
  camera: ^0.10.5+4
```

Run `flutter pub get` to install these dependencies.

## Step 2: Configuring Permissions
For Android, add the following permissions in **AndroidManifest.xml**:

```xml
<uses-permission android:name="android.permission.CAMERA" />
<uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" />
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
```

For iOS, add these in **Info.plist**:

```xml
<key>NSCameraUsageDescription</key>
<string>App needs access to the camera</string>
<key>NSPhotoLibraryUsageDescription</key>
<string>App needs access to the photo library</string>
```

## Step 3: Implementing Image Picker
Create a Flutter widget that allows users to pick an image from the gallery or camera.

```dart
import 'package:flutter/material.dart';
import 'package:image_picker/image_picker.dart';
import 'dart:io';

class ImagePickerScreen extends StatefulWidget {
  @override
  _ImagePickerScreenState createState() => _ImagePickerScreenState();
}

class _ImagePickerScreenState extends State<ImagePickerScreen> {
  File? _image;
  final ImagePicker _picker = ImagePicker();

  // Function to pick image from gallery
  Future<void> _pickImageFromGallery() async {
    final pickedFile = await _picker.pickImage(source: ImageSource.gallery);
    if (pickedFile != null) {
      setState(() {
        _image = File(pickedFile.path);
      });
    }
  }

  // Function to capture image from camera
  Future<void> _pickImageFromCamera() async {
    final pickedFile = await _picker.pickImage(source: ImageSource.camera);
    if (pickedFile != null) {
      setState(() {
        _image = File(pickedFile.path);
      });
    }
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text("Image Picker Example")),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            _image != null ? Image.file(_image!) : Text("No image selected"),
            SizedBox(height: 20),
            ElevatedButton(
              onPressed: _pickImageFromGallery,
              child: Text("Pick from Gallery"),
            ),
            ElevatedButton(
              onPressed: _pickImageFromCamera,
              child: Text("Capture Image"),
            ),
          ],
        ),
      ),
    );
  }
}
```

## Step 4: Implementing Camera Preview
To capture and preview images, we use the `camera` package.

```dart
import 'package:flutter/material.dart';
import 'package:camera/camera.dart';

class CameraScreen extends StatefulWidget {
  @override
  _CameraScreenState createState() => _CameraScreenState();
}

class _CameraScreenState extends State<CameraScreen> {
  CameraController? _controller;
  List<CameraDescription>? cameras;

  @override
  void initState() {
    super.initState();
    _initializeCamera();
  }

  // Function to initialize the camera
  Future<void> _initializeCamera() async {
    cameras = await availableCameras();
    _controller = CameraController(cameras![0], ResolutionPreset.medium);
    await _controller!.initialize();
    setState(() {});
  }

  @override
  void dispose() {
    _controller?.dispose();
    super.dispose();
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text("Camera Preview")),
      body: _controller == null || !_controller!.value.isInitialized
          ? Center(child: CircularProgressIndicator())
          : CameraPreview(_controller!),
    );
  }
}
```

## Full Code Example
Here is the full working example of an app that picks images from the gallery or captures them using the camera.

```dart
import 'package:flutter/material.dart';
import 'package:image_picker/image_picker.dart';
import 'dart:io';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: ImagePickerScreen(),
    );
  }
}

class ImagePickerScreen extends StatefulWidget {
  @override
  _ImagePickerScreenState createState() => _ImagePickerScreenState();
}

class _ImagePickerScreenState extends State<ImagePickerScreen> {
  File? _image;
  final ImagePicker _picker = ImagePicker();

  Future<void> _pickImageFromGallery() async {
    final pickedFile = await _picker.pickImage(source: ImageSource.gallery);
    if (pickedFile != null) {
      setState(() {
        _image = File(pickedFile.path);
      });
    }
  }

  Future<void> _pickImageFromCamera() async {
    final pickedFile = await _picker.pickImage(source: ImageSource.camera);
    if (pickedFile != null) {
      setState(() {
        _image = File(pickedFile.path);
      });
    }
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text("Image Picker Example")),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            _image != null ? Image.file(_image!) : Text("No image selected"),
            SizedBox(height: 20),
            ElevatedButton(onPressed: _pickImageFromGallery, child: Text("Pick from Gallery")),
            ElevatedButton(onPressed: _pickImageFromCamera, child: Text("Capture Image")),
          ],
        ),
      ),
    );
  }
}
```

This guide covers everything from installing dependencies, configuring permissions, and implementing both **Image Picker** and **Camera Preview**. Happy coding!

