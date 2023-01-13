# Effortlessly Manage State in Flutter with Riverpod: A Beginner's Guide.

## Introduction

In this tutorial, we will learn how to use Riverpod in a Flutter app to manage the application's state. Riverpod is a state management library for Flutter based on the concept of providers. It uses the Provider pattern, which is similar to the Dependency Injection pattern, to manage the state of an application. The library is designed to be simple yet powerful and compatible with both Dart 2 and 3.

If you want to know more about the Provider pattern, you can check out this [article](https://cswithiyush.hashnode.dev/exploring-state-management-in-flutter-with-provider)

## Project Setup

Add the `riverpod` package as a dependency in your `pubspec.yaml` file.

```dart
dependencies:
  riverpod: ^2.1.3
```

Import the package wherever you need it.

```dart
import 'package:riverpod/riverpod.dart';
```

## Coding the Logic.

Once again, we will use our good old friend, "The counter app" to understand riverpod in a very simple manner. Here is a step-by-step guide to state management using riverpod.

* Create a `Provider` for the state you want to manage. A `Provider` is a piece of state that can be read and updated by any part of your app.
    
    ```dart
    final counterProvider = StateProvider<int>((ref) => 0);
    ```
    
* Add this line of code is used to read the current value of the `counterProvider` and make it available for use in the `ref` function of the `ConsumerWidget`.
    
    ```dart
    final counter = ref.watch(counterProvider);
    ```
    
* Use the `ConsumerWidget` widget to rebuild a part of your UI when the state changes. `ConsumerWidget` takes a `WidgetRef` function as arguments. `ConsumerWidget` is a good replacement `StatelessWidget` and gives us a convenient way of accessing providers with minimal code.
    
* `WidgetRef` allows us to gain access to any provider within our codebase, provided that we have imported the corresponding file. This is a feature of `Riverpod` as all the providers in it are designed to be global and accessible from anywhere in the codebase.
    
    ```dart
    class MyHomePage extends ConsumerWidget {
      @override
      Widget build(BuildContext context, WidgetRef ref) {
         final counter = ref.watch(counterProvider);
      }
    }
    ```
    

Update the state using the `Provider.of` method and calling `.read` and `.write`

```dart
context.read(counterProvider.notifier).state++;
```

This line is where all the magic is happening.

*The line* [`context.read`](http://context.read)`(counterProvider).state++;` *is used to update the state of the* `counterProvider`*. The* [`context.read`](http://context.read)`(counterProvider)` *is used to read the current value of the provider. The* `.state` *property is used to access the current value of the state, in this case, the current value of the counter. The* `++` *operator is used to increment the current value of the counter by 1.*

1. Make sure you wrap your Material app with ProviderScope widget.
    

If you add up everything, this is how your code will look like,

```dart
import 'package:flutter/material.dart';
import 'package:flutter_riverpod/flutter_riverpod.dart';

void main() {
  runApp( MyApp());
}

final counterProvider = StateProvider<int>((ref) => 0);

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return ProviderScope(
      child: MaterialApp(
        home: MyHomePage(),
      ),
    );
  }
}

class MyHomePage extends ConsumerWidget {
  @override
  Widget build(BuildContext context, WidgetRef ref) {
    final counter = ref.watch(counterProvider);
    return Scaffold(
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: <Widget>[
            Text(
              'You have pushed the button this many times:',
            ),
        Text(
          '$counter',
          style: Theme.of(context).textTheme.headline4,
        ),
            TextButton(onPressed: (){
              ref.read(counterProvider.notifier).state++;
            }, child: Text("Increment"))
          ],
        ),
      ),
    );
  }
}
```

I have coded everything in a single file just for the sake of your understanding but it is advised to keep your folder structure well-maintained. If we had to create a folder structure for this project, this is how it would be like

```yaml
lib/
  main.dart
  my_home_page.dart
  providers.dart
```

* `main.dart` the entry point of your app, it creates `MaterialApp` and wraps it with them `ProviderScope` to make the providers available to the entire app.
    
* `my_home_page.dart` is where you define the `MyHomePage` class and its build method, this class displays the UI of your home page and uses the `Consumer` widget to rebuild the text displaying the counter and the button that updates the counter.
    
* `providers.dart` is where you define all your providers, in this example, we have only one provider `counterProvider` but in a real-world app, you will have many more.
    

## Building with Riverpod 2.0 way.

Well, recently we got Riverpod 2.0 where we were introduced to Notifier and async Notifier. We will now see how we can build the same counter app, but with Notifier.

`StateProvider` is ideal for managing and updating simple variables such as the counter-example shown above. However, if your state requires validation logic or you need to manage more complex objects, `StateProvider` may not be the best fit. In such cases, `StateNotifier` can be a good alternative. The new `Notifier` class is now recommended for more advanced scenarios.

So our `counterProvider` will change into this

```dart
final counterProvider = NotifierProvider<Counter, int>(() {
  return Counter();
});
```

And this is how we will build our Counter class

```dart
import 'package:flutter_riverpod/flutter_riverpod.dart';

class Counter extends Notifier<int> {
  @override
  int build() {
    return 0;
  }

  void increment() {
    state++;
  }
}
```

It turns out that the `counterProvider` can be used in the `CounterWidget` without any modification, provided that the `counter.dart` file is imported.

```dart
class MyHomePage extends ConsumerWidget {
  @override
  Widget build(BuildContext context, WidgetRef ref) {
    final counter = ref.watch(counterProvider);
    return Scaffold(
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: <Widget>[
            Text(
              'You have pushed the button this many times:',
            ),
        Text(
          '$counter',
          style: Theme.of(context).textTheme.headline4,
        ),
            TextButton(onPressed: (){
              ref.read(counterProvider.notifier).increment(); // the change
            }, child: Text("Increment"))
          ],
        ),
      ),
    );
  }
}
```

## StateProvider vs Notifier

For storing a simple state, `StateProvider` remains the most straightforward option. `Notifier` is more detailed but also more adaptable, as it allows us to include methods with intricate logic in our `Notifier` subclasses (similar to what we do with `StateNotifier`).

## ref.read() v s ref.watch()

In the examples provided, two methods for reading providers were demonstrated: [`ref.read`](http://ref.read) and [`ref.watch`](http://ref.watch). When retrieving the value of a provider within a `build` method, [`ref.watch`](http://ref.watch) should always be used. This guarantees that if the value of the provider changes, the widgets that rely on it will be rebuilt accordingly.

Remember this:

* To keep an eye on a provider's state within the `build` method and rebuild a widget when it changes, use the [`ref.watch`](http://ref.watch)`(provider)` method.
    
* To read a provider's state only once in `initState` or other lifecycle methods, use the [`ref.read`](http://ref.read)`(provider)` method.
    

## Additional Features

Riverpod is a powerful state management library and it provides many more features that can be used to manage the state of your app. Some of the other features include:

* `ChangeNotifierProvider` which allows you to use `ChangeNotifier` to notify the listeners when the state changes. (similar to the Provider package).
    
* `FutureProvider` and `StreamProvider` which allows you to handle asynchronous state and automatically updates the listeners when the state changes.
    
* `AutoDisposeProvider` which automatically disposes of the provider when the widget is removed from the tree.
    
* `ProviderContainer` which allows you to create a custom container for your providers and makes it easy to test your providers.
    

With these features, Riverpod can handle any kind of state management needs that your app might have. It's also important to note that Riverpod can be used with other state management solutions like `BLoC` or `ScopedModel` and can work well with other packages like `get_it` for dependency injection.

## Conclusion

So with this, we conclude our tutorial for state management in Flutter with Riverpod. Mind you, this was a beginner's guide, if you want to get more knowledge, get your hands dirty by building a real-world project with Riverpod. Learning by doing is the best way, isn't it?

You can appreciate and support my blogs via.

![https://cdn.hashnode.com/res/hashnode/image/upload/v1646372265341/O0KkM6E-0.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1646372265341/O0KkM6E-0.png align="left")

Also, let's connect on [Twitter](https://twitter.com/Iyush004). Follow CSwithIyush for more amazing tutorials, tips/tricks on Flutter & DSA.