# Choosing the Right Dart/Flutter Build Mode: JIT vs AOT Comparison

# Introduction ✌🏻

Dart is a popular language for developing applications and is used to build robust and scalable applications. In Dart, there are different types of build modes that developers can use to build their applications. In this blog post, we will discuss the different build modes and when to use them.

Before jumping into different build modes, let's understand two different types of compilation methods Dart uses to compile your code.

# Ahead-of-Time (AOT) vs Just-in-Time (JIT)

![How does dart VM work?. Hello Guys, today we are going to see… | by  Raahavajith | YavarTechWorks | Medium](https://miro.medium.com/max/1400/1*BFPOPyWC77Xn2TT1Dwxfgg.png align="left")

JIT (Just-In-Time) and AOT (Ahead-of-Time) compilation are two different approaches to compiling code in Dart.

In JIT mode, the code is compiled at runtime, when the application is executed. The advantage of JIT mode is that it allows for faster development and testing, as you can make changes to the code and see the results immediately.

In AOT mode, the code is compiled ahead of time, before the application is executed. The advantage of AOT mode is that the compiled code runs faster than JIT-compiled code, as it does not require the additional overhead of compiling the code at runtime. This makes AOT mode ideal for deploying your application to production, as it provides a smooth, fast, and reliable user experience.

## **Development/Debug Mode 🪲**

The development mode is the default build mode for Dart. When an application is built in development mode, Dart includes additional information in the generated code.

This additional information makes it easier for developers to debug and profile their applications. The Dart runtime also includes additional error checking to catch errors at runtime. This build mode is ideal for developers who are in the process of writing and testing their applications.

The "just" mode in Dart uses Ahead-of-Time (AOT) compilation.

## **Profile Mode ⚒️**

Profile mode is used for performance profiling and optimization. This build mode is similar to the development mode, but it includes more aggressive inlining and optimization.

The Dart runtime also includes additional performance profiling information. This build mode is ideal for developers who are looking to optimize the performance of their applications. The "profile" mode in Dart uses Ahead-of-Time (AOT) compilation.

## **Release Mode 🚀**

The release mode is used for building the final version of an application that will be deployed to end users. This build mode includes the most aggressive inlining and optimization, and the Dart runtime includes only the minimum amount of error checking necessary to catch critical errors.

The Dart runtime also does not include the additional performance profiling information included in the profile mode. This build mode is ideal for developers who are looking to release a high-performance, production-ready application. The "release" mode in Dart uses Ahead-of-Time (AOT) compilation.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1675260860585/826d8b88-8a5a-4f37-908e-3e44ad5df97d.gif align="center")

## **Conclusion 👋🏻**

In conclusion, Dart provides developers with different build modes to build their applications. The development mode is ideal for developers who are in the process of writing and testing their applications.

The profile mode is ideal for developers who are looking to optimize the performance of their applications. The release mode is ideal for developers who are looking to release a high-performance, production-ready application. It's important to choose the right build mode for your application based on your development needs and the stage of development.