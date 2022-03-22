## Beginners Guide to Navigation and Routing in Flutter

# Introduction
In today's article, we will look at how navigation and routing between different pages work in Flutter. We will see two different routing types. Non-named and Named routing.  There are some advanced routing methods, but we will be looking only at the basics today.

So without wasting time, let's get started.
![LooneyToonsBugsBunnyGIF.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1647874167092/JOx0uG3rM.gif)

# Default Routing
The default routing method is where we use Navigator.push() command if we want to go to a new screen. A code example would be better I guess.

```
Navigator.push(context,
              MaterialPageRoute(builder: (context) => const SecondScreen()));
```
Navigator.push needs two parameters, the context, and the Route. The route parameter is a function that routes to the class mentioned in the material page route function. 

We can also pass data from one screen to another by adding parameters like this.

```
Navigator.push(context,
              MaterialPageRoute(builder: (context) => const SecondScreen(data: "From Screen 1")));
```
If we want to go back to the previous page, we use the Navigator.pop() method

```
Navigator.pop(context); 
```

This is a very simple way to navigate between screens but this doesn't work when you are building a little complex app. Here is the code sample for default routing.

```
import 'package:flutter/material.dart';

void main() {
  runApp(MaterialApp(
    home: HomePage(),
  ));
}

class HomePage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Home'),
      ),
      body: new Center(
        child: RaisedButton(
          onPressed: () {
            Route route = MaterialPageRoute(builder: (context) => SecondHome());
            Navigator.push(context, route);
          },
          child: Text('Second Home'),
        ),
      ),
    );
  }
}

class SecondHome extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Second Hoem'),
      ),
      body: new Center(
        child: RaisedButton(
          onPressed: () {
            Navigator.pop(context);
          },
          child: Text('Go Back'),
        ),
      ),
    );
  }
}
```

# Named Routing
Named Routing won't solve all your problems but it is better than the default routing. It is much more manageable, understandable and the code looks clean too. To add named routing, we need to add two parameters in your Material App widget. routes and initial routes. 

routes take a map that maps a string to a builder function. The initial route takes the string of the initial home page. You don't need to add a home attribute if you are using named routing. Here is how the code for the material app looks like

```
MaterialApp(
 routes: {
  '/': (context)=> const HomeScreen(),
  '/secondscreen': (context)=> const SecondScreen()
},
 initialRoute: '/',
);
```
Now in order to use these for navigating, we use Navigator.pushNamed() function.

```
Navigator.pushNamed(context, '/secondscreen');
```

This piece of code will take us to the second page from the first page. This looks much cleaner and easier to manage, understand. 

Going back to the previous screen is completely the same. We use Navigator.pop(). If suppose, there is a mismatch or typo then you can create an error route as well. This is how you do it.

```
 onUnknownRoute: (RouteSettings setting) {
    # To can ask the RouterSettings for unknown router name.
    String unknownRoute = setting.name ;
    return new MaterialPageRoute(
                builder: (context) => NotFoundPage()
    );
  }
```
Here is the complete code sample for Named Routing.

This piece of code is to be added in the MaterialApp. MaterialApp has an onUnknownRoute attribute.

```
import 'package:flutter/material.dart';

void main() {
  runApp(MaterialApp(
  initialRoute: '/',
  routes: <String, WidgetBuilder>{
      '/': (context) => HomePage(),
      '/secondscreen': (context) => SecondHome(),
    },
 onUnknownRoute: (RouteSettings setting) {
    # To can ask the RouterSettings for unknown router name.
    String unknownRoute = setting.name ;
    return new MaterialPageRoute(
                builder: (context) => NotFoundPage()
    );
  }
  ));
}

class HomePage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Home'),
      ),
      body: new Center(
        child: RaisedButton(
          onPressed: () {
            Navigator.pushNamed(context, '/second');
          },
          child: Text('Second Home'),
        ),
      ),
    );
  }
}

class SecondHome extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Second Home'),
      ),
      body: new Center(
        child: RaisedButton(
          onPressed: () {
            Navigator.pop(context);
          },
          child: Text('Go Back'),
        ),
      ),
    );
  }
}

class NotFoundPage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Error Screen'),
      ),
      body: new Center(
        child: RaisedButton(
          onPressed: () {
            Navigator.pop(context);
          },
          child: Text('Go Back'),
        ),
      ),
    );
  }
}
```

# Conclusion
With this, we conclude our article on the basic ways of navigation and routing in Flutter. This was a beginner-friendly article so I don't expect any intermediate or expert Flutter devs to learn anything from it. As for the newbies, I hope you learned something new today.

You can appreciate and support my blogs via.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1646372265341/O0KkM6E-0.png)

Also, let's connect on [Twitter](https://twitter.com/Iyush004). Follow CSwithIyush for more amazing tutorials, tips/tricks on Flutter & DSA.