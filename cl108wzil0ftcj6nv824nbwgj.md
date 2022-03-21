## How to add an app icon to your Flutter app? Beginners Guide

# Introduction
In todays' article, we will see how you can add an app icon to your Flutter app. Every app has its own unique icon and an app icon is one of the most important parts of an app. 

Earlier, adding an app icon was a time taking task because we had to generate app icons via an external website and then store it in a particular folder in your project directory but since the arrival of flutter_launcher_icons, everything has changed. 

How? let's find out.
![ultimate-app-icon-set-1.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1647766919207/CNYoQsgGA.jpg)

# Project Setup
So first of all we will add the flutter_launcher_icons package in pubspec under the dev_dependencies tag.

```
dev_dependencies:
  flutter_launcher_icons: "^0.9.2"
```

Now, add these lines of code in your pubspec

```
flutter_icons:
  android: "launcher_icon"
  ios: true
  image_path: "assets/icon/appicon.png"
```
This whole code block comes after the dev_dependencies part. So your code will look something like this

```
dev_dependencies:
  flutter_launcher_icons: "^0.9.2"
flutter_icons:
  android: "launcher_icon"  // name of your icon
  ios: true    // creates an ios icon as well if true
  image_path: "assets/icon/appicon.png" // path to the image
```
As you can see the image_path attribute needs a path to the image. For that, add an image first. Create a new assets folder then create an icon folder and add your image there. You can name it anything you want. Just make sure that name of the file and image_path attribute has the same name.

Whatever we did above in the pubspec file can also be done in a new YAML file. All you need to do is create a file called **flutter_launcher_icons.yaml** and add the above block of code to it. 

# Generating Icons
Now let's generate our icons. We do that by typing 4 simple commands. The first command is ***flutter pub get***. Once done with pub get, type this command in your terminal.

```
// config file will be pubspec.yaml or flutter_launcher_icons.yaml. 
flutter pub run flutter_launcher_icons:main -f <your config file name>
```
This will generate your icons. It will take some time. Once it is done again type ***flutter pub get***. Once pub get is done successfully, type this command in your terminal

```
flutter pub run flutter_launcher_icons:main
```
This will run your package and add the icon to your app. Once you are done with running all 4 commands successfully, build an APK of your flutter app and install it on your phone. You will successfully see the launcher icon of your app.

To build an APK version, type this command

```
flutter build apk
```


![1_ZBuVqp08BJuOvkEH7njkvQ.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1647766871757/YvS3WatD8.png)

# Common Errors
If you are getting some errors while running the build commands then try reading the troubleshooting part of [this page](https://pub.dev/packages/flutter_launcher_icons)

# Conclusion
If you were successful in generating app icons and seeing them then CONGRATULATIONS! You have learned how to add launch icons to your app in the easiest way. 

You can appreciate and support my blogs via.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1646372265341/O0KkM6E-0.png)

Also, let's connect on [Twitter](https://twitter.com/Iyush004). Follow CSwithIyush for more amazing tutorials, tips/tricks on Flutter & DSA.
