## Packages vs Plugins

# Introduction
This is the 3rd article of this vs that series in Flutter. Recently, I wrote an article on how you can publish your own package on pub dev. Someone asked me how do you know it is a package and not a plugin, so I thought of writing a small article on the same. A lot of people often get confused between both of them So let's see what both of them are and what are the differences.
![fluter.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1647150384835/BaE5MTpqm.png)

# What is a package?
Suppose I want to create a flipping card animation. All I need to do for that is to write some dart code. I will need the animation builder widget, transform widget, and some mathematical calculations. I don't think I will need to use any other language than dart to build a flip-card animation. 

So I write the code and publish my flip-card animation on pub dev. This is what you call a package. If all the code written inside the package is in the dart, it is called a package.

# What is a plugin
Now, suppose I want to create a Snapchat-like AR camera. Something like the dog filter or the cat filter. In this case, I will need to think and write some dart code but I will also need to write some Java code or Objective-C code. 

Why the java code? Because I have to generate an intent and ask the device to open the camera for me. This is done internally with Java code. Another example can be the URL launcher. Url launcher is one of the top plugins on pub dev. 

If you import the package and try digging in the code, you will see some files in java and objective c. The code inside that is to generate permission to open the web browser.

In short, if your package consists of code in any language other than a dart, it becomes a plugin. 

# Difference

1. Packages have only dart code. Plugins have dart + native code.
2. Platform-dependent packages are generally plugins. Eg: url_launcher.
3 Every plugin is a package but every package is not a plugin.
![download (1).png](https://cdn.hashnode.com/res/hashnode/image/upload/v1647150367788/-HoGkYlw4.png)

# Conclusion
So, this concludes our short article on packages vs plugins. I hope that after reading this article, you now understand the difference between package and plugin.

 If you learned something new today, then share this article among fellow flutter devs and help them too.

You can appreciate and support my blogs via.

![https://cdn.hashnode.com/res/hashnode/image/upload/v1646372265341/O0KkM6E-0.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1646372265341/O0KkM6E-0.png)

Also, let's connect on [Twitter](https://twitter.com/Iyush004). Follow CSwithIyush for more amazing tutorials, tips/tricks on Flutter & DSA.