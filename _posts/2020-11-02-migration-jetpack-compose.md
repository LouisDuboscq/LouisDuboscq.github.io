---
layout: post
title: Jetpack compose
subtitle: New Android UI Toolkit
tags: [android-jetpack-compose]
comments: true 
---
 
## Migrate an Android project to Jetpack compose

# Interoperability with existing codebase

{: .box-error}
**Error:** There's at the time an error if your project contains Kotlin synthetics, 
the issue is reported on [IssueTracker](https://issuetracker.google.com/issues/166927559)

At the time I have those versions :

- 1.0.0-alpha06 for Jetpack compose
- 1.4.10 for Kotlin

~~~
e: java.lang.AssertionError: Unbound symbols not allowed
    Unbound public symbol for public kotlinx.android.synthetic.
~~~

If your UI codebase is not too important you can replace all Kotlin synthetic with [ViewBinding](https://developer.android.com/topic/libraries/view-binding) or old findViewById. 
I did this on a small application and everything worked.

If not, you have to wait the [issue shipped in Kotlin 1.4.20](https://github.com/JetBrains/kotlin/pull/3726)