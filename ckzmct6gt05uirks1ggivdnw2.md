## 5 Mistakes you must avoid as a new Flutter developer

# Introduction
As beginners, we all make mistakes but some wise man said, it is better to learn from someone else's mistakes rather than from yours. So that is exactly what you will do after reading this article.

Today, I will share the 5 mistakes I made as a newbie Flutter developer which reduced my efficiency and made my codebase messy too.

# Mistake 1
**Not keeping a design in mind**. Keep a design ready before you start coding your UI. If you are working on a solo personal project and you don't have good design skills, go to figma's open source community and get design inspirations from there.
![Dramatic Crossroads 14022022115334.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1644820314998/vU89rvAN0.jpeg)

You can [check out the community here](https://www.figma.com/community). Everything there is free and you get all the pages, icons, and everything ready made for you. Having a design before you start coding will save you tons of time.

# Mistake 2
**Not structuring your project.** This is a very common mistake among newbie developers. Please don't go on creating new .dart files everytime. Structure your codebase properly as it will be easier to navigate around files as your codebase grows bigger in size. Even if your project is small, make a habit to structure it accordingly.

# Mistake 3
**Not converting JSON object into models**. Well, this is probably the best tip a beginner can recieve which will make his/her codebase cleaner and make him/her much more efficient. Converting your JSON object into classes is a recommended practice as it is easier to debug and check for any NULL value errors.

Things are good when the JSON data you recieve isn't complex, but for a complex JSON data, please convert them into classes and then use them across your app. If you feel that you are too lazy to write classes for the json data then open source has got you covered there too.
![Young Michael Scott Shaking Ed Trucks Hand 14022022115506.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1644820326680/iu33qp5XX.jpeg)


[Use this website](https://app.quicktype.io/). Copy paste your JSON object and it will give you the dart code that parses it into a Dart class. This is one of the best tools I use in all my Flutter projects. 

# Mistake 4
**Trying to build everything on their own.** Use packages. Yes, do not waste time implementing a complex bottom navigation bar by yourself. There are people who have already done it for you. Just go to pub.dev, search for your desired widget, and import it. If it is not available as a package, then you should start implementing it. 
![Thick Book vs Thin Book 14022022115649.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1644820335023/ZwRlTQdoC.jpeg)

You must know when to use an external package and when not to. If you have to do some minor changes in the widget, then its fine by doing it yourself. If it requires to change a lot of internal properties and a custom paint, then it is time to search for packages.

# Mistake 5
**Not taking advantage of extraction**. Make constants and extract widgets whenever you can. Suppose I have a red colored rectangular button which is to be used across 5 screens then my first thought would be to extract it. This is how you can extract a widget. 
![Screenshot (103).png](https://cdn.hashnode.com/res/hashnode/image/upload/v1644819046684/aVbKPi-oH.png)
With extraction, now you don't need to code the button 5 times. You do it once, and use that widget every where you want to. You want to have different color of the button on different pages? Simple, make the color as a variable and then pass it in the arguements. 
```
Your material App
{
...
MyButton(buttonColor:Colors.black)
...
}

class MyButton extends StatelessWidget {
 Color buttonColor;
  xtext({
    Key key,
    this.buttonColor
  }) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Container(
    color: buttonColor,
);
  }
}
```

# Bonus Tip
Avoid rebuilding widgets. Well, the best way to avoid rebuilding unecessary widgets is obviously by using state manegement but you can also use the const keyword before widgets. The const keyword doesn't rebuild the widget during the set state. 

The const keyword will only work if all the values inside the widgets are hardcoded numbers and not variables. The const keyword won't work in the class MyButton which we have used above but it will work on a widget like this

```
const Text('Hi i am a hardcoded text'),
```

# Conclusion
So this concludes our article on mistakes that you must avoid as a beginner. I hope these 5 tips will improve your efficiency and make you a better Flutter developer.

My blog is also featured on [tech-dev.blogs](https://t.co/ACp2EwR5os). For more tips/tricks/tutorials on Flutter, follow me and do not forget to subscribe!

![Albert Einstein 14022022115825.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1644820342866/SmTVFi8ZT.jpeg)