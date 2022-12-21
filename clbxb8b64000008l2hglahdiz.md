# How to integrate location services in Flutter.

## Introduction ✌🏻

Location services are an integral part of a lot of mobile apps today. It helps developers give every user a more personalized and customized experience. We can easily integrate location services in our Flutter app.

There are two types of location access: one is fetching the location once and not updating it until the user wants and the other is real-time location fetching. We will see how we can achieve both functionalities.

## Project Setup 💻

First, let's import the geolocator package and set them up in our pubspec file.

```dart
dependencies:
  geolocator: ^9.0.2
```

Rub pub get and let Flutter import the dependency for you.

## Code Example (Single time location fetch) ⚒️

All we need is a function called as getCurrentLocation which will have all the business logic of location fetching.

First, we will check if the location service is enabled or not. If no, then we will prompt the user to enable the location services. You can use a snackbar or a toast to display that message. Here is the code snippet for the same.

```dart
Future<Position> _determinePosition() async {
  bool serviceEnabled;
  LocationPermission permission;

  // Test if location services are enabled.
  serviceEnabled = await Geolocator.isLocationServiceEnabled();
  if (!serviceEnabled) {
    // Location services are not enabled don't continue
    // accessing the position and request users of the 
    // App to enable the location services.
    return Future.error('Location services are disabled. Please enable it');
      }
  }
```

Next, if they enable the location services, we will ask for permission to access the current location. If we don't get permission, we won't be able to access the location and we will return the same via a string message. If the user grants permission, then we will fetch the location and return it. Here is the code example for the same.

```dart
Future<Position> _determinePosition() async {

   // write this logic after the code given above.

    permission = await Geolocator.checkPermission();
  if (permission == LocationPermission.denied) {
    permission = await Geolocator.requestPermission();
    if (permission == LocationPermission.denied) {
      // Permissions are denied, next time you could try
      // requesting permissions again (this is also where
      // Android's shouldShowRequestPermissionRationale 
      // returned true. According to Android guidelines
      // your App should show an explanatory UI now.
      return Future.error('Location permissions are denied');
    }
  }
  
  if (permission == LocationPermission.deniedForever) {
    // Permissions are denied forever, handle appropriately. 
    return Future.error(
      'Location permissions are permanently denied, we cannot request permissions.');
  } 

  // When we reach here, permissions are granted and we can
  // continue accessing the position of the device.
  return await Geolocator.getCurrentPosition();
  }
```

## Code Example (Realtime Location fetching) ⚒️

In order to fetch real-time location and keep on updating it, we will need to use streams. If you are not familiar with streams in flutter, [go check out this article.](https://cswithiyush.hashnode.dev/streams-vs-futures-in-flutter)

The code is pretty small, we just need to change our return type from Future&lt;Position&gt; to StreamSubscription&lt;Position&gt;. In our UI, we will need to wrap our whole widget tree in a stream builder so that we can display the data provided by the position stream.

Here is the code for the business logic of fetching location as a stream.

```dart
StreamSubscription<Position> getRealtimeLocation(){
final LocationSettings locationSettings = LocationSettings(
  accuracy: LocationAccuracy.high,
  distanceFilter: 100,
);
return Geolocator.getPositionStream(locationSettings: locationSettings).listen(
    (Position? position) {
        print(position == null ? 'Unknown' : '${position.latitude.toString()}, ${position.longitude.toString()}');
    });
}
```

You can wrap the above two functions in a class called LocationServices and use them anywhere throughout your project codebase. So the final code would look something like this.

```dart
class LocationServices{

Future<Position> _determinePosition() async {

   // write this logic after the code given above.

    permission = await Geolocator.checkPermission();
  if (permission == LocationPermission.denied) {
    permission = await Geolocator.requestPermission();
    if (permission == LocationPermission.denied) {
      // Permissions are denied, next time you could try
      // requesting permissions again (this is also where
      // Android's shouldShowRequestPermissionRationale 
      // returned true. According to Android guidelines
      // your App should show an explanatory UI now.
      return Future.error('Location permissions are denied');
    }
  }
  
  if (permission == LocationPermission.deniedForever) {
    // Permissions are denied forever, handle appropriately. 
    return Future.error(
      'Location permissions are permanently denied, we cannot request permissions.');
  } 

  // When we reach here, permissions are granted and we can
  // continue accessing the position of the device.
  return await Geolocator.getCurrentPosition();
  }

StreamSubscription<Position> getRealtimeLocation(){
final LocationSettings locationSettings = LocationSettings(
  accuracy: LocationAccuracy.high,
  distanceFilter: 100,
);
return Geolocator.getPositionStream(locationSettings: locationSettings).listen();
}

}
```

## Conclusion 👋🏻

Well, this concludes our article. Today, you have learned how to integrate location services in your flutter app. There are other features provided by the geolocator package as well, such as fetching the last known location and much more. You can check out the package at pub.dev for more information.

I hope that you learned something new today. You can appreciate and support my blogs via.

![https://cdn.hashnode.com/res/hashnode/image/upload/v1646372265341/O0KkM6E-0.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1646372265341/O0KkM6E-0.png?auto=compress,format&format=webp align="left")

Also, let's connect on [**Twitter**](https://twitter.com/Iyush004). Follow CSwithIyush for more amazing tutorials, tips/tricks on Flutter & DSA.