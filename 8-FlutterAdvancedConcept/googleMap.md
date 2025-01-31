# Location & Maps Integration in Flutter (Google Maps)

## Introduction
This guide will help beginner Flutter developers integrate Google Maps into their Flutter applications. We will cover setting up Google Maps, displaying maps, getting the user's current location, and adding markers.

## Step 1: Add Dependencies
To integrate Google Maps in Flutter, add the following dependencies to your `pubspec.yaml` file:

```yaml
dependencies:
  flutter:
    sdk: flutter
  google_maps_flutter: latest_version
  geolocator: latest_version
  geocoding: latest_version
```

Run:
```sh
flutter pub get
```
This installs the required packages.

## Step 2: Configure Google Maps API Key
1. Visit [Google Cloud Console](https://console.cloud.google.com/)
2. Enable **Google Maps SDK for Android and iOS**
3. Create an API Key and add it to your Flutter project.

For Android, update `android/app/src/main/AndroidManifest.xml`:
```xml
<manifest>
    <application>
        <meta-data
            android:name="com.google.android.geo.API_KEY"
            android:value="YOUR_API_KEY_HERE"/>
    </application>
</manifest>
```

For iOS, update `ios/Runner/AppDelegate.swift`:
```swift
import GoogleMaps
GMSServices.provideAPIKey("YOUR_API_KEY_HERE")
```

## Step 3: Display Google Maps
Create a new Flutter widget for the map:

```dart
import 'package:flutter/material.dart';
import 'package:google_maps_flutter/google_maps_flutter.dart';

class MapScreen extends StatefulWidget {
  @override
  _MapScreenState createState() => _MapScreenState();
}

class _MapScreenState extends State<MapScreen> {
  GoogleMapController? _controller;
  static const CameraPosition _initialPosition = CameraPosition(
    target: LatLng(37.7749, -122.4194), // Default location (San Francisco)
    zoom: 10,
  );

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text("Google Maps in Flutter")),
      body: GoogleMap(
        initialCameraPosition: _initialPosition,
        onMapCreated: (GoogleMapController controller) {
          _controller = controller;
        },
      ),
    );
  }
}
```

## Step 4: Get User's Current Location
Modify `MapScreen` to fetch and display the user's location:

```dart
import 'package:flutter/material.dart';
import 'package:google_maps_flutter/google_maps_flutter.dart';
import 'package:geolocator/geolocator.dart';

class MapScreen extends StatefulWidget {
  @override
  _MapScreenState createState() => _MapScreenState();
}

class _MapScreenState extends State<MapScreen> {
  GoogleMapController? _controller;
  LatLng _currentPosition = LatLng(37.7749, -122.4194);

  @override
  void initState() {
    super.initState();
    _getCurrentLocation();
  }

  void _getCurrentLocation() async {
    Position position = await Geolocator.getCurrentPosition(
      desiredAccuracy: LocationAccuracy.high,
    );
    setState(() {
      _currentPosition = LatLng(position.latitude, position.longitude);
    });
    _controller?.animateCamera(CameraUpdate.newLatLng(_currentPosition));
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text("Google Maps in Flutter")),
      body: GoogleMap(
        initialCameraPosition: CameraPosition(
          target: _currentPosition,
          zoom: 15,
        ),
        onMapCreated: (controller) {
          _controller = controller;
        },
        myLocationEnabled: true,
      ),
    );
  }
}
```

## Step 5: Full Code Example with Comments

```dart
import 'package:flutter/material.dart';
import 'package:google_maps_flutter/google_maps_flutter.dart';
import 'package:geolocator/geolocator.dart';

// Main entry point of the application
void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: MapScreen(),
    );
  }
}

class MapScreen extends StatefulWidget {
  @override
  _MapScreenState createState() => _MapScreenState();
}

class _MapScreenState extends State<MapScreen> {
  GoogleMapController? _controller; // Google Map Controller
  LatLng _currentPosition = LatLng(37.7749, -122.4194); // Default Location

  @override
  void initState() {
    super.initState();
    _getCurrentLocation(); // Get the user location when screen loads
  }

  void _getCurrentLocation() async {
    Position position = await Geolocator.getCurrentPosition(
      desiredAccuracy: LocationAccuracy.high,
    );
    setState(() {
      _currentPosition = LatLng(position.latitude, position.longitude);
    });
    _controller?.animateCamera(CameraUpdate.newLatLng(_currentPosition));
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text("Google Maps in Flutter")),
      body: GoogleMap(
        initialCameraPosition: CameraPosition(
          target: _currentPosition,
          zoom: 15,
        ),
        onMapCreated: (controller) {
          _controller = controller;
        },
        myLocationEnabled: true,
      ),
    );
  }
}
```
This study material provides an easy-to-follow guide for Flutter beginners to integrate Google Maps into their apps with fully commented code. 
