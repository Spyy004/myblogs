## How to add Glassmorphism effect in Flutter

# Introduction
In today's article, we will learn how to add a cool glassmorphism effect to your Flutter apps. Glassmorphism is a component that looks like glass. You can display images or text on it. It creates a blur effect above the background and looks awesome.  

So without wasting any time, let's get started.

# Project Setup
We will use the glassmorphism package to implement glassmorphism. Add it to your dependency and also import it into your dart file.

```
dependencies:
  glassmorphism: ^3.0.0
```

```
import 'package:glassmorphism/glassmorphism.dart';
```

# Coding the Logic
Well since this is a UI tutorial, there isn't much logic involved today. I will show you two widgets that are glassmorphized already. I will also attach the images of how they look on screen. Here is a container with a glassmorphism effect added to it

```
GlassmorphicContainer(
  width: 350,
  height: 350,
  borderRadius: 20,
  blur: 20,
  alignment: Alignment.bottomCenter,
  border: 2,
  linearGradient: LinearGradient(
      begin: Alignment.topLeft,
      end: Alignment.bottomRight,
      colors: [
        Color(0xFFffffff).withOpacity(0.1),
        Color(0xFFFFFFFF).withOpacity(0.05),
      ],
      stops: [
        0.1,
        1,
      ]),
  borderGradient: LinearGradient(
    begin: Alignment.topLeft,
    end: Alignment.bottomRight,
    colors: [
      Color(0xFFffffff).withOpacity(0.5),
      Color((0xFFFFFFFF)).withOpacity(0.5),
    ],
  ),
  child: Center(child:Text("Hey There")),
),
```

Here is the result.
![Screenshot (156).png](https://cdn.hashnode.com/res/hashnode/image/upload/v1648742294457/mYcJPDc0E.png)

# Conclusion
Well, this was it. This is how you can add a glassmorphism effect to your Flutter app. This was a very simple tutorial. 

You can appreciate and support my blogs via.

![https://cdn.hashnode.com/res/hashnode/image/upload/v1646372265341/O0KkM6E-0.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1646372265341/O0KkM6E-0.png)

Also, let's connect on [Twitter](https://twitter.com/Iyush004). Follow CSwithIyush for more amazing tutorials, tips/tricks on Flutter & DSA.