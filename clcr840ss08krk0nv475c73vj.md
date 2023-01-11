# Understanding Object-Oriented Programming Concepts in Dart

## Introduction

Dart is a programming language developed by Google that is used for building web, mobile, and desktop apps. One of the key features of Dart is its support for object-oriented programming (OOP) concepts. Understanding OOP concepts is crucial for any developer looking to build robust and maintainable apps using Dart.

So without wasting any time, let's get started.

## What is Object-Oriented Programming?

Before getting into the concepts of OOP, let's understand what OOP is. OOP is a programming paradigm that is based on the concept of "objects" that have properties and methods. Objects are instances of a class, which define a blueprint for how the object should behave. Classes are used to create objects and objects interact with each other through methods.

In Dart, classes are the blueprint for creating objects, the basic syntax for a class is the following:

```dart
class MyClass {
  // properties
  // methods
}
```

## Encapsulation

Encapsulation is the practice of keeping an object's properties and methods private and only allowing them to be accessed through public methods. This helps to keep the object's internal state consistent and prevent external code from accidentally modifying it. In Dart, you can achieve encapsulation by using the '\_' symbol to make a property or method private, and then exposing it through a public method if necessary.

```dart
class MyClass {
  int _x; // private property
  void setX(int x) {
    _x = x;
  }
  int getX() {
    return _x;
  }
}
```

## Inheritance

Inheritance is the ability for one class to inherit the properties and methods of another class. This allows developers to create a parent class that contains common functionality and then create child classes that inherit that functionality. In Dart, you can use the 'extends' keyword to create a child class that inherits from a parent class.

```dart
class Person {
  String name;
  int age;

  Person(this.name, this.age);

  void display() {
    print("Name: $name, Age: $age");
  }
}

class Student extends Person {
  String major;
  String school;

  Student(String name, int age, this.major, this.school) : super(name, age);

  void display() {
    super.display();
    print("Major: $major, School: $school");
  }
}
```

In this example, the `Person` class is defined with properties `name` and `age` and a `display` method that prints the values of the properties. The `Student` class inherits the properties and methods of the `Person` class through the `extends` keyword. It also defines its own properties `major` and `school` and its own implementation of the `display` method that prints the values of the inherited properties and the additional properties.

By inheriting from the `Person` class, the `Student` class can reuse the code from the `Person` class, and we can avoid duplicating the same code.

The `Student` class can also override methods from the `Person` class by defining a new method with the same name. As you can see in the example, the `display()` method is overridden in the `Student` class. By using the `super.display()` we can call the superclass method inside the subclass.

The `: super(name, age)` is the constructor of the superclass, and it's called in the constructor of the subclass.

Inheritance allows for more code reuse, more flexibility, and more ease in the maintenance of your code. It also allows for a clear class hierarchy, making it easier to understand and navigate your codebase.

## Polymorphism

Polymorphism is the ability for different objects to respond to the same method call in different ways. This allows developers to create a single interface that can be used by multiple types of objects. In Dart, polymorphism is achieved through the use of interfaces and abstract classes.

```dart
abstract class Shape {
  double getArea();
}

class Circle extends Shape {
  double radius;
  double getArea() {
    return 3.14 * radius * radius;
  }
}

class Square extends Shape {
  double side;
  double getArea() {
    return side * side;
  }
}
```

In the above example, `Shape` is an abstract class with a single abstract method called `getArea`. The `Circle` and `Square` classes are concrete classes that extend the `Shape` class and implement the `getArea` method. Both classes have different properties and methods specific to their respective shapes but they can be treated as a `Shape` class since they both implement `getArea` method which was defined in the abstract class.

we can use these classes in a similar way by creating a list of `Shape` objects and adding different shapes to it:

```dart
List<Shape> shapes = [Circle(), Square()];
for(Shape shape in shapes) {
    print(shape.getArea());
}
```

In the above example, each element of the `shapes` list is of type `Shape`, but it could be an object of either the `Circle` or the `Square` class. The `for` loop uses the `getArea` method of each element, which is implemented differently in each class.

Polymorphism allows us to create a single interface that can be used by multiple types of objects, this gives more flexibility and modularity to our code as we can use it for different shapes by implementing the same method but with different implementation.

It's worth noting that polymorphism is not limited to classes and it can also be used with methods, functions, interfaces and other constructs.

## Conclusion

Object-oriented programming concepts are a fundamental part of the Dart language, and understanding how to use them effectively can help you to build robust and maintainable apps. Encapsulation, Inheritance, and Polymorphism are the key concepts that developers should be familiar with when working with Dart. These concepts can help to simplify the complexity of large-scale applications and make it easier to organize and manage your code. Remember that all of this is just a starting point, and as you start to explore and develop more with Dart, you will discover more details and usage that will help you to build better apps.

As with any programming language, it's important to practice and experiment with the concepts and features of Dart, and to keep learning from other developers and experts in the community.

I hope that you learned something new today. You can appreciate and support my blogs via.

![https://cdn.hashnode.com/res/hashnode/image/upload/v1646372265341/O0KkM6E-0.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1646372265341/O0KkM6E-0.png align="left")

Also, let's connect on [Twitter](https://twitter.com/Iyush004). Follow CSwithIyush for more amazing tutorials, tips/tricks on Flutter & DSA.