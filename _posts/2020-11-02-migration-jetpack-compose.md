---
layout: post
title: Tips for a bug while migrating to Jetpack compose
subtitle: AssertionError: Unbound symbols not allowed
tags: [android, android-jetpack-compose]
comments: true 
---
 
Was migrating an existing project to Jetpack compose and what.. Already an error...
 
If you don't know what compose is, you can have an 
[overview reading this]({% post_url 2020-11-01-android-ui-history %}).
 
{: .box-error}
**Error:** There's at the time an error if your project contains Kotlin synthetics, 
the issue is reported on [IssueTracker](https://issuetracker.google.com/issues/166927559)

For now, the most updated versions are :

- 1.0.0-alpha06 for Jetpack compose
- 1.4.10 for Kotlin

~~~
e: java.lang.AssertionError: Unbound symbols not allowed
    Unbound public symbol for public kotlinx.android.synthetic.
~~~

If your UI codebase is not too important you can replace all Kotlin synthetic with [ViewBinding](https://developer.android.com/topic/libraries/view-binding) or old findViewById. 
I did this on a small application and everything worked.

If not, you have to wait the [issue shipped in Kotlin 1.4.20](https://github.com/JetBrains/kotlin/pull/3726)