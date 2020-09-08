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

```
Computers are not magic  🔗︎
At core, computers are built on a set of (mostly) 
deterministic foundations, which follow strict rules 
at each tick of the clock. We built layers upon layers 
of abstractions upon those foundations, each of which, 
as well, behaves in a (mostly) reproducible and 
deterministic way based on the abstractions at the previous level.

There is no magic. There is no layer beyond which 
we leave the realm of logic and executing instructions 
and encounter unknowable demons making arbitrary 
and capricious decisions. Most behaviors in one layer 
are comprehensible in terms of the concepts of the 
next layer, and all behaviors can be understood by 
digging down through enough layers.

Source, documentation, and reverse-engineering 
In modern computer systems, a great many of the 
layers are open-source, and can be understood 
directly by reading the implementation. For a developer 
working on a Ruby on Rails app running against a 
MySQL database and deployed to a Linux server, 
every relevant piece of software involved is 
open-source and can be read if needed.

When systems aren’t open-source, often there is 
deep and carefully-written documentation; in the above 
hypothetical system one of the first closed-source 
layers we will encounter is the hardware itself, 
likely a modern x86 processor. Intel makes available 
thousands of pages of documentation about their 
processors’ interface that do an excellent job of 
exhaustively exploring virtually every detail of 
their hardware’s behavior while executing code.

When source and documentation are unavailable or 
insufficient, systems can still be reverse-engineered 
via experiment and inspection by a sufficiently-determined 
engineer. Often, someone else has beat you to it and 
their results are available for you. Security engineers 
tend to be the most practiced at this particular skill; 
two of my favorite examples are Google Project Zero’s 
reverse-engineering the Haswell microarchitecture’s 
branch predictor, and the various efforts by security 
engineers to reverse-engineer and document macOS 
internals, such as this document on the WebKit heap in Safari.

Those two examples are massive efforts conducted by 
engineers at the top of their field with years of experience. 
I don’t mean to imply that I could perform those 
reverse-engineering projects anywhere near as efficiently. 
For me, though, their existence proves (1) that this work 
can be done if I wanted to badly enough and (2) often 
I don’t have to do it myself, if it has been done already 
and published.
```
计算机并不是魔术  
最核心的，计算机是构建在一个确定性集合的基础设施之上。这些基础设施遵循  
严格的规则，每一个时钟都是如此。我们在这些基础设施之上构建了一层又一层的抽象层，  
这些构建在前一层之上的抽象层次，其行为都是可复制以及确定性的。  
计算机并不存在魔术。这些层次，没有一个是我们离开了逻辑领域去执行指令  
并且导致了任意性的决定(即所有的计算机指令都是确定性和有逻辑的)。  
就下一层级而言，某个层级的绝大部分行为，都是可以被人理解的。所有的行为，只要   
深入足够多的层级，都是可以被理解的。  
在现代计算机系统当中，许多层级都是开源的，通过阅读源码就可以直接理解。  
对于一个需要使用mysql数据库，需要将rails app部署在linux服务器上的ruby开发者，  
他所使用的每一个软件都是开源的，如果需要，就可以去阅读。  
当系统不是开源的，那通常就得有一个深入的并且详细编写的文档，在上边那个假想的系统当中，  
我们遇到的第一个层级就是硬件自身，比如x86 cpu。intel写了数以千计的文档来描述cpu的   
接口，用于在执行代码时将每一点cpu的虚拟能力都物尽其用。   
当这个系统既不是开源也没有文档的时候，系统仍然可以被逆向工程--工程师只要通过足够多的实验，  
就可以达到这个目的。经常性的是有黑客破解了你的系统，并且给你分享了他们的结果。  
关于这个特殊技能，安全工程师是最有经验的。我最喜欢的2个例子是谷歌zero实验室的2个例子。  
这两个例子是由具有多年经验的高级工程师在其领域内做出的巨大努力才完成的。我并不是指   
我可以在任何领域都这么有效率的做逆向工程。对我而言，他们证明了:   
1. 如果足够需要，逆向工程是可以完成的；  
2. 如果已经完成并公开了，通常我自己就不需要做了。  

```
Understanding your dependencies 
Perhaps the most direct manifestation of this mindset is that 
it leads me — and people who share something like this mindset — 
to spend time learning more about the systems they depend on, 
and how they work and how they are implemented. If I’m writing 
a non-trivial application against a library or framework, 
I almost always have a checkout of that library’s source 
code on my laptop, and will regularly dig into it if I need 
to debug a strange behavior, or find that the documentation 
doesn’t answer a question I have.
```
理解你的依赖关系  
或许这是这个理念对我最直接的影响。花更多的时间在依赖系统之上，理解它们是怎么work的，  
他们是怎么实现的。如果我正在写一个牛逼的东西依赖一个库或者框架，我会经常把  
这个库或者框架的代码下载到电脑上，如果遇到了一个奇怪的行为，或者是文档对于某些问题没有答案，  
我就会跟进去调试。  

```
Debugging
Having this habit and knowing a lot about my dependencies 
has definitely been a superpower for debugging tricky bugs. 
If you work with any tool long enough, you will butt up against 
bugs in the tool which affect you, and it’s valuable at a minimum 
to be able to accurately describe and diagnose them in terms of 
the tool’s abstractions, in order to produce an actionable bug 
report or a minimal reproducer.

The trickiest bugs are often those that span multiple layers, 
or involve leaky abstraction boundaries between layers. 
These bugs are often impossible to understand at a single layer 
of the abstraction stack, and sometimes require the ability 
to view a behavior from multiple levels of abstractions at 
once to fully understand. These bugs practically require 
finding someone on your team who is comfortable moving 
between multiple layers of the stack, in order to track down; 
on the flip side, to the engineers with the habit of 
so moving around anyways, these bugs often represent an 
engaging challenge and form the basis of their favorite war stories.

One of my own favorite war stories of this genre was tracking 
down and identifying a single-bit memory flip on my desktop. 
This kind of problem can’t even be fully understood without 
a good understanding of the interplay between userspace 
libraries, the kernel, the filesystem, and the hardware. 
My debugging war-story tumblr has a number of other great examples.
```
调试   
拥有这个习惯，以及非常了解软件的依赖，成为调试那些很难的bug的利器。  
如果你对于某些工具很有经验，就会避免工具中影响你的bug，然后就可以使用工具去  
准确的调试和描述bug，也可以用于复现bug  
最扯淡的bug，一般都是垮了好几个层级的，也包括跨越抽象层级的抽象边界的那种。  
这些bug如果只懂得一个抽象层级的话是无法理解并搞定的。并且有一个bug需要一次看透   
好多个层级才能完全理解。这些bug就需要puppy这样的同学(对多个层级都能够完全理解)    
才能深入调试。另一方面对于更换方向的程序员来说，这些bug代表着充满挑战，同时也是他们  
最喜欢的战争故事(没看懂原文，大概意思就是具有有人喜欢这些挑战性的bug)  
我最喜欢的一个分析bug的文章(https://blogs.oracle.com/linux/attack-of-the-cosmic-rays-v2)  
这种类型的bug，必须得对用户层、kennel、fs、硬件都特别了解，才能搞定。