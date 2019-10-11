---
layout: post
cover:  assets/images/babysteps-c-prog.jpg
navigation: True
tags: [C, Programming, Learning]
class: post-template
author: bauripalash
---

**C** is one of the most used Programming languages till date. It is one of the most powerful language and mother of many modern Programming language (e.g., Python, Ruby)

![](https://media2.giphy.com/media/fnD9cHHIrYRYk/giphy.gif)
[©giphy](https://giphy.com)
{: .crtx}


🍭 C is a compiled language, unlike [Python](https://python.org) or [Ruby](https://www.ruby-lang.org/en/), C programs must be translated from human-readable code to machine-readable code.

>  The program which translates human-readable C code to machine-readable code is called a compiler


> You'll Be Astonished to know that the most [Compilers](https://en.m.wikipedia.org/wiki/Compiler) of C (e.g., GCC) is also written in C

You'll find people who say C is so hard, but I say nothing is hard; it just needs a good teacher to explain everything.

So without further talking, let's take our first step in the world of C Programming.

## Setting Up Workspace

As I mentioned earlier, C is a compiled language, so you need a compiler such as GCC to compile C programs.

Today we'll be using Repl.it to Compile and Run C programs online.

If you want to run and compile C Programs in Your local device [Read This Article](https://www.tutorialspoint.com/cprogramming/c_environment_setup.htm)

To Run and Compile C programs online without installing anything, Use [REPL.it](https://repl.it/languages/c)

When Opening Repl.it, you'll see a sample program is already written in the left pane. Clear it first.


## Writing Traditional Hello World

As I mentioned earlier, Hello World is a traditional program that every programmer Writes at first when learning a new language. Which just prints **Hello World** text in a console window

Hello World program in C is a bit longer than Python or Ruby.

Let's Write

{% highlight python %}
#include<stdio.h>

int main()
{
    printf("Hello World\n");
    return 0;
}
{% endhighlight %}

Write the above code in the left pane of repl.it or if using Local device, write the above script in a file called **hello.c** and execute the command in terminal

` GCC -o hello hello.c.`

If you're in repl.it click the **Run ** button and if on local device execute this command

`./hello`  if on a Linux or Mac Device
Or
`hello` on MS Windows Device

If everything is fine, you'll see a **Hello World** text in console/terminal. 

![](https://2.bp.blogspot.com/-XZzF3zjKqLI/VHs78mMe7SI/AAAAAAAACHE/T4Vk3REwaaI/s1600/Hello_world.jpg)[©cprogramsbasics.blogspot.com](http://cprogramsbasics.blogspot.com/2014/11/first-c-program-hello-world.html?m=1)
{: .crtx}

If there's any problem, feel free to let me know in the comments bellow 👇

Otherwise, Let's Go To The Next Chapter

## Understanding The Hello World Program

Writing code without understanding it is really useless. Copying-Pasting will not work forever.
So, Let's Try to Understand The Above Code.

Let's Try To Understand From First Line

{% highlight c %}
#include<stdio.h>
{% endhighlight %}

It includes instructions for C compiler and the definition of `printf,` this is like a dictionary for a C Compilers, from this Compilers know what to do with `printf`

Let's Step in the next line. We'll find this,

{% highlight c %}
int main()
{% endhighlight %}

`int` is the acronym of integer.

Here` main()` is a function; everything inside a function is taken as instructions. From this, our program knows what to do. There may be other functions, but `main()` is a special function, in every program, this function is executed first.

And this `()` parentheses help Compilers identify that it is a function.

Functions are like a jar, which contains some special instructions on what to do.

In the next line, we'll find `{` a curly brace. It denotes the beginning of a function. It's like the lid of a jar.

In the next line, we'll find

{% highlight c %}
printf("Hello World");
{% endhighlight %}

`printf` is also like a function but pre-defined; things inside its quotation marks will be written in. Console window when we'll run our program.

Parentheses `()` denotes the beginning and ending of the `printf` function. 

We see a Text, `Hello World\n` inside quotation marks this is the text which will be written in console window, and at the end, there's a `\n` which tells our program to start a new line and put the cursor in the new line.

> Try changing the text and running it

It's not necessary, but it is necessary when working with a program which needs to print two or more lines. But you should keep it as a good practice.

> You'll see a semicolon `;` at the end of line, it's not for style, it's necessary, it helps compiler to understand that this line is ended now.

in the next line, we'll find

{% highlight c %}
return 0;
{% endhighlight %}

which is not actually for us, but for machine, it returns 0 to the machine, and that's how machine understands that the program ran successfully and now ending.

> If a program returns a number other than, Computer will think that it has not run successfully. Try Changing it and running it.

And finally, at the end,`}` ending curly brace denotes that our main function is ended.

So, guys, that's for now, if you've any questions or find any problems, please let me know in the comments below. 👇

Thank You
