# Implementing Biometric Authentication in a Flutter App

## Introduction ✌🏻

A lot of apps today have biometric authentication to authenticate the user. Have you ever wondered how they implement this feature? If yes, then today in this tutorial, I will show you how simple it is to add this feature to your app.

No time to waste, let's get started!

![5 steps to implement Biometric authentication in Android | by Anitaa Murthy  | ProAndroidDev](https://miro.medium.com/max/1200/1*3t7vK1kRG8H4GdBzXk7Lzg.jpeg align="left")

## Project Setup 💻

First of all, we will add the package local\_auth to our project. Add this line of code in pubspec.yaml file and run the command "pub get".

```dart
dependencies:
  local_auth: ^2.1.3
```

After this, we will need to edit the Androidmanifest.xml file. Since we are using biometrics, we are trying to access other features of our mobile device so we need permission for that. Add this line of code to the Andoirmanifest.xml file. You can find this file in android &gt; app &gt; src &gt; main.

```dart
<uses-permission android:name="android.permission.USE_BIOMETRIC"/>
```

We will also need to edit the MainActivity.kt file. Go to your `android > app > src > main > kotlin` and open the `MainActivity.kt` file and change it to the code below:

```dart
import io.flutter.embedding.android.FlutterFragmentActivity
class MainActivity: FlutterFragmentActivity() {
}
```

That's it. Our project is now configured to handle biometric authentications. Let's jump on to the coding part.

## Coding the Logic ⚒️

We will create a screen with a button that initiates the biometric authentication process. On successful authentication, you will be shown some text and on an unsuccessful authentication, you will be shown some other text.

To begin with, we will first import the package in main.dart or whichever dart file you are coding your logic in.

```dart
import 'package:local_auth/local_auth.dart';
```

Next, create a simple Elevated Button or Text Button and in the onPressed attribute of the button, add this piece of code.

```dart
onPressed: () async {
            dynamic isAuthenticated = await authenticate(); // main focus.
            if (isAuthenticated == true) {
              Navigator.push(
                context,
                MaterialPageRoute(
                  builder: (context) {
                    return const Page1();
                  },
                ),
              );
            } else {
               Navigator.push(
                context,
                MaterialPageRoute(
                  builder: (context) {
                    return const Page2();
                  },
                ),
              );
            }
          },
```

The if-else part is just random. You can do whatever you want in that. I am just showing two different pages depending on the result of the biometric scan. Our main focus should be on the authenticate function.

Let's look at how we will implement the authenticate function.

```dart
Future<dynamic> authenticate() async {
      LocalAuthentication auth = LocalAuthentication(); // creating an instance
      final bool isBiometricsAvailable = await auth.isDeviceSupported(); // checking if device supports biometric
      if (!isBiometricsAvailable) return false;
      try {
        return await auth.authenticate(
          localizedReason: 'Scan Fingerprint To Enter Vault',
          options: const AuthenticationOptions(
            useErrorDialogs: true,
            stickyAuth: true,
          ),
        );
      } on PlatformException catch (e) {
        return e.code;
      }
    }
```

Here is what's happening in the function.

* We check if the device is capable of providing biometric auth functionalities
    
* If no, we end the function and return false.
    
* If yes, we authenticate the user and wait for the result. Once got it, we return it.
    
* If there is any platform exception error, we return the error message.
    

You can see there is an attribute called options. It takes an instance of AutenticationOptions() and we can pass various parameters into it. To know more about it, I suggest you read their docs.

This package offers a wide range of customization options, making it easy to tailor to your specific needs.

## Conclusion 👋🏻

So that's it for today. We have learned how we can use a package called local\_auth to create a biometric authentication feature in our Flutter app. I hope that you learned something new today.

You can appreciate and support my blogs via.

![https://cdn.hashnode.com/res/hashnode/image/upload/v1646372265341/O0KkM6E-0.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1646372265341/O0KkM6E-0.png align="left")

Also, let's connect on [Twitter](https://twitter.com/Iyush004). Follow CSwithIyush for more amazing tutorials, tips/tricks on Flutter & DSA.