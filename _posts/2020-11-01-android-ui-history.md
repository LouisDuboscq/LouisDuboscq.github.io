---
layout: post
title: Android UI - Where to start ?
subtitle: Tools from past to future
tags: [android, android-jetpack-compose]
comments: true
---
 
Let's just see how Android **UI** development has evolved those last years and see what's next.

## Java 7 + findViewById

{% gist 157fad61faacccf446a657adf39e4693 %} 
   
Did you remember this 👻 from the past ? 
  
Traditionnal findViewById was a lot of boilerplate code, crashed on runtime (like often in Android+Java world ?). 
Note at the time naming was weird.

**Java 7 and findViewById ! I didn't miss you 🙅‍♂️**

## Butterknife

~ 2013 :

Android developpers used to import Butterknife. This was an awesome library which avoided all the UI boilerplate. 
You also could bind strings, dimensions, colors. It was 👌 at the time but it lacked compile time safety.
 
{% gist 29b435568b930352c9468f7f6396a9ab %} 
    
Since Kotlin arrival the new Butterknife, Kotterknife, could have been a possibility but it was recommended to switch to ViewBinding.

## Kotlin synthetic

{% gist c4179f5ed85af353fc2c890a20ddef11 %}  

~ 2016 :

Kotlin synthetic is heavily used in android applications because it is really elegant version of findViewById, 
it has good performance and it is easy to start with. 
Under the hood, it calls findViewById, but it calls it only once for each views and caches 
the view reference for next calls.

However :
- This is Kotlin only and Java does not have access to this feature
- It lacks compile time safety and you can access ids of other layouts
- It is not null-safe and you can access views only present in some configuration e.g. landscape layout
- This does not work with multi-module while multi-module is highly recommended and used in applications

This is why ViewBinding is recommended over Synthetic.

I personnally used a lot kotlin synthetic since it takes way less code than all the others solutions and it's really easy to use.
All you need to know is the disadvantages in mind and you're good to go.
 
{: .box-warning}
**Warning:** Anyway in (Kotlin 1.4.20-M2)[https://github.com/JetBrains/kotlin/releases/tag/v1.4.20-M2] Jetbrains deprecated Kotlin Android Extensions compiler plugin in favour of other solutions.
 
R.I.P 🕊️ all of you who migrated your codebase in favour of Android Kotlin extensions.

## DataBinding

~ Late 2018 :

Jetpack released [Data Binding library](https://developer.android.com/topic/libraries/data-binding). 
It allows to bind data from code to views with data tags and bind views to code.
- Population data boilerplate is eliminated : no more setText(), setImageResource() etc. 
- Event listeners can also be set in data binding.
- Kotlin code can significantly be reduced this way.
 
However it increases compilation times 

{: .box-warning}
**Warning:** The solution may be misused with too much business logic in xml files and it may be too complicated to maintain those files 

## View Binding

~ Early 2020 :

Android Studio 3.6 released ViewBinding. 
It's almost same as DataBinding except : 
- Layouts do not need layout tag as in DataBinding
- It can't be used if there is a layout with data in xml
- Faster and more efficient over DataBinding
- Type-safe and null-safe 💪 : it works well in multiple configurations
- Java or Kotlin 🙏

It's definitelly easier to use than DataBinding, have a look if you don't already use it 👍
 
When ViewBinding is enabled in gradle module, it generates for each xml layout file a binding class in Java.
E.g a `ActivityMainBinding` is generated because there is in module a file named `activity_main.xml`.

It is type-safe and null-safe in the sense that generated classes have all xml views in properties already typed and annotated with @Nullable or @NonNull.

ViewBinding can do less than DataBinding but its advantage is speed.
   
{: .box-warning}
**Warning:** ViewBinding introduces memory leaks when playing with fragments, you have to clear fragment binding in onDestroy

{: .box-note}
**Note:** ViewBinding is the recommendation for building views.

## Jetpack compose 

~ 2020-2021 :

Now, Jetpack compose is the new thrilling UI toolkit for Android applications. 
Alpha has been released in august 2020 and a full release is expected for 2021.

It's a completely different way to build Android UI.
It looks more like React, Flutter or SwiftUI. 
 
It combines declarative API and reactive programming model.
The way to build the UI are intuitive :

![](https://1.bp.blogspot.com/-cxPO9bE5QT4/X0Vw6rOOAAI/AAAAAAAAPjg/UmpOu9X6wHMUFaEjuJEdfOcOcwuKEefTwCLcBGAsYHQ/s1600/Screen%2BShot%2B2019-05-06%2Bat%2B9.48.28%2BAM.png)
  
It allows developpers to significantly reduce, modularize and reuse code.
See [how a simple RecyclerView looks in Jetpack Compose]({% post_url 2020-11-03-jetpack-compose-basic-list %})

{: .box-warning}
**Warning:** All the API may change until full release planned in 2021

It's moving fast ! This is at a time a pro and a con.
On the one hand lot's of feature is already available and the community is impressive.
Even if something is missing in the library, it can be released very quickly. 
One the other hand, it's sure changes are expected before full release in 2021.

I think Compose will be in Android ecosystem as important as the move from Java to Kotlin back in years.

## TL;DR

Since couple of years, android developpers have choices between severals libraries/manners to build their UI. 

If you are starting from scratch and if using Compose before full release does not scare you, it may be conceivable 
to just use Compose. 
You can also use compose for some parts of the application as you can read it [here]({% post_url 2020-11-02-migration-jetpack-compose %}).

In other cases, the current recommendation is to go with ViewBinding. 
The migration is very easy and there are only pros to use it (fast, null and type safe, supports Java and Kotlin).

In any case you should forget about Kotlin Android extensions because Jetbrains deprecated it in 1.4.20-M2.

And you, will you try compose, stay with the strong ViewBinding or maybe you prefer the traditionnal findViewById ?
