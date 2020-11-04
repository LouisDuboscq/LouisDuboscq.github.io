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

Note the only new `Window` keyword that is making it magic. All the rest is basic Jetpack Compose.

~~~
import androidx.compose.desktop.Window

Window { ... }
~~~
 
![](/assets/img/jetbrains-compose-starter.gif)

## My previous example with list

Let's copying the example of a [basic list in compose]({% post_url 2020-11-03-jetpack-compose-basic-list %}) . 
It's just copying / reusing in same codebase all the UI composable functions.

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
 
## Under the hoods 

Jetbrains Compose is based on [skiko](https://github.com/JetBrains/skiko), a Jetbrains library 
which is powered by Kotlin Multiplatform. 

Compose on desktop is available on Windows, mac OS, Chrome OS and surely other platforms.

I can't wait to see the evolution of this amazing technology !
