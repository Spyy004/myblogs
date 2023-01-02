# 5 Awesome Flutter packages you must use in your next Flutter project

## Introduction

First of all, Happy new year to everyone out there! Today, we will have a look at 5 amazing Flutter packages that can be integrated with any Flutter project. If you already know about these packages, great! If not, then stick around and find out more about them.

So without wasting any time, let's get started.

## Package 1

The first package on our list is called permisson\_handler. On most operating systems, permissions aren't just granted to apps at install time. Rather, developers have to ask the user for permission while the app is running.

This plugin provides a cross-platform (iOS, Android) API to request permissions and check their status. You can also open the device's app settings so users can grant permission.

Here is a small snippet of how the code looks like

```dart
var status = await Permission.camera.status;
if (status.isDenied) {
  // We didn't ask for permission yet or the permission has been denied before but not permanently.
}

// You can can also directly ask the permission about its status.
if (await Permission.location.isRestricted) {
  // The OS restricts access, for example because of parental controls.
}
```

To know more about the package, follow [this link.](https://pub.dev/packages/permission_handler)

## Package 2

The second package is called share\_plus. It is a very useful package that can be used to share images, links, text, and files from your Flutter app. It is a very useful package because a lot of apps need sharing functionalities. The usage is pretty simple too, just import the package and use it.

```dart
Share.share('check out my website https://example.com', subject: 'Look what I made!');

// to share files

Share.shareFiles(['${directory.path}/image.jpg'], text: 'Great picture');
Share.shareFiles(['${directory.path}/image1.jpg', '${directory.path}/image2.jpg']);
```

To know more about this package, head to [this link](https://pub.dev/packages/share_plus) .

## Package 3

This is a very useful package that I believe you can use in any of your Flutter projects. It is called auto-size text. It is a widget that automatically resizes text to fit perfectly within its bounds.

The widget is exactly like a text widget but in the background, it knows how to auto-size it. Here is an example of the code

```dart
AutoSizeText(
  'A really long String',
  style: TextStyle(fontSize: 30),
  maxLines: 2,
)
```

To know more about this package, check out [this link](https://pub.dev/packages/auto_size_text)

## Package 4

This plugin is a must-have if your app heavily relies on having a good internet connection. This package is called connectivity plus. This plugin allows Flutter apps to discover network connectivity and configure themselves accordingly. It can distinguish between cellular vs WiFi connection.

If you think, you can make a lot of cool utility apps using this and the geolocator package together.

```dart
import 'package:connectivity_plus/connectivity_plus.dart';

var connectivityResult = await (Connectivity().checkConnectivity());
if (connectivityResult == ConnectivityResult.mobile) {
  // I am connected to a mobile network.
} else if (connectivityResult == ConnectivityResult.wifi) {
  // I am connected to a wifi network.
}
```

To know more, check out [this link](https://pub.dev/packages/connectivity_plus)

## Package 5

The last package is a very handy package if you want your app to have multiple language support. I am talking about the intl package. intl provides internationalization and localization facilities, including message translation, plurals and genders, date/number formatting and parsing, and bidirectional text.

The package has a single current locale, called [defaultLocale](https://pub.dev/documentation/intl/latest/intl/Intl/defaultLocale.html). Operations will use that locale unless told to do otherwise. This package has a lot of features. It can be covered in an article of its own.

If you want to get an in-depth idea about this package, head on to [this link](https://pub.dev/packages/intl)

## Conclusion

So this was it for today. There are 1000s of great flutter packages. These 5 are more of a regular utility hence I thought of sharing this with everyone. I hope that you learned something fun today

You can appreciate and support my blogs via.

![https://cdn.hashnode.com/res/hashnode/image/upload/v1646372265341/O0KkM6E-0.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1646372265341/O0KkM6E-0.png align="left")

Also, let's connect on [Twitter](https://twitter.com/Iyush004). Follow CSwithIyush for more amazing tutorials, tips/tricks on Flutter & DSA.