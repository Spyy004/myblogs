## How to store secret keys and keep them out of Version Control in Flutter

# Introduction
In many projects, you use API keys from third-party APIs and when the time comes to push your project to GitHub, things start getting tricky. If you are a beginner, you may mistake pushing your code directly to GitHub. This will lead to your API keys being exposed in the open. You definitely don't want that to happen.

So how do we protect our API keys? Well, today we will discuss exactly the solution to this question.

# Step 1
First of all, we will create a new secret.dart file. Create a new folder auth under lib and inside auth, create secret.dart. 

# Step 2
In the secret.dart file, add your API key as a variable.

```
var secretKey = 'ce4167ujggtr5hhhh889ju3nnlik89';
```
Now, we will add this secret.dart file in our gitignore file. You can find the gitignore file in your root project directory itself. (only if you have already created a local repo using git).

```
#In your gitignore file, add the path to your secrets file below

/lib/auth/secret.dart
```
Now, if I want to use my API key anywhere in the code, I will import the secret.dart file and then use the variable by adding a $ in front of it. 

```
import 'secret.dart';

// some Flutter code.

$secretKey

// some Flutter code.
```
Now, if you push your code to Github, you will see that your secret key is nowhere in your repo on Github. This is because we added the secret file in gitignore. The contents of the gitignore file are not pushed to Github whenever you make changes and push your code.

# Conclusion
With this, we conclude today's article. I hope that you learned something new today. A lot of beginners make the mistake of revealing their API key in the open. Follow the practice that I have mentioned in this article and your API keys will be safe.

You can appreciate and support my blogs via.

![https://cdn.hashnode.com/res/hashnode/image/upload/v1646372265341/O0KkM6E-0.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1646372265341/O0KkM6E-0.png)

Also, let's connect on [Twitter](https://twitter.com/Iyush004). Follow CSwithIyush for more amazing tutorials, tips/tricks on Flutter & DSA.