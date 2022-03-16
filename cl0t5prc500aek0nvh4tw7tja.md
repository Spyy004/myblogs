## 4 Ways to Store Data Locally with your Flutter apps.

# Introduction 📕
Storage is a very important aspect of any app. You will need to store some kind of data in any app that you make. Unless and until it is just a 1 or 2-page apps like a calculator or weather app. 

There are 2 major ways to store data. One is to use databases and call them via APIs or fetch data directly from them. The second is to make use of the local storage of your android devices. Today, we will explore the second option. 

We will look at 4 different ways to store data locally that are usually used. We will see what are their features and how to use them.

# SQLite
SQLite is a SQL database that can be used to store data locally. It is very useful if you want to store a large amount of data in an ordered manner. One example would be a to-do list. 

Go read these [official docs](https://docs.flutter.dev/cookbook/persistence/sqlite) to get an idea of how you can use SQLite to persist data locally.

There are some cases where we don't need SQLite. For example, if we just need to store something like dark mode or light mode of the app, why use a table like SQL database? We have different options to store such kinds of data. One of them is shared preferences. Let's have a look at it.
![sqlite.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1647354375350/7JrS-30Lw.png)

# Shared Preferences
Shared Preferences is one of the most popular (if not the most popular) ways to store data locally. It uses the concept of key-value pairs to store data locally. We can store integers, doubles, floats, and strings with Shared Preferences. It is a great tool if we want to store some user preferences locally. For example, app theme.

Go [read this article](https://cswithiyush.hashnode.dev/what-is-and-how-to-use-shared-preferences-in-flutter) to know how to use Shared Preferences to store your data locally.

What if I wanted to store the login status of a user? Shouldn't Shared Preferences be the best way to do it? Umm, I would say no. I am saying no because shared preferences don't encrypt the data it is storing.

Suppose I want to save some kind of access token locally which verifies if the user is logged in or not, it can be unsafe to store it unencrypted. So this is where Secure Storage comes in. Let's see what it is. 
![spref.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1647354070070/U9zn9-tK_.png)

# Secure Storage
The concept of Secure Storage is similar to shared preferences, i.e store data as key-value pairs. The only difference is that in secure storage, the stored data is encrypted.

Here is the [documentation](https://pub.dev/packages/flutter_secure_storage) that will guide you on how to use secure storage. 
![download (2).png](https://cdn.hashnode.com/res/hashnode/image/upload/v1647354024382/kC8DPHdvi.png)

# Hive

Hive is a local data storage that is very popular among Flutter developers. The two main reasons for its popularity are that it is a NoSQL database and it can not only store primitive data types, but it can also store Dart classes. 

So yeah, that is a big deal. You can create a class and store it as a NoSQL document in the hive database. It can store almost the same amount of data compared to SQLite. Hive is used for caching text messages of a particular chat, for caching the profile details of the user, and much more complex data like this.

Hive is definitely an upgrade over Shared Preferences and Secure Storage in terms of data storing size and if you prefer NoSQL over SQL, then Hive is the way to go.

Hive has amazing [documentation](https://docs.hivedb.dev/#/basics/hive_in_flutter). Read it if you want to set up Hive in your app and use it as your local database.
![hive.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1647353990564/GQKaREXQr.png)

# Conclusion 👋🏻
So with this, we conclude our article on different types of local databases. Every option provides a solution according to your needs. 

- If you have a huge amount of structured data, go for SQLite.
- If you want to store just some boolean or integer, go for Shared Preferences.
- If you want to store private or classified data, go for Secure Storage
- If you have a huge amount of data or Dart classes and don't want to worry about the structure much, go for Hive.

You can appreciate and support my blogs via.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1646372265341/O0KkM6E-0.png)

Also, let's connect on [Twitter](https://twitter.com/Iyush004). Follow CSwithIyush for more amazing tutorials, tips/tricks on Flutter & DSA.