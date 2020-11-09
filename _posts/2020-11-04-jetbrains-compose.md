---
layout: post
title: Desktop application with Jetpack Compose
subtitle: Cross-platform future
tags: [kotlin, kotlin-multiplatform, jetpack-compose]
comments: true 
---

We live exciting moments !

No I'm not talking about lockdown or election day but the amazing news that Jetpack Compose 
on desktop is now accessible on EAP version of Intellij IDEA.

Have a look on what it is and how to use it. 

## Sample template

When we launch Intellij IDEA, a sample template is provided for taking your first step with Compose on desktop. 

~~~
fun main() = Window {
    var text by remember { mutableStateOf("Hello, World!") }

    MaterialTheme {
        Button(onClick = {
            text = "Hello, Desktop!"
        }) {
            Text(text)
        }
    }
}
~~~

Note there is only a new `Window` keyword that is making it magic. All the rest is basic Jetpack Compose.

~~~
import androidx.compose.desktop.Window

Window { ... }
~~~
 
![](/assets/img/jetbrains-compose-starter.gif)

## My previous example with list

Let's see how to port in desktop the example of a [basic list in compose]({% post_url 2020-11-03-jetpack-compose-basic-list %}) . 
It's just reusing all Android composable functions.

~~~
fun main() = Window {
   var text by remember { mutableStateOf("Hello, World!") }

   MaterialTheme {
       ListComponent((0..100).map { "item$it" })
   }
}

@Composable
fun ListComponent(dataset: List<String>) {
   LazyColumnFor(items = dataset) { item ->
       Text(text = item, modifier = Modifier.padding(8.dp))
   }
}
~~~

![](/assets/img/jetbrains-compose-list.gif)
 
## Little bit more complicated UI

I made this UI on desktop, this is just an UI and there is no feature. 
It was inspired by [this dribble](https://dribbble.com/shots/14511340-Landing-UI/attachments/6197391?mode=media).

![](/assets/img/compose-desktop.png)

You can find the code [here](https://gist.github.com/LouisDuboscq/dc14c0fae5ecebe2490f26bbc7b26129).
  
## Conclusion

Under the hood Jetbrains Compose is based on Skia and it seems that the next compatible platform could be iOS, it would be awesome.

Compose on desktop is already available on Windows, Linux and mac OS.

Jetbrains just announced [Milestone 1 released](https://blog.jetbrains.com/cross-post/jetpack-compose-for-desktop-milestone-1-released/) and they said that more effort will be put on Kotlin multiplatform in near future.

I can't wait to see the evolution of this amazing technology !
  