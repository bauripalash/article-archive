<!---
layout: post
cover:  assets/images/conandroid.png
title: Run C Programs on Android - C for Android
navigation: True
tags: [Programming, Android]
class: post-template
author: bauripalash
--->
#Run C Programs on Android - C for Android
C is a well known Programming language Created by [Dennis Ritchie](https://en.m.wikipedia.org/wiki/Dennis_Ritchie) between 1969 and 1973 at [Bell Labs](https://en.m.wikipedia.org/wiki/Bell_Labs), since then it has become one of the most widely used Programming Language of all time. 

It is usually used for low level Programming such as developing [Operating Systems](https://en.m.wikipedia.org/wiki/Operating_system), [Drivers](https://en.m.wikipedia.org/wiki/Device_driver), well as various [application software](https://en.m.wikipedia.org/wiki/Application_software) for computers ranging from [supercomputers](https://en.m.wikipedia.org/wiki/Supercomputer) to [embedded systems](https://en.m.wikipedia.org/wiki/Embedded_system).

The language has become available on a very wide range of platforms, from embedded [microcontrollers](https://en.m.wikipedia.org/wiki/Microcontroller) to [supercomputers](https://en.m.wikipedia.org/wiki/Supercomputer).

![The C Programming](https://upload.wikimedia.org/wikipedia/commons/thumb/3/35/The_C_Programming_Language_logo.svg/452px-The_C_Programming_Language_logo.svg.png)


> Android is based on Linux Kernel so it's definitely possible to compile & run C/C++ programs on Android.

C is quite [cross-platform](https://en.m.wikipedia.org/wiki/Cross-platform) , so a C Program written in Windows can Run on Linux ( and android ) and vice versa.

> Special Note : You might be wondering why i included [C++](https://en.m.wikipedia.org/wiki/C%2B%2B) where we should be only focusing on C.
The Reason is, C++ was actually developed as a superset of C Programming Language, and nowadays nobody builds a [compiler](https://en.m.wikipedia.org/wiki/Compiler) specific for only C. So a compiler for C can also compile C++ programs

### If You're New To C Programming or want to start learning C Programming , i recommend reading our article, [Baby Steps in C Programming](https://palash.tk/Baby-Steps-In-C-Programming)

So With Further Talking Let's Jump into to find ways to run C/C++ Programms in Android

## #1 CXXDroid

Developed by IIEC, CXXDroid is fully fledged C/C++ IDE for Android. It has quite powerful features listed below

* Full Offline Compiler  - No Internet Needed
* Package Manager available to get libraries
* Powerful Editor
* C/C++ interpreter (REPL)
* Code Examples

![CXXDroid - Run C programs on Android](https://fsgh.palash.tk/imgs/cxxdroid.jpg)

CXXDroid From Play Store
{: .crtx}

If you want to learn and experiment with C/C++ , I recommend using CXXDroid.

#### Install From : [Play Store](https://play.google.com/store/apps/details?id=ru.iiec.cxxdroid)

## #2 CppDroid

Developed by Anton Smirnov, CppDroid is a quite famous and well known C/C++  IDE for Android , it's robust and reliable which has many features, 

* Full Offline C/C++ compiler - No need of internet
* Smart Syntax Highlighting
* Auto Indentation
* Themes

![CppDroid - Run C & Cpp programs on Android](https://fsgh.palash.tk/imgs/cppdroid.jpg)

CppDroid from Play Store
{: .crtx}

If you want a full C/C++ Development workspace , I recommend using CppDroid. 
But right Now there's one down point about it, It's not been updated in Play Store since 17 August,2017

#### Install it From : [Play Store](https://play.google.com/store/apps/details?id=name.antonsmirnov.android.cppdroid)
Visit Their Official Website : <https://www.cppdroid.info>

## #3 Termux

Termux, the all-in-one solution which was also mentioned on our previous article , [Python For Android - Run Python Programs in Android](https://palash.tk/Python-For-Android-Run-Python-Programs-In-Android)

As also mentioned in previous article, it's a terminal emulator for Android which means with help of it we can run any linux (almost any 😉) programs on Android.

![editing C scripts in vim](https://termux.com/files/vim-main_framed.png)

termux.com
{: .crtx}

To Install and Use C/C++ compiler in Termux (in Termux clang is the C/C++ compiler) , 

1. Download & Install Termux from :  [Play Store](https://play.google.com/store/apps/details?id=com.termux)
2. After Installing execute this command `pkg install clang`
3. After Successfully installing `clang`  you can compile C/C++ scripts.

 Example :
`clang hello.c`
After you'll get an executable `a.out` which you can run using `~$./a.out`

> To edit and create C/C++ Scripts you can use [**VIM**](https://en.m.wikipedia.org/wiki/Vim_(text_editor)) inside termux which can be installed with `pkg install vim`
Or, you can use  [QuickEdit](https://play.google.com/store/apps/details?id=com.rhmsoft.edit) 


If you're new to the world of programming and never used Command Line Applications I wouldn't recommend you to use Termux , use **CXXDroid** or **CppDroid** instead.

So Friends That's It For Now, See You Next Time. Have and Questions , Suggestions? Let me know the comments below 👇

If you like my writing and articles , consider [Buying Me a Coffee](https://buymeacoff.ee/palash) ☕