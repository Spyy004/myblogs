## Let's build a Chrome Extension using Flutter!

# Intro
In todays' article, we will create a Chrome extension using Flutter. As we know Flutter can be used to build apps across multiple platforms, so we will make use of Flutter web in order to build our Chrome extension.

So without wasting any time, let's get started. 
![RunGIF.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1647510091038/iSDez72NQ.gif)

# Project Setup
First of all, we will create a new Flutter project and enable web support for it. You can do this by typing this command into your integrated terminal.

```
flutter run -d chrome
```
This will run the Flutter project in your Chrome browser. 

# Coding the Logic
Now let's see how we can change our current website into an extension. For that, we will need to go to our index.html file. This file is present in the web folder. In index.html, there will be some piece of code between the <script></script> tag.

Just replace the code with the whole script tag with the following code.

```
<script
 type="application/javascript" src="main.dart.js">
</script>
```

Once done with this, we will need to change the manifest.json file. manifest.json is also in the web folder as well. Replace the complete code in the manifest.json with this code.

```
{
    "name": "flutter_chrome_extension",
    "description": "flutter_chrome_extension",
    "version": "1.0.0",
    "content_security_policy": {
        "extension_pages": "script-src 'self' ; object-src 'self'"
    },
    "action": {
        "default_popup": "index.html",
        "default_icon": "/icons/Icon-192.png"
    },
    "manifest_version": 3
}
```
We are done with making the required changes to make an extension. Let's run our current code. For that, type this command in the integrated terminal. 

```
flutter build web --web-renderer html --csp
```

Once our project is up and running, let's add it to chrome. For that, type this in your web browser.

```
chrome://extensions/
```
You will reach a page like this.
![Screenshot (148).png](https://cdn.hashnode.com/res/hashnode/image/upload/v1647502273476/cK5h2UqXj.png)

On this page, there will be a toggle on the top-right Turn it on and then you will see three buttons on top. Out of those 3, tap on the load unpacked button. It will ask you for a folder, there we will need to add the web folder which is under the build folder in our project directory. 

Now, open a new tab and you will see a new extension with Flutter icon. Tap on it and Voila! you will see our Flutter counter app. 
![Screenshot (149).png](https://cdn.hashnode.com/res/hashnode/image/upload/v1647502869437/6VuRTQBF4.png)

If you were able to do this then CONGRATULATIONS! You have successfully created a Chrome extension with your Flutter code. 

You can think of unique ideas for your extension. For example a crypto price tracker, discount coupon tracker, and so on. If you want to change the icon of your extension, add the new image in your icon folder in the web folder and mention that file name in manifest.json.

```
    "action": {
        "default_popup": "index.html",
        "default_icon": "/icons/Icon-192.png"  // make the change here.
    },
```

# Conclusion
This concludes today's article. We have seen how to make a chrome extension. I have just shown you how to make the required changes to convert your current web code to an extension. You can now play around and build some cool stuff with it.

You can appreciate and support my blogs via.

![https://cdn.hashnode.com/res/hashnode/image/upload/v1646372265341/O0KkM6E-0.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1646372265341/O0KkM6E-0.png)

Also, let's connect on [Twitter](https://twitter.com/Iyush004). Follow CSwithIyush for more amazing tutorials, tips/tricks on Flutter & DSA.