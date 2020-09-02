 原文链接(https://blog.nelhage.com/post/computers-can-be-understood/)  

```
Introduction
This post attempts to describe a mindset I’ve come to realize 
I bring to essentially all of my work with software. 
I attempt to articulate this mindset, some of its implications 
and strengths, and some of the ways in which it’s lead me astray.
```
这个帖子在描述一种概念。这种概念我是将它带到了所有跟软件系统相关的工作当中的。  
我会尝试去清晰的描述这个概念。包括它的一些应用和好处，以及某些让我上道的方式。  

```
Software can be understood
I approach software with a deep-seated belief that computers 
and software systems can be understood.

This belief is, for me, not some abstruse theoretical assertion, 
but a deeply felt belief that essentially any question I might 
care to ask (about computers) has a comprehensible answer which 
is accessible with determined exploration and learning.

In some ways, this belief feels radical today. Modern software 
and hardware systems contain almost unimaginable complexity 
amongst many distinct layers, each building atop each other. 
It is common — and substantially correct — to observe that no 
single human understands all of the layers in, say, a modern 
web application, starting from the transistors and silicon up 
through micro-architecture, the CPU instruction set, the OS kernel, 
the user libraries, the compilers, the web browser, 
and Javascript VM, the Javascript libraries, 
and the application code, not even to mention all the network services 
invoked in loading that code.

In the face of this complexity, it’s easy to assume that 
there’s just too much to learn, and to adopt the mental shorthand 
that the systems we work with are best treated as black boxes, 
not to be understood in any detail.

I argue against that approach. You will never understand every 
detail of the implementation of every level on that stack; 
but you can understand all of them to some level of abstraction, 
and any specific layer to essentially any depth necessary for any purpose.
```
软件是可以被理解的  
我对计算机和软件是可以被理解这件事深信不疑。简单的对我来说，并不是什么高深的理论的断言，  
而是一种深深的信念：所有涉及计算机本质的问题，都会有一个可以简单理解的答案，只要有决心  
和学习，就可以找到相关的答案。  
在某种意义上说，这种新年今天看起来有点疯狂。现代软件和硬件系统，在每一个分层系统里，  
都包含了难以想象的复杂性。每一层都构建在另一层之上。这很正常，并且本质上是正确的。  
观察到没有一个人能够理解所有的层级，也就是说，一个现代的网络应用，是建立在晶体管、  
硅，CPU指令集、os kernel、用户态应用、编译器、浏览器、js vm、js 库和应用代码，甚至说  
都没有提及加载这些代码的网络服务了。  
面对这个复杂性，很容易就能知道有太多的东西要学习，并且为了匹配心智速度，我们工作的这些系统  
最好都是一个黑盒，这样不用理解其任何细节。  
我反对这种态度。的确你不可能把计算机世界的每一个层级的细节都了解清楚，但是你可以在某种  
程度的抽象之上，全部理解它们。并且，如果需要的话，可以在任何特定的层级去深入的理解。  
