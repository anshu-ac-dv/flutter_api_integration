# API Integration in flutter.

>* Adding API in our application for real time data change and for live updates.
>* API is second main integration of our future flutter application.

## How to implement API in flutter application?

* STEP-1 : Add the "Http" Package.
    * Open your pubspec.yaml file.
    * Add http: ^1.1.0 (or the latest version) under dependencies.
    * Run flutter pub get in your terminal.

* STEP-2 : Create a Data Model.
    * When you get data from an API, it usually arrives as a JSON object. 
    * A "Model" is just a simple Dart class that converts that messy JSON into an object your app can easily understand.
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

* STEP-3 : Build the API Service
    * Create a dedicated file (e.g., api_service.dart) to keep your networking logic separate from your UI.
    ```dart
        import 'dart:convert';
        import 'package:http/http.dart' as http;
        import 'post_model.dart';
        
            class ApiService {
            Future<List<Post>> fetchPosts() async {
            final response = await http.get(Uri.parse('https://jsonplaceholder.typicode.com/posts'));
            
                if (response.statusCode == 200) {
                  List<dynamic> body = jsonDecode(response.body);
                  return body.map((json) => Post.fromJson(json)).toList();
                } else {
                  throw Exception('Failed to load posts');
                }
            }
        }
    ```

* STEP-4 : Display Data with FutureBuilder
    * Flutter provides a FutureBuilder widget that automatically handles the "Loading," "Success," and "Error" states of an API call.
```dart

```