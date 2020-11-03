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

Note the only new `Window` that is making it magic. All the rest is basic Compose.

~~~
import androidx.compose.desktop.Window

Window { ... }
~~~
 
![](assets/img/jetbrains-compose-starter.gif)

## My previous example with list

Let's copy the example of a [basic list in compose]({% post_url 2020-11-03-jetpack-compose-basic-list %})

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

![](assets/img/jetbrains-compose-list.gif)
