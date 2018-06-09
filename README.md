## This repo is to add best practices that developers can apply to write clean, short and testable code in android.

[![Open Source Love](https://badges.frapsoft.com/os/v1/open-source.svg?v=102)](https://opensource.org/licenses/Apache-2.0)
[![License](https://img.shields.io/badge/license-Apache%202.0-blue.svg)](https://github.com/balsikandar/Android-Studio-Plugins/blob/master/LICENSE)

## Table of Contents

   * [Writing clean code](#writing-clean-code)
      * [Nested Ifs](#nested-ifs)
      * [Cognitive complexity](#cognitive-complexity)
      * [Region](#region)
      * [Naming](#naming)
      * [Parameter Object pattern](#parameter-object-pattern)
      * [No comments](#no-comments)
   * [Must follow rules](#must-follow-rules)
      * [Horizontal and vertical formatting rule](#horizontal-and-vertical-formatting-rule)
      * [Boy Scout rule](#boy-scout-rule)
      * [Keep it simple rule](#keep-it-simple)
      * [Consistency](#consistency)
   * [Must have android tools](#must-have-android-tools)
      * [SonarLint](#sonarlint)
      * [FindBugs](#findbugs)
      * [Codota](#codota)
   * [Stupid mistakes by developers](#stupid-mistakes-by-developers)
   * [Some good articles](#some-good-articles)
   * [High performance layouts](#high-performance-layouts)   
   * [The coding principles](#the-coding-principles)
      * [SOLID](#solid)
      * [DRY principle](#dry-principle)
      * [The critics principle](#the-critics-principle)
   * [Must have Android Libraries](#android-libraries)
      * [Android Debug Database](#android-debug-database)
      * [Robin](#robin)
      * [Android studio plugins](#android-studio-plugins)
   * [Quotes from authors](#quotes-from-authors)
      * [uncle-bob](#uncle-bob)
      * [kent](#kent)
      
 ##  Writing clean code
 
 ### Nested If's
 I hate this, I seriously do, you have statements which require multiple checks like this below code and it goes so deep really deep, In coding which is bad actually.
 
 ```
 if (vehicle != null) {
        if (vehicle.getCar() != null) {
            if (vehicle.getCar().getModel() != null) {
                int price = vehicle.getCar().getModel().getPrice();
            }
 
        }
    }
 ```
 
 And the thing is, It can be avoided, you totally can, like this. As you see below one is more readable and easy to understand.
 ```
 if (vehicle == null || vehicle.getCar() == null || vehicle.getCar().getModel() == null) return;
  
 
 
 int price = vehicle.getCar().getModel().getPrice();
 
 ```
 
 ### Cognitive complexity
 **Definition**: It's a psychological characteristic or psychological variable that indicates how complex or simple is the frame and perceptual skill of a person.
 
 In programming a method with nested if else's and larger size causes high cognitive complexity means less understandability. So better to split large methods into logically separated smaller ones and use above **Nested If's** trick to reduce it. Also SonarLint a static code analysis tool calculates this for you in realtime in android studio you can use sonar to see how you doing.
 
 ### Region
 
 Use regions to separate your code fragments in big classes like britisher's did with divide and rule policy, very effective ask indians.
 ```
 //region meaningful name of your logically separated region
 do your work here.
 //endregion
 ```
 
 ### Naming
 Short names for short living variables and good and meaningful names for long living ones because they'll be with you for a long-long time. They are family.
 ```
 For e.g. index variable within for loop can be 'i' but as class variable should be 'index'
 ```
 
 ### [Parameter Object pattern](https://refactoring.guru/introduce-parameter-object)
 There is no restriction to number of paramters passed in methods but it's a bad practice to pass more than 3 or 4, So if your methods contains a repeating group of parameters which are passed among several methods. We can avoid that by replacing these parameters with an object.
 
 ### Height and width constraint
 
 
 ## Must follow rules
 
 ### Horizontal and vertical formatting rule
 It's not a constraint but a formatting rule that should be followed to keep your code vertically and horizontally small so with just one glance you can read it all.
 
 ### No comments
 "Code never lies, comments sometimes do." - **Ron Jeffries**
 * Always try to explain yourself in code because you're a coder not a commenter.
 * Don't add obvious noise.
 * Add comments for Public APIs.
 * Use it where necessary as time passes by code will change comment wouldn't.
 * You're being paid for coding not commenting.
 
 
 ### Boy Scout rule
 **Definition**: Leave the campground cleaner than you found it
 
 ### Consistency
 If you do something in one way then do it the same way everywhere- **Uncle Bob**
 
 ### Keep it simple rule
 Keep it simple stupid. Simpler is always better. Reduce complexity as much as possible - **Uncle Bob**
 
 
 ## Must have Android tools
 
 ### SonarLint
 I recommend this, i have been using it and i got to know about this from a colleague, sometimes they can be helpful, kidding. It has several features best one to just scan the modified classes and it'll automatically criticise you for your bad code and how ugly you can be sometimes. BTW **Cognitive complexity** we talked earlier it helps.
 
 ### FindBugs
 It's a program that uses static code analysis to find bugs in java code just like SonarLint. To know more about FindBug check this. Flip a coin or whatever but pick one of these tools.
 
 ### [Codota](https://www.codota.com/)
 It's a great tool to help you with code segments that you might otherwise have to search on github and stackoverflow.
 
 ## Stupid mistakes by Developers
 
 ### Not using parcelable
 If you're not using it then you're making a mistake. 
 
 * Parcelable is designed for android.
 * Parcelable is faster than serializable interface
 * Parcelable interface takes more time for implemetation compared to serializable interface but there are plugins to automate it.
 * Serializable interface is easier to implement
 * Serializable interface create a lot of temporary objects and cause quite a bit of garbage collection
 * Parcelable array can be pass via Intent in android
 
 ### Directly accessing variables
 If you're accessing another class variables using dot operator it'll become ugly with time. There is a reason why we have access modifiers keep your variables private and se getters to access those variables.
 
 This'll reduce code coupling. People who code in activity and fragments might know what i'm talking about.
 
 ### Creating too many class variables
 If you still remember class as in OOPs concept class represents an entity a noun. A class has attributes which define it's states and methods it's behavior.
 
 I have a totally different understanding from my experience I believe attributes are the real deal and methods they just work on it. So try to keep attributes which are relevant to class and trim those extra global variables(mostly booleans) you added for whatever reason.
 
 Parameter object pattern can be of some help her.
 
 
 ### Integer.valueOf
 Integer.valueOf returns `Integer` object whereas Integer.parseInt returns primitive `int`. Avoid using Objects for primitive types they're not meant for it.
 
 ### Looping to add elements to arraylist
 People there is addAll method in ArrayList use it for adding another list.
 
 ### [Avoid overdraw](https://developer.android.com/topic/performance/rendering/overdraw)
 In nested layouts we usually set `backgroundColor` property to ViewGroups without realising that it'll result in overdraw. This reduces your layouts performance. In Developer Options setting you can enable Overdraw to pinpoint your bad layouts.
  
 
 ## Some good articles
 
 - [Right way to implement Splash screen](#https://www.bignerdranch.com/blog/splash-screens-the-right-way/)
 - [Debugging Android Database and SharedPreferences](#https://medium.com/mindorks/debugging-android-databases-and-shared-preferences-in-the-easiest-way-e5f705dfc06b)
 - [How to become more productive in android with android studio plugins](https://medium.com/mindorks/how-to-become-more-productive-in-android-with-android-studio-plugins-3beb3861fa7)
 - [Who lives and who dies](https://medium.com/google-developers/who-lives-and-who-dies-process-priorities-on-android-cb151f39044f)
 - [VectorDrawable Adaptive Icons](https://medium.com/@ianhlake/vectordrawable-adaptive-icons-3fed3d3205b5)
 - [How to be a Mock-star](https://medium.com/fueled-engineering/how-to-be-a-mock-star-fc00714d8c2f)
 - [Why i studied full time for a google interview](https://medium.freecodecamp.org/why-i-studied-full-time-for-8-months-for-a-google-interview-cc662ce9bb13)
 - [Picking your compileSdkVersion, minSdkVersion, and targetSdkVersion](https://medium.com/google-developers/picking-your-compilesdkversion-minsdkversion-targetsdkversion-a098a0341ebd)
 - [Supercharging the Android WebView](https://medium.com/myntra-engineering/leveraging-native-power-in-webview-105d248fe71)
 
 
 ## High performance layouts
 
 #### [Anko Layouts](https://github.com/Kotlin/anko/wiki/Anko-Layouts)
 - XML layouts are somewhat slow and aren't typesafe or nullsafe
 - Whereas Anko Layouts are [400% faster](https://android.jlelse.eu/400-faster-layouts-with-anko-da17f32c45dd) than XML layouts.
 
 
 #### [Proteus](https://github.com/flipkart-incubator/proteus)
 Uses json for layout creation ans as you'll know json parsing is faster than xml it improves layout performance.
 
 ## The coding principles
 
 ### SOLID
 It's a mnemonic acronym that helps define the five basic object-oriented design principles:
 - Single Responsibility Principle
 - Open-Closed Principle
 - Liskov Substitution Principle
 - Interface Segregation Principle
 - Dependency Inversion Principle
 
 
 ### DRY principle
 Never ever write same piece of code twice make it your ironclad rule and strictly prohibit this in your kingdom.
 
 ### The Critics principle
 Okay it's totally made up but it's very logical. When you're reviewing code of your teammates don't be a friend, Be their arch enemy, don't let them make mistakes that you might have to clean someday. Cleaning other's shit will make your hand dirty. Enforce good practices in code reviews.
 
 ## Must have Android Libraries
 
 ### [Android Debug Database](https://github.com/amitshekhariitbhu/Android-Debug-Database)
 
 Android Debug Database allows you to view databases and shared preferences directly in your browser in a very simple way.
 
  #### What can Android Debug Database do?
 * See all the databases.
 * See all the data in the shared preferences used in your application.
 * Run any sql query on the given database to update and delete your data.
 * Directly edit the database values.
 * Directly edit the shared preferences.
 * Directly add a row in the database.
 * Directly add a key-value in the shared preferences.
 * Delete database rows and shared preferences.
 * Search in your data.
 * Sort data.
 * Download database.
 * Debug Room inMemory database.
 
 ### [Robin](https://github.com/balsikandar/Robin)
 
 Robin is a logging library for Bundle data passed between Activities and fragments. It also provides a callback to send screen views of user visited pages to your analytics client
 
 ### [Android studio plugins](https://github.com/balsikandar/Android-Studio-Plugins)
 
 This is a list of all awesome and useful android studio plugins.



### TODO
Anything that improves code quality, improves it performance.
### Find this project useful? :heart:
* Support it by clicking the :star: button on the upper right of this page. :v:

### Contact - Let's connect and share knowledge
- [Twitter](https://twitter.com/balsikandar)
- [Github](https://github.com/balsikandar)
- [Medium](https://medium.com/@balsikandar.nsit)
- [Facebook](https://www.facebook.com/balsikandar)

### License

   ```
   Copyright (C) 2017 Bal Sikandar
   Copyright (C) 2011 Android Open Source Project

   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License.
   ```
