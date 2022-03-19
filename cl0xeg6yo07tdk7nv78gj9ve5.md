## Flutter Null Safety Operators and its uses. (Part 2)

# Introduction
In todays' article, we will see 3 null safety Flutter operators and their uses. This is part 2. In part 1, we saw the different null aware operators and their use cases. You can [read the first part here](https://cswithiyush.hashnode.dev/what-are-null-aware-operators-in-flutterdart-a-guide-on-different-types-of-null-aware-operators). So without wasting any time, let's get started

# ?
The ? mark operator is used to make any non-nullable data-type nullable. So if I write something like this

```
String x = null;
```
This will give me an error. But if I like it like this

```
String ? x = null;
```
This works fine! We use the  ? operator with the variables we are unsure about. 

# !
! operator is used for giving exceptions whenever we are accessing the value of a potentially null variable

```
String? x = null;
print(x);  // error
print(!x). // throws exception

String? y = 'data';
print(y) // error
print(!y) // prints data.
```

# late 
A late keyword tells the compiler that a particular variable is initialized later in time.

```
String y; // error
--------------------
late String y; // works fine
y = 'data';
```
# Conclusion
So this concludes a short and concise article on some more null safety operators. I hope you learned something new today. These are small things in Dart and Flutter that beginners ignore but this can really save you from some very bad and frustrating null-check errors.

You can appreciate and support my blogs via.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1646372265341/O0KkM6E-0.png)

Also, let's connect on [Twitter](https://twitter.com/Iyush004). Follow CSwithIyush for more amazing tutorials, tips/tricks on Flutter & DSA.

