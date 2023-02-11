# Flutter 101: The "WhatWhyHow" of Google's Revolutionary Mobile App Framework

## Introduction

Welcome to the "WhatWhyHow" series of blogs! In this series, we explore various topics in the technology domain, providing concise yet informative answers to some of the most common questions about them.

In this blog, we will be discussing Flutter, a mobile application development framework created by Google. We will cover the basics of Flutter, why it's important for mobile app development, and how it works, including how the Flutter code compiles. So whether you're a beginner or an experienced developer, this blog will provide you with valuable insights into the world of mobile application development using Flutter. Let's get started!

## **What is Flutter?**

Flutter is a free and open-source mobile application development framework created by Google. It allows developers to build high-performance, visually attractive applications for Android, iOS, and other platforms, using a single codebase. Flutter uses the Dart programming language and provides a rich set of customizable widgets and tools for creating beautiful and responsive user interfaces.

## **Why do we need Flutter?**

We need Flutter because it provides several advantages for mobile application development, including:

1. Cross-platform development: Flutter allows developers to build applications that can run on multiple platforms, such as Android and iOS, using a single codebase.
    
2. Fast development: Flutter's hot reload feature allows developers to see the changes they make to the code immediately on the app, speeding up the development process.
    
3. Beautiful and customizable UI: Flutter provides a rich set of customizable widgets and tools for creating visually attractive and responsive user interfaces, making it easy to create beautiful and engaging apps.
    
4. High performance: Flutter's use of Dart language and the Flutter framework's architecture enable high performance and smooth animations, resulting in a great user experience.
    

Overall, Flutter simplifies the mobile application development process, allowing developers to build apps faster, with fewer bugs, and with better user experiences.

![Why Flutter is the most popular cross-platform mobile SDK - Stack Overflow  Blog](https://lh4.googleusercontent.com/75J3q22dKWHeYn2R4gddMfvnCWvrGLMqsWBtdtxQ1R1Ucu75lLYR_hWUCXHAJoikFQJE4AGiI68X16B829ZEQDocNSmfOqghbd3LEzk7pNxiaN_sWzDJtLeMJLzu5IZia0yR4Mir align="left")

## **How does Flutter work?**

Flutter uses a layered architecture to build mobile applications. The core of Flutter is a reactive framework composed of two main layers:

1. The Flutter Engine: This is a C++ rendering engine that provides low-level rendering capabilities to Flutter. It works with the host operating system to render graphics, provide access to platform APIs, and manage app lifecycle events.
    
2. The Flutter Framework: This is a collection of libraries and tools written in the Dart language that provides high-level APIs for building mobile applications. It provides a rich set of customizable widgets, tools for managing app state, and APIs for accessing device features such as camera, GPS, and sensors.
    

The Flutter framework also includes a hot reload feature, which allows developers to make changes to the code and see the results in the app immediately, without the need for a full rebuild.

When a Flutter app runs, the Flutter framework manages the app's state and builds a widget tree based on the app's configuration. The widget tree defines the app's user interface and is rendered by the Flutter engine, which uses low-level graphics APIs to draw the UI elements on the screen.

![dart - Flutter - How does it work behind the scenes? - Stack Overflow](https://i.stack.imgur.com/xJvY6.png align="left")

### **How does Flutter code compile?**

When you write code in Flutter using the Dart programming language, you can use a tool called the Flutter SDK to compile your code into a native application. Here's how the compilation process works:

1. Compilation to Bytecode: When you write Dart code in Flutter, the Dart compiler compiles your code into bytecode, which is a low-level representation of your code that can be executed by the Dart Virtual Machine (VM).
    
2. [Ahead-of-Time (AOT) Compilation:](https://cswithiyush.hashnode.dev/choosing-the-right-dartflutter-build-mode-jit-vs-aot-comparison) Flutter also supports AOT compilation, which compiles your Dart code into native machine code that can be executed directly by the operating system. AOT compilation produces faster startup times and lower memory usage compared to Just-in-Time (JIT) compilation, which is an alternative compilation method.
    
3. Building the Application Bundle: Once the Dart code is compiled into either bytecode or native machine code, the Flutter SDK packages the code along with any necessary assets and libraries into an application bundle.
    
4. Generating Native Code: The Flutter engine generates native code for the target platform, such as Android or iOS, which interacts with the operating system and provides access to device-specific features.
    
5. Deploying the Application: Finally, the compiled application bundle is deployed to the target device, where it can be installed and run.
    

Overall, Flutter's compilation process enables high-performance and efficient application development, allowing developers to create visually appealing and responsive mobile applications for multiple platforms.

## **Conclusion**

Flutter is a powerful framework that simplifies the development of high-performance and visually attractive mobile applications. Its use of Dart and layered architecture enables faster development, efficient compilation, and smoother animations. With Flutter, developers can build cross-platform apps with ease, offering an engaging user experience for their target audience.

You can appreciate and support my blogs via.

![https://cdn.hashnode.com/res/hashnode/image/upload/v1646372265341/O0KkM6E-0.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1646372265341/O0KkM6E-0.png align="left")

Also, let's connect on [Twitter](https://twitter.com/Iyush004). Follow CSwithIyush for more amazing tutorials, tips/tricks on Flutter & DSA.