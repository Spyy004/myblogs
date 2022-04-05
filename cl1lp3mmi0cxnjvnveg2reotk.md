## 10 most common questions in a Flutter interview

# Introduction
There is a lot of theory in dart and Flutter and you need to know some of it along with practical experience. It is important to know why and what is behind things. So in today's article, I am going to write about the 10 most common interview questions asked in a Flutter interview

## What is Tween?
Tween is the short form of in-between. In the tween animation, it is required to define the start and endpoint of animation. It means the animation begins with the start value, then goes through a series of intermediate values, and finally reached the end value. 

The Tweener class includes the timeline and curve that can define the time and speed of transition. The animation between two points can be done with an in-between, which could be blended by using interpolation, and/or function curves.

## Difference between Stateful & Stateless widgets
Stateful widgets in Flutter are widgets that could change the data. For instance, the state of a slider can be changed by the user through manipulations on the device. The state can also be changed due to altering the tab bar position or showing off a different screen when it's triggered by an action. 

The stateless widget, on the other hand, is a widget without any data changes. The major examples of the stateless widget are Text, Row, Column, Container, etc. This widget does not have any lifecycle-related functions such as _didChangeDirection or _willChangeTheme. It should not have any function that alters the method on its callback.

## What is async & await?
Async and Await keywords are used to provide a declarative way to define the asynchronous function and use their results. The async keyword is used when we want to declare a function as asynchronous and the await keyword is used only on asynchronous functions.

## Difference between runApp and void main()
main(): This function starts the program. Flutter does not allow us to write any program without the main() function.  

runApp(): Using runApp(), you are able to return the widgets that are connected to the screen as a root of the widget tree that will be rendered on the screen. This function is called the main function, which is the driver of the app

## What is a Stream?
A stream is a sequence of asynchronous events. It provides an asynchronous sequence of data. It is the same as a pipe where we put some value on one end, and if we have a listener on the other end, it will receive that value. We can keep multiple listeners in a stream, and all of those will receive the same value when put in the pipeline.

## What are different build modes in Flutter?
The Flutter tooling supports three modes while compiling the application. These compilation modes can be chosen depending on where we are in the development cycle. The name of the modes are:

- Debug
- Profile
- Release

## What are keys in Flutter, and when to use it?
Keys are used in Flutter as identifiers for widgets, elements, and semantic nodes. The state of the modified widgets is preserved by a key.

Keys are used in both Flutter and Dart to accomplish a variety of feats. Essentially, keys are identifiers for widgets, elements, and semantic nodes. Using a key as a unique identifier ensures that only one widget will receive a given command from the Dart code. Global keys, rather than unique per instance like LocalKeys, provide stability in Flutter and Dart code when referencing instances of parts of a widget tree.

## What is BuildContext?
The BuildContext is a required parameter for most widgets in material design. It contains a function that we can use to get a reference to the parent widget and avoid nestings just for one reference of another widget. 

For example, if we want to use a material design button, the first thing we do is make it inherit the MaterialApp class, and then get the reference to the Scaffold using Scaffold.of(context). It helps us avoid adding an extra variable just for this kind of operation.

## What is the use of Mixins?
Dart does not support multiple inheritances. Thus to implement the multiple inheritances in Flutter/Dart, we need mixins. Mixins provide a way to write the reusable class's code in multiple class hierarchies.

## What is unit testing?
Unit Tests: It tests a single function, method, or class. Its goal is to ensure the correctness of code under a variety of conditions. This testing is used for checking the validity of our business logic.

# Conclusion
With this, we conclude our article on the 10 most common interview questions in a Flutter interview. I hope that you learned something new today from these questions.

You can appreciate and support my blogs via.

![https://cdn.hashnode.com/res/hashnode/image/upload/v1646372265341/O0KkM6E-0.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1646372265341/O0KkM6E-0.png)

Also, let's connect on [Twitter](https://twitter.com/Iyush004). Follow CSwithIyush for more amazing tutorials, tips/tricks on Flutter & DSA.