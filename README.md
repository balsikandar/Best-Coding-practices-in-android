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
   * [Must follow rules](#must-follow-rules)
      * [Horizontal and vertical formatting rule](#horizontal-and-vertical-formatting-rule)
      * [Boy Scout rule](#boy-scout-rule)
   * [Must have android tools](#must-have-android-tools)
      * [SonarLint](#sonarlint)
      * [FindBugs](#findbugs)
   * [Stupid mistakes by developers](#stupid-mistakes-by-developers)
      * [Not using parcelable](#not-using-parcelable)
      * [Directly accessing variables](#directly-accessing-variables)
      * [Creating too many class variables](#creating-too-many-class-variables)
      * [Integer.valueOf](#integer-valueof)
   * [Some good articles](#some-good-articles)
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
  
 
 if (vehicle.getCar().getModel() != null) {
     int price = vehicle.getCar().getModel().getPrice();
 }
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
 Short names for short living variables and good and meaningful names for long living ones because they'll be with you for long-long time. They are family.
 ```
 For e.g. index variable within for loop can be 'i' but as class variable should be 'index'
 ```
 
 ### Parameter Object pattern
 
 ## Must follow rules
 
 ### Horizontal and vertical formatting rule
 
 ### Boy Scout rule
 
 ## Must have Android tools
 
 ### SonarLint
 I recommend this, i have been using it and i got to know about this from a colleague, sometimes they can be helpful, kidding. It has several features best one to just scan the modified classes and it'll automatically criticise you for your bad code and how ugly you can be sometimes. BTW **Cognitive complexity** we talked earlier it helps.
 
 ### FindBugs
 It's a program that uses static code analysis to find bugs in java code just like SonarLint. To know more about FindBug check this. Flip a coin or whatever but pick one of these tools.
 
 ## Stupid mistakes by Developers
 
 ### Not using parcelable
 
 ### Directly accessing variables
 
 ### Creating too many class variables
 
 ### Integer.valueOf
 
 ## Some good articles
 
 - [Right way to implement Splash screen](#https://www.bignerdranch.com/blog/splash-screens-the-right-way/)
 - [Debugging Android Database and SharedPreferences](#https://medium.com/mindorks/debugging-android-databases-and-shared-preferences-in-the-easiest-way-e5f705dfc06b)
 
 ## The coding principles
 
 ### SOLID
 It's a mnemonic acronym that helps define the five basic object-oriented design principles:
 - Single Responsibility Principle
 - Open-Closed Principle
 - Liskov Substitution Principle
 - Interface Segregation Principle
 - Dependency Inversion Principle
 
 For complete reference check.
 
 ### DRY principle
 Never ever write same piece of code twice make it your ironclad rule and strictly prohibit this in your kingdom.
 
 ### The Critics principle
 Okay it's totally made up but it's very logical. When you're reviewing code of your teammates don't be a friend, Be their arch enemy, don't let them make mistakes that you might have to clean someday. Cleaning other's shit will make your hand dirty. Enforce good practices in code reviews.
 
 ## Must have Android Libraries
 
 ### Android Debug Database
 
 ### Robin
 Robin is a logging library for Bundle data passed between Activities and fragments. It also provides a callback to send screen views of user visited pages to your analytics client
 
 ### Android studio plugins
 
 This is a list of all awesome and useful android studio plugins.
