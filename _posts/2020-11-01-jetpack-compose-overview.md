---
layout: post
title: Jetpack compose
subtitle: Overview of the new Android UI Toolkit
tags: [android-jetpack-compose]
comments: true
---
 
Jetpack compose is the new thrilling UI toolkit for Android applications. 
Alpha has been released in august 2020 and a full release is expected for 2021.
Let's see what is the landscape of UI Android Development, why use compose and what we can or can't do with this.

## Another migration ? 

Before diving into Jetpack compose, let's just see what was the evolution of Android UI this last years.

Did you remember this 👻 from the past ? 
 
~~~ 
private TextView mFirstName;
private TextView mLastName;

@Override public View onCreateView(LayoutInflater inflater, ViewGroup container, Bundle savedInstanceState) {
    View view = inflater.inflate(R.layout.profile_fragment, container, false);
    mFirstName = view.findById(view, R.id.first_name);
    mLastName = view.findById(view, R.id.last_name);
    return view;
}
~~~
Java 7 + old findById way

**Java and findById ! I didn't miss you 🙅‍♂️**

Around 2016 : Android developpers used to import Butterknife, this awesome library which avoided all the UI boilerplate. 
You also could bind strings, dimensions, colors. It was 👌 at the time but it still lacks compile time safety

~~~
@BindView(R.id.first_name) TextView firstName;
@BindView(R.id.last_name) TextView lastName;

@Override public View onCreateView(LayoutInflater inflater, ViewGroup container, Bundle savedInstanceState) {
    View view = inflater.inflate(R.layout.profile_fragment, container, false);
    ButterKnife.bind(this, view);
    return view;
}
~~~
Butterknife way

Next ViewBinding, DataBinding, Kotlin and Kotlin synthetics arrived about the same time.

~~~  
override fun onCreateView(
    inflater: LayoutInflater,
    container: ViewGroup?,
    savedInstanceState: Bundle?
): View? {
    binding = ProfileBinding.inflate(inflater, container, false)
    val view = binding.root 
    return view
}
~~~
ViewBinding way

**Note the Kotlin language and the Jetpack Lifecycle-Aware Components**
 
~~~  
override fun onCreateView(
    inflater: LayoutInflater,
    container: ViewGroup?,
    savedInstanceState: Bundle?
): View? { 
    return inflater.inflate(R.layout.profile_fragment, container, false)
}

override fun onViewCreated(view: View, savedInstanceState: Bundle?) { 
    firstName = viewModel.firstName
    lastName = viewModel.lastName
}
~~~
Kotlin synthetic way

Kotlin synthetic is heavily used in Android modern applications because it is really elegant version of findViewById, 
it has good performance but it lacks compile time safety.
 
You can now ask yourself why the hell I need to change again ?

## Why Jetpack compose

It combines declarative API for building UI and reactive programming model.
 
The way to build the UI are intuitive :

![](https://1.bp.blogspot.com/-cxPO9bE5QT4/X0Vw6rOOAAI/AAAAAAAAPjg/UmpOu9X6wHMUFaEjuJEdfOcOcwuKEefTwCLcBGAsYHQ/s1600/Screen%2BShot%2B2019-05-06%2Bat%2B9.48.28%2BAM.png)
  
  
    
Strength and honor to those who made all these moves : findView -> Butterknife -> ViewBinding / DataBinding -> Kotlin Synthetic and next Jetpack compose 

![](https://i.ytimg.com/vi/3uKemgoWFlI/maxresdefault.jpg)

~~~
@Composable
fun Greeting(name: String {
    Text("Hello $name"
}
~~~

{: .box-warning}
**Warning:** All the API may change until full release planned in 2021