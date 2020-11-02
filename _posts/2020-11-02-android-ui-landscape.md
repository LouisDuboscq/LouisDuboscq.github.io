---
layout: post
title: Android UI history
subtitle: 10 years of Android
tags: [android, android-jetpack-compose]
comments: true
---
 
Let's just see how Android **UI** development has evolved those last years and see what's next.

## Java 7 + findById

Did you remember this 👻 from the past ? 
  
{% gist 157fad61faacccf446a657adf39e4693 %} 
   
Lot of boilerplate, awkward namings, crashs on runtime, etc.

**Java 7 and findById ! I didn't miss you 🙅‍♂️**

## Butterknife

Around 2016, Android developpers used to import Butterknife. This was an awesome library which avoided all the UI boilerplate. 
You also could bind strings, dimensions, colors. It was 👌 at the time but it lacked compile time safety.
 
{% gist 29b435568b930352c9468f7f6396a9ab %} 
    
Butterknife is now deprecated and it's recommended to switch to view binding / data binding.

## DataBinding

Jetpack released [Data Binding library](https://developer.android.com/topic/libraries/data-binding). 
It allows to bind data from code to views with data tags and bind views to code.
Population data boilerplate is eliminated : no more setText(), setImageResource() etc. 
Event listeners can also be set in data binding. Kotlin code can significantly be reduced this way.

**DataBinding is the recommendation, since ~2019, for view building but it adds a bit of overhead compared to Android Kotlin Extensions**

## View Binding

Android Studio 3.6 released ViewBinding. It's almost same as DataBinding except : 
- Layouts do not need layout tag as in DataBinding
- it can't be used if there is a layout with data in xml
- faster and more efficient over DataBinding
- type-safe and null-safe
 
ViewBinding can do less than DataBinding but its advantage is speed.
  
## Kotlin synthetic

Kotlin synthetic calls findViewById on the views under the hood, but it calls it only once for each 
view and caches the view reference for next calls.

{% gist c4179f5ed85af353fc2c890a20ddef11 %}  

{: .box-warning}
**Warning:** Typing isn't guaranteed
 
Kotlin synthetic is heavily used in android applications because it is really elegant version of findViewById, 
it has good performance and it is easy to start with. But it lacks compile time safety. This is why DataBinding is recommended over this.
  
## Jetpack compose 

Jetpack compose is the new thrilling UI toolkit for Android applications. 
Alpha has been released in august 2020 and a full release is expected for 2021.

It's a completely different way to build Android UI.
It looks more like React, Flutter or SwiftUI. 
 
It combines declarative API and reactive programming model.
The way to build the UI are intuitive :

![](https://1.bp.blogspot.com/-cxPO9bE5QT4/X0Vw6rOOAAI/AAAAAAAAPjg/UmpOu9X6wHMUFaEjuJEdfOcOcwuKEefTwCLcBGAsYHQ/s1600/Screen%2BShot%2B2019-05-06%2Bat%2B9.48.28%2BAM.png)
  
It allows developpers to significantly reduce, modularize and reuse code.

{: .box-warning}
**Warning:** All the API may change until full release planned in 2021

It's moving fast ! This is at a time an advantage and a disadvantage.
On the one hand lot's of feature is already available and the community is impressive.
Even if something is missing in the library, it can be released very quickly. 
One the other hand, it's sure changes are expected before full release in 2021.

I think Compose will be in Android ecosystem as important as the move from Java to Kotlin back in years.

I already made these moves findView -> Butterknife -> ViewBinding / DataBinding / Kotlin Synthetic -> next Jetpack compose
And you, will you try compose, stay with DataBinding/Synthetic or maybe you regret the time of Java7/findById ?