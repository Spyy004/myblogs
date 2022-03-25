## Flutter 2.10 migration guide. How I migrated to Flutter 2.10

# Introduction
It has been a time since Flutter has launched the 2.10 version and I found quite a few difficulties while migrating my old project to Flutter 2.10. In this article, I will show you how to solve some common errors that you may face while migrating an old Flutter project.

So without wasting any time, let's get started.
![StartBugsBunnyGIF.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1648186162004/Gk9GxK55S.gif)

# My Problems & Solutions

## Issue 1
The first problem that I faced was the return Nullable type error. This piece of code was accepted in the previous versions of Flutter

```
// returns true if string is empty
bool? isEmpty(String text) {
  if (text.isEmpty) {
    return true;
  }
}
```
This won't work in Flutter 2.10. It will throw this error

```
This function has a nullable return type of 'String?', but ends without returning a value.
```
To overcome this, just add a return statement outside the if block

```
bool? isEmpty(String text) {
  if (text.isEmpty) {
    return true;
  }
return false;
}
```

## Issue 2
The second issue that I faced was a build issue. I was getting some errors related to compile SDK version. All you need to do is change the compile SDK version in android/app/build.gradle to 31.

Another problem that you will face is *android:name* in the application tag of AndroidManifest.xml. Earlier, the application tag used to look like this,

```
<application
        android:name="io.flutter.app.FlutterApplication"
        android:label="Example app"
        tools:replace="android:label"
        android:icon="@mipmap/ic_launcher">
```

Change the android:name attribute from "io.flutter.app.FlutterApplication" to 
"${applicationName}". 

## Issue 3
There are some packages that I used in my project which used some APIs that are depreciated in the SDK version 31.  I updated my packages to the latest version and that solved the issue. 

If you are using some packages that are not regularly updated and even after updating to the latest version gives you the deprecated error, then you will need to find a new package that does the same function.
![SpongebobSquarepantsGIF.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1648138319046/DFY8o4etD.gif)

# Conclusion
Well, there can be a lot more issues that you may face them migrating to Flutter 2.10. I can remember these 3 and I solved it using the power of StackOverflow and docs. If you didn't find the problem you are facing, then browse StackOverflow or search in Github issues. I am sure you will find an answer because you are not the only one to get stuck on that problem.

With this, we conclude today's article. We didn't learn anything new. It was just an article to share how I tackled some problems while migrating. If you found any issue mentioned above and were able to solve it then awesome!

You can appreciate and support my blogs via.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1646372265341/O0KkM6E-0.png)

Also, let's connect on [Twitter](https://twitter.com/Iyush004). Follow CSwithIyush for more amazing tutorials, tips/tricks on Flutter & DSA.