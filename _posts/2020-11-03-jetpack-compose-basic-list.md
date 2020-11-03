---
layout: post
title: What's the equivalent of RecyclerView in Jetpack compose ?
subtitle: Productivity, clean, readable, maintanable, reduces bugs
tags: [android, android-jetpack-compose]
comments: true 
---

Let's start simple with a basic list of String items. How to do the old way and what's Jetpack compose manner.

![](/assets/img/recyclerview.gif)
 
## RecyclerView and adapter

Here you have to bind the recycler view, setup layout manager for triggering onBindViewHolder and getItemCount, 
create Adapter and finally write xml layouts for recycler view and its inner items.

{% gist 666792f1292c515f2b6071757f5027dc %}  

{% gist 9df7b75006e810224097c43b99931bbe %}  
  
{% gist f193885f1d5efaf8ca23fd47d20b0a99 %}  

{% gist 515b64e48dc6b548a80266e39c94919b %}  
 
## Jetpack compose

With Compose, simply create a function with @Composable. 
Use a LazyColumnFor, pass data and create your inner items in LazyItemScope.

{% gist 0b4a325e740f9ca88bc82d7e0e2d2e0c %}  
 
That's all.
This example with list may be the most significant where Jetpack compose shines.

You understand that Jetpack compose is not only a cool tool for developpers. 
It's also about productivity 🚀, clean, readable and maintanable code.