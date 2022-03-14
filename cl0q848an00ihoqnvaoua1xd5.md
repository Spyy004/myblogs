## What are null-aware operators in Flutter/Dart? A guide on different types of null-aware operators.

# Introduction 📕
In today's article, we will look at all the different types of null-aware operators in Flutter. A null-aware operator is an important concept of Flutter because it can save you from random null-check errors.

There are 4 different null-aware operators. These null operators can easily confuse a beginner so if you are a beginner and want to know exactly what they are, then read this till the end.![CalculatingPuzzledGIF.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1647233087405/SgeMhfDk2.gif)

# ?.
The first operator is the **?.** operator. This operator is used when the value of a variable can potentially be null. If the variable is null, this operator will return a null value and if it is not null, it will return the value stored in it.

```
String ? myStr = "Flutter";
print(myStr?.length) // prints 5

String ? myStr = null;
print(myStr?.length) // prints null

String ? myStr = null;
print(myStr.length) // gives an error
```
# ??
The second operator is the **??** operator. This operator is used when we are accessing a value that can be null but we don't know about it. Have a look at the below examples.

```
void main() {
  String? s;
  print(s??'Is null'); // prints is null

 String? p = 'dummy';
 print(p??'Is null'); // prints dummy
}
```
# ??=
The third operator is just an extension to the second operator. It is the **??=** operator. This operator is used to assign values to the variables that can be null.
For example,

```
String? s;
s??='345';
print(s); // prints 345

String? s='123';
s??='345';
print(s);  // prints 123
```

# ...?
The fourth operator is **...?**. This is very useful when you are dealing with nullable lists. As you know, ... is the spread operator. The ...? checks if the list is null or not and does the operation accordingly. Here is an example of the same

```
void main() {
 List<int>? x1;  
 print([...x1,13]);   // this will give an error because we are not doing the null check

 List<int>? x2;
 print([...?x2,13]);   // prints [13]

 List<int>? x3=[10,12];
 print([...?x3,13]);   // prints [10,12,13]
}
```
In all the examples, we are using ? after declaring our variable because it means that this variable can be null. If we don't use the ? it becomes non-nullable by default.


# Conclusion 
With this, we conclude our article on different types of null-aware operators. I hope that you understood the differences and uses of all these operators. 

You can appreciate and support my blogs via.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1646372265341/O0KkM6E-0.png)

Also, let's connect on [Twitter](https://twitter.com/Iyush004). Follow CSwithIyush for more amazing tutorials, tips/tricks on Flutter & DSA.