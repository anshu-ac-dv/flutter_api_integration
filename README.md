# API Integration in flutter.

>* Adding API in our application for real time data change and for live updates.
>* API is second main integration of our future flutter application.

## How to implement API in flutter application?

* Add the "Http" Package.
    * Open your pubspec.yaml file.
    * Add http: ^1.1.0 (or the latest version) under dependencies.
    * Run flutter pub get in your terminal.

* Create a Data Model.
    * When you get data from an API, it usually arrives as a JSON object. A "Model" is just a simple Dart class that converts that messy JSON into an object your app can easily understand.
```dart
    class User {
    final int id;
    final String name;
    
    User({required this.id, required this.name});
    
    // This converts JSON into a User object
    factory User.fromJson(Map<String, dynamic> json) {
    return User(
    id: json['id'],
    name: json['name'],
      );
    }
    }
```