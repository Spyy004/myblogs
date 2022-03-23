## How to disable Screen Recording and Screenshots in Flutter apps

# Introduction 📕
Privacy is one of the biggest concerns for a user while using any app. If you are building an app where you want the users to feel safe and secure then one of the first steps to make your app more rigorous is to prevent Screen recording and taking screenshots. 

In today's article, we will learn how you cannot allow users from taking screenshots and record in your app. So without wasting any time, let's get started.
![LooneyToonsBugsBunnyGIF.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1647950077831/49MFpMg69.gif)

# Project Setup 🔨
We are going to use the flutter_windowmanager package to create this feature. First of all, let's add the package to our pubspec.

```
dependencies:
  flutter:
    sdk: flutter

  # The following adds the Cupertino Icons font to your application.
  # Use the CupertinoIcons class for iOS style icons.
  cupertino_icons: ^1.0.2
  flutter_windowmanager: // add this line of code.

```

Run the pub get command and then import this package in your main file.

```
import 'package:flutter_windowmanager/flutter_windowmanager.dart';
```

# Coding the Logic 🧑🏻‍💻
We are done with our setup so now let's move on to coding the logic. It is going to be very easy. First of all, we will create a boolean which tells us if taking screenshots is allowed or not, next up we will need a function that is triggered when a button is pressed. 

The button's function is to toggle between allowing the permissions and disallowing them.

Here is the code for the variable and the function.

```
bool isAllowed = false;
 void togglePermission(){
// if screenshot and recording are allowed, disable it.
 if (isAllowed == true) {
 // this flag blocks screenshot taking and screen recording feature.
  FlutterWindowManager.addFlags(FlutterWindowManager.FLAG_SECURE);
  isAllowed=false;
}
// if screenshot and recording are not allowed, enable it.
else
{
// remove the flag that we added in the if block.
   FlutterWindowManager.clearFlags(FlutterWindowManager.FLAG_SECURE);
   isAllowed=true;
 }
}
```
Now, let's quickly create a TextButton and call this function from there

```
TextButton(
 onPressed: () {
 togglePermission();
},
 child: Text("Change Settings"),
),
```
Well, that is pretty much everything you need to do. It was so short and easy, wasn't it? You can try recording the screen in your app. If the isAllowed variable is true, you will see a screen recording of your app but if the isAllowed variable is false, you will see the screen is being recorded but when you play it, there will be a dark screen.

# Conclusion 👋🏻
So with this, we conclude our article on preventing screenshot and screen recording features in your Flutter app. I hope you learned something new today.

You can appreciate and support my blogs via.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1646372265341/O0KkM6E-0.png)

Also, let's connect on [Twitter](https://twitter.com/Iyush004). Follow CSwithIyush for more amazing tutorials, tips/tricks on Flutter & DSA.
