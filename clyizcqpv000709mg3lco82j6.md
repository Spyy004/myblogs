---
title: "Anidex: A Step-by-Step Journey to Building an Animal Pokedex"
seoTitle: "Building Anidex: Your Animal Pokedex Guide"
seoDescription: "Discover Anidex, the ultimate Pokedex for real-world animals, with identification, chatting, offline features, and more for nature enthusiasts"
datePublished: Fri Jul 12 2024 17:36:57 GMT+0000 (Coordinated Universal Time)
cuid: clyizcqpv000709mg3lco82j6
slug: anidex-a-step-by-step-journey-to-building-an-animal-pokedex
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1720805715903/cb681bfd-2cd4-4940-b375-4fbac5aac664.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1720805790135/e7291e36-5a93-477e-9883-f8089cd6dbce.png
tags: ai, flutter, hashnode, frontend-development, aifortomorrow

---

# Introduction

This is my official entry to the **#AIForTomorrow** hackathon organized by Hashnode. It has been a long time since I built a project, and this AI hackathon came at the perfect time for me.

The project that I have built is Anidex. **Anidex is your Pokedex but for real-world animals and birds.**

GitHub Repo Link: [https://github.com/Spyyy004/anidex/](https://github.com/Spyyy004/anidex/tree/main)

App Download Link: [https://github.com/Spyyy004/anidex/releases/download/1.0.0/anidex.apk](https://github.com/Spyyy004/anidex/releases/download/1.0.0/anidex.apk)  
  
Website Link : [https://anidex.tech/](https://anidex.tech/)

Let's see how I got the idea for the project, how I actually built it, the features it possesses, and what my future plans are.

# Inspiration

Recently, I went on a one-day hike with my friends and saw a bird I had never seen before. I thought of using Google Lens to identify it, but poor connectivity prevented me from getting any information. I captured an image and later used Lens to search for the bird. While I did find some basic information, I had to visit multiple websites to learn more about it. This tedious process made me realize the need for a more comprehensive solution.

That's when I thought of creating an app that not only identifies animals but also provides detailed information about their habitats, behaviors, and conservation status—all in one place. And if the information seems too dry, users can actually engage with the animal through a fun chat interface.

I envisioned a tool that combines the educational aspects of a traditional field guide with the interactive experience of a chat feature. Imagine being able to point your phone at a bird in your backyard and instantly learn about its species, migration patterns, and even have a conversation with it, just like a Pokémon trainer! This vision led to the creation of Anidex, your digital Pokedex for real-world animals and birds.

# Features

Anidex is feature packed. Here is a list of features the app possesses.

### Scan and Identify Animals

Imagine being in a park, surrounded by nature's wonders. You whip out your phone, open Anidex, and aim your camera at a beautiful bird perched on a tree branch. With a quick scan, Anidex identifies the bird as a Blue Jay, providing detailed information about its habitat, diet, and distinctive features. The seamless real-time scanning capability powered by Gemini's AI instantly enriches your outdoor experience, turning every hike into a learning adventure.

### Talk to Animals

Curiosity piqued? After scanning the Blue Jay, you decide to engage further. With a tap of a button, you enter the "Talk to Blue Jay" feature. The screen lights up with a chat interface where you can ask questions like, "What's your favorite food?" or "Tell me about your nest." Powered by Gemini's AI, the Blue Jay responds with fascinating insights, enhancing your understanding of its lifestyle in a uniquely interactive way.

### Offline Scanning

Picture this: you're on a remote trail, far from cell service. No worries—Anidex has you covered with its offline scanning feature. Even without an internet connection, you can continue scanning and identifying animals. The app stores essential data locally, ensuring seamless access to information without interruption. Once you're back online, simply sync your scans to update your collection effortlessly.

### Save Scans

Back at home, you review your collection of scanned animals. Each entry holds memories of your outdoor adventures and discoveries. With Anidex, saving scans is easy and intuitive. You can revisit details about any animal at any time, whether it's the majestic eagle you spotted last week or the curious fox you encountered yesterday.

### Favourite Animals

Some animals leave a lasting impression. With Anidex, you can mark them as favourites with a simple tap. Whether it's the rarest species or a personal favourite, keeping track is effortless. Your favourites list becomes a curated gallery of the wildlife you cherish, ready to inspire and delight whenever you revisit it.

### Leaderboard and Badges

Feeling competitive? Anidex adds a fun twist with its leaderboard and badges. Every scan contributes to your ranking, earning you badges for milestones like "Explorer" or "Wildlife Enthusiast." See how you stack up against other users, fostering a sense of community and achievement in your wildlife discoveries.

### Explore

Embark on a journey through the Anidex community's collective knowledge. The Explore feature offers a treasure trove of scanned animals contributed by users worldwide. Whether you're researching a specific species or simply browsing, the categorized and searchable database ensures you find what you're looking for with ease.

# Building the App

From the outset, Anidex was designed with one goal: to deliver the ultimate user experience in wildlife exploration. By placing the Scan Page front and center upon installation, users dive right into the app's core functionality without barriers. No sign-in required means immediate access to scanning and exploring animals, fostering a seamless and engaging experience from the very first interaction.

Each feature, from scanning and chatting with animals to saving and exploring wildlife, is crafted to inspire curiosity and connect users with the natural world effortlessly. Anidex isn't just an app—it's a gateway to discovery, empowering users to appreciate and learn about wildlife in ways that are intuitive, immersive, and above all, enjoyable.

The app is built with Flutter and Firebase. The AI features are powered by Gemini 1.5 Pro. It has a total of 10 screens. Since I have a decent hands on experience in Flutter and Firebase, It didn't take much time for me to code the UI and connect it to the DB.

Talking in depth about the database. I am using NoSQL database. I have users, scans, leaderboard, and badges collection.

This is my user schema

```json
{
  "badges": ["string"],
  "favorites": ["string"],
  "firstName": "string",
  "lastName": "string",
  "phoneNumber": "string",
  "profilePic": "string",
  "scans": ["string"],
  "createdAt": "timestamp",
  "userId": "string",
}
```

This is my Scan schema

```json
{
  "imagePath": "string",
   "scanId": "string",
  "scanData": {
    "animalIdentification": "string",
    "basicInformation": {
      "behavior": "string",
      "classification": {
        "class": "string",
        "family": "string",
        "genus": "string",
        "kingdom": "string",
        "order": "string",
        "phylum": "string",
        "species": "string"
      },
      "commonName": "string",
      "conservationStatus": "string",
      "diet": "string",
      "geographicDistribution": [
        "string"
      ],
      "habitat": "string",
      "interestingFacts": [
        "string"
      ],
      "physicalDescription": "string",
      "rarity": "number",
      "scientificName": "string",
      "type": "string"
    },
    "timestamp": "timestamp",
    "userId": "string"
  }
}
```

I've implemented robust error handling mechanisms to ensure smooth performance across various user interactions. Additionally, I've optimized data fetching and storage processes to maintain app responsiveness even under heavy user traffic. By adhering to these best practices from the outset, Anidex is poised to deliver a reliable and seamless experience for all users.

## Challenges

The biggest challenge was to make Gemini give me data in the format I wanted. I experimented around with various prompts to get data in the perfect format.

Another big challenge was offline scans and syncing data. I used the path\_provider and connectivity package to get access to local storage and save images when the user is not connected to the internet. Here is the code for storing and retriving images from local storage.

```plaintext
  Future<void> _loadLocalScans() async {
    try {
      final directory = await getApplicationDocumentsDirectory();
      if (!await Directory(directory.path).exists()) {
        print('Directory does not exist: ${directory.path}');
        return;
      }
      List<LocalScanItem> scans = await fetchLocalScans(directory.path);
      setState(() {
        localScans = scans;
      });
    } catch (e) {
      print('Error loading local scans: $e');
    }
  }

  Future<String?> saveImageLocally(XFile imageFile) async {
    try {
      // Get the local app directory path using path_provider
      final directory = await getApplicationDocumentsDirectory();
      final imagePath = '${directory.path}/${DateTime.now().millisecondsSinceEpoch}.jpg';

      // Ensure directory exists
      await Directory(directory.path).create(recursive: true);

      // Read the file as bytes
      final bytes = await imageFile.readAsBytes();

      // Write the bytes to a new file
      final file = File(imagePath);
      await file.writeAsBytes(bytes);

      return imagePath;
    } catch (e) {
      print('Error saving image locally: $e');
      return null;
    }
  }
```

I also restricted access to sections like My Scans, Favourites, and My Profile when disconnected because all this data is fetched in realtime from the Firebase DB for now.

I am not a good designer and I always struggle building good designs. Thankfully, the pinterest community helped me this time. I found some decent design inspirations for a pokedex style info card.

The app has a plain and minimalistic design. The typography is based on poppins and consistent throughout the app. Here are a few screenshots of the current app.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720798457795/5f0ccf87-f817-4569-aefc-16c276be8619.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720798486067/cf1057f6-c950-4de1-8bf5-607f87a48909.png align="center")

# Impact

Anidex aims to transform wildlife exploration by making it easy and immediate to identify animals through innovative technology.

By removing the need for a sign-in page, the app ensures that learning about wildlife is accessible to everyone from the start. This approach encourages users to engage with nature effortlessly, fostering a deeper connection and appreciation for biodiversity.

With features like real-time animal chats and access to scan animals without internet, Anidex enhances learning opportunities and promotes conservation awareness in a user-friendly way.

Whether users are exploring local habitats or encountering wildlife in remote areas, the app inspires curiosity and encourages environmental stewardship. Anidex is designed not just as an app, but as a tool that empowers individuals to explore, learn, and contribute to the conservation of our natural world.

# Future Plans

As Anidex continues to evolve, I have exciting plans to enrich its features and expand its impact:

**1\. Enhanced Filtering and Exploration**

* Currently, Anidex offers a search bar for quick access to species information. In the pipeline are advanced filtering options, allowing users to sort scans and explore wildlife by various categories such as habitat, rarity, and region. These enhancements will empower users to tailor their wildlife discoveries to specific interests and deepen their learning experiences.
    

**2\. Diverse Leaderboards**

* While the current leaderboard celebrates total scans, upcoming updates will introduce specialized leaderboards. These will highlight achievements based on animal rarity, geographic location, and user contributions. By gamifying exploration through different metrics, Anidex will foster friendly competition and community engagement among wildlife enthusiasts worldwide.
    

**3\. AI-Powered Quizlet**

* Imagine starting your day with a fun and informative challenge—Anidex will soon feature a daily AI-powered quizlet. Each quiz question will offer insights into animal behaviors, habitats, and conservation efforts. Participants can earn points and compete on a dedicated leaderboard, encouraging regular engagement while expanding their wildlife knowledge.
    

**4\. iOS Development**

* Bringing Anidex to iOS devices is a top priority. While integrating camera and storage features poses unique challenges on iOS, I'm committed to delivering a seamless experience across platforms. Stay tuned as we navigate the app store guidelines and ensure Anidex reaches a broader audience passionate about wildlife exploration.
    

These future updates reflect Anidex's ongoing commitment to enhancing user experience, fostering community engagement, and promoting wildlife conservation through innovative technology. I look forward to sharing these developments with you as we continue to grow and refine Anidex.

# Conclusion

Creating Anidex has been a long-awaited project for me, driven by my love for wildlife and technology. It's become one of my favorite side projects because it serves a practical purpose and offers fun for everyone.

Anidex isn't just an app—it's a tool that helps you discover and learn about wildlife effortlessly. Whether you're identifying birds in your backyard or exploring animals on a hike, Anidex makes it easy and enjoyable.

Looking ahead, we're working on adding more features like filters and daily quizzes, and we're excited to bring Anidex to iOS soon. Our goal remains to make wildlife exploration accessible and engaging for everyone.

Join me on this journey with Anidex as we continue to grow and make learning about wildlife a part of everyday fun.