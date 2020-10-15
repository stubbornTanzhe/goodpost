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

```
Documentation 
Willingness and skill for reading source reduces your 
reliance on documentation. If the documentation is lacking 
in some way, you can always go to the source and look at 
the implementation for an authoritative answer.

The ability to answer questions this way is powerful to 
have on a team, since even the best documentation tends 
to have holes. It also has a downside, though; the engineers 
I’ve worked with (including myself) who are the most 
comfortable reading unfamiliar code bases are at risk of 
habitually undervaluing documentation (since they have 
gotten good at getting answers without it), and can be 
even worse at documenting their own system than the median engineer.
```
关于文档  
阅读源码的意愿和技能会降低你对文档的依赖。如果文档某种意义上缺实的话，  
你总是可以通过阅读源码来得到第一视角的答案。  
在团队中这个回答问题的能力实在是很牛逼，因为最好的文档可能都有漏洞。  
不过这也有一个缺点，就是，我合作过的最喜欢阅读不熟悉源码的人，  
都不太重视文档，因为他们很善于通过源码得到答案，在写文档方面，  
比中庸的工程师还要糟糕。(译者:大师总是这样啊)  

```
Security 
Understanding security issues very often requires 
working at multiple levels of abstraction. An attacker 
attacking a system isn’t bound by the documented or 
intended behavior of any layer; she cares about how 
the system actually behaves in practice, potentially 
including when one layer or input is “out-of-spec.” 
The C specification says only that a buffer overflow 
is “undefined behavior”; understanding how to turn 
one into remote-code-execution, or reasoning about 
countermeasures like ASLR or DEP requires a deep 
understanding of the actual implementation of the 
abstract C specification by the compiler, libc, 
underlying hardware, and more.

I started my career substantially in security, 
while working at Ksplice, which sold zero-downtime 
software updates for the Linux kernel, primarily as 
a security feature. I learned a lot of my current 
skill and comfort with digging deeper into the 
stack and understanding all the layers of abstraction 
while spending time around a lot of security bugs there.
```
安全  
理解安全问题，通常需要许多抽象层级的经验。一个骇客攻击一个系统，不是  
按照文档的边界，或者是层级的行为来攻击的；她会关注系统实际运行表现，  
对于某些层级或者输入，潜在的非安全性的东西。C语言的标准里只说了缓冲区溢出  
是一个未定义的行为，如果要理解远程代码执行，或者找到ASLR/DEP的加密对策，  
需要对于C语言的标准、编译器、libc、硬件等更多的东西深入理解。  

```
Performance 
Understanding and reasoning about software performance 
also often involves understanding multiple layers of 
your stack. It’s hard to write efficient Python code 
without some understanding of the CPython (or PyPy) 
implementation, and you can’t write cache-efficient C code 
without some understanding of the generated code and the 
underlying hardware. Dig into a crowd of performance engineers, 
and you’ll virtually always find a handful of engineers with 
the habit of always digging deeper to continually better-understand 
ever-more layers of abstraction.
```
性能  
理解和找到软件性能表现的原因，同样需要很深的技术栈。  
如果不懂CPython或者PyPy的话是不会写出很高效的python代码的。  
如果不理解代码的生成以及底层硬件，也不会写出缓存效率的C代码。  
如果与性能工程师混在一起，你会就基本上会遇到一群特别实用的工程师，  
因为他们的习惯是挖的很深所以就能够更好的理解以及更深的理解层级内部。  

```
Building mental models 
A deeply related habit to trying to learn about the underlying 
layers of a software stack is the habit of trying to understand 
software by building detailed mental models of the underlying 
system. Instead of understanding systems (languages, libraries, 
APIs, etc) solely as collections of rules and behaviors and 
edge-cases, I try to build a smaller model of their core 
primitives, and the rules or principles that generate the 
larger behaviors of the system.

As a concrete example, I’ve written more bash shell scrips 
in my life than I should perhaps be proud of. At some point, 
instead of continually memorizing specific patterns and 
anti-patterns that happen to work or not work (when do you 
or don’t need to quote something?), I stepped back to read 
the bash documentation in order to understand the various 
expansion phases that bash follows when processing a 
command line, and which ones are applied in which order 
in which context. This knowledge didn’t eliminate the 
need to learn a ton of trivia to write shell scripts — 
arguably, it added more trivia — but having a framework 
to fit knowledge into both made it easier to retain that 
trivia, and increased its explanatory power in the face 
of novel problems or patterns of code.

I think there’s a related belief here which ties into 
and is reinforced by the basic belief that computers 
are comprehensible: Computer systems tend to be, well, 
systematic, and have some core algebra or logic that is 
comprehensible, which is smaller than a complete list of 
possible behaviors, and which generates or at least 
organizes all of those behaviors. And, as an addendum, 
I tend to believe that work invested in learning these 
underlying systems will pay off in terms of understanding 
and working with the system.
```
构建思维模型  
一个很好的学习底层知识的习惯，就是构建底层知识的思维模型。  
不只是要把系统(编程语言、库、api等等)当成一种规则、行为和特殊case的集合，  
还需要去构建一个核心原语组成的模型。这个模型可以生成更大的系统  
（我理解就是计算机底层的思想，处理问题的思维模型）  
举个具体的例子，我写过很多bash脚本。  
某些时候，记住一些特定的脚本套路，或者反脚本讨论，我很少做。  
我深入阅读了bash文档，了解了bash脚本在执行一个命令行的时候是  
如何真正去执行的，按照什么顺序，依赖了什么上下文，以及它展开的策略。   
这个知识呢，并不会避免写shell脚本的各种细节，也许反而还增加了一些琐碎的东西。  
但是会让你得到一个知识的框架（framework），让你能够很轻松的维护这些琐碎的细节，    
(降低程序员的心智负担吧)并且面对新问题，能够让你更快速的理解。  
我认为这里有一个相关的概念，并且它和"计算机是可以被理解"的概念紧密相关  
并且还进一步增强。再提一下，计算机是可以被理解的，是说，计算机系统，是具有逻辑+代数  
的一个系统，逻辑和代码是可以被理解的，它可能不会包含所有的逻辑和代数的行为，但应该具有大多数。  
同时会生成这些行为，至少是组织这些行为。  
然后，我觉得如果投入在学习基础知识层面，对于理解系统和使用系统很有好处，会得到回报。  

```
Single-shot debugging  🔗︎
As a corollary of having good mental models of software 
systems, and of those systems being mostly deterministic, 
it becomes possible to make fairly detailed inferences 
about program state and behavior off of a a small number 
of observations about its behavior at points in time 
(perhaps a stack trace, or a log line, or a core dump). 
In the most extreme examples, a developer can sometimes 
root-cause a buggy behavior based on a single encounter 
with a bug. With a rich mental model of the system and 
the code at hand, you can perform backwards reasoning 
in the form of deductions like “Ah, if this field is set 
to NULL, someone must have set it … the only code that 
sets that field is {here}, {here}, and {here} … only the 
first and third could ever be called with a NULL argument …” 
and so on.

Even if you can’t “one-shot” a bug, there’s a general skill 
here of being able to formulate theories and hypotheses and 
refine your mental models based on observations of the system, 
which allow you to ask much more specific questions, which you 
can then test (in a debugger, with a print statement, by reading 
code, …), which then further refine your models. A rich mental 
model and the ability to play it forward and backwards in time 
is an incredible aid to debugging and to learning a system.
```
单步调试  
这些系统具有良好的软件系统模型，并且觉有确定性，所以可以从较少的时间量上，  
通过调试软件，观察跟踪堆栈、日志或者是kernel的dump文件，来对于程序的状态  
和行为进行推断和预测。有时候开发者会因为遇到一个单纯的bug，找到系统bug根因。  
如果对整个系统模型有经验，或者是对代码很熟悉，你就会在找问题根因这种事情上  
经常会出现这样的对话:  
哦，如果这个地方被设置为了NULL，肯定是有人特定赋值的，    
并且赋值的代码位置肯定就是在这，这，以及这里。   
并且，只有第一个和第三个地方才会设置成NULL。  
(译者:会心一笑)  

甚至于说，也许你无法直接就找到bug原因，但是，你可以不断的从调试、跟踪、读代码  
或者是问特定的问题，在这些行为当中，提炼你对整个系统的理解，从而形成  
更通用的理论或者说是经验。如果对于这种软件模型的经验很丰富，并且从前往后都很熟练  
(或者翻译成倒背如流？)，会对学习整个系统帮助很大。  
(之前的经验是，对于一个庞大的系统，确实一个人无法完全掌握；但是对于一个特定的模块  
一个人如果可以熟练掌握，往往可以管中窥豹，明白整个系统的设计思路，这样即便在定位其他  
模块代码的时候也会很容易就找到问题原因)  

```
Single-shot debugging in kernel engineering 
The more complex and nondeterministic a system is, 
the harder it gets to reliably predict behavior from 
a small number of observations, which I think in part 
explains the modern trend of “observability” in distributed 
systems — you need much more data to fully explain these systems’ 
behaviors.

However, at the bottom of the stack, among systems 
engineers and especially kernel engineers, this skill 
set is widespread. I’ve seen threads on the LKML where 
a developer will post a single crash log with a stack 
trace and a register dump, and a handful of senior 
kernel lieutenants will collaboratively go on the hunt 
for the bug, making detailed inferences based on mapping 
between the register dump and the compiled code, and based 
on their understanding of all the places in the kernel that 
deal with the implicated data structures.

When I worked at Oracle (following the Ksplice acquisition), 
I talked with some Solaris kernel engineers there, and 
learned that they had taken this kind of approach even 
further. They apparently had an explicit goal of a 100% 
rate of root-causing kernel crashes based on a single 
crash report. In order to strive for this goal they had 
built a lot of elaborate crash-reporting and debugging 
technology — it wasn’t just raw thinking hard about bugs 
— but at root I think this goal comes from the deep 
belief that their system, while complex, is understandable 
and mostly deterministic, and that they have the ability 
to reason about it. I found this story pretty inspiring.

I think in many ways, kernel development is the prime 
audience for this mindset. For one, it’s not uncommon, 
especially a decade ago prior to our modern virtualization 
era, that your only ability to debug a kernel crash is 
by inspecting a crash dump or log trace — you may not 
have a debugger or even the ability to continue executing 
at all. And, for another, because the OS kernel is 
essentially the software closest to the hardware, 
the number of layers you have to understand to fully 
explain your code’s behavior and interactions is 
comparatively small. You (mostly) only need to 
understand your C compiler / compiled code, and the 
hardware itself. Anyone developing in userspace (atop the kernel) 
has strictly more layers to work through.
```
系统越复杂，不确定性越强，很难通过少量观察来可靠地预测行为，  
这在一定程度上解释了分布式系统中“可观察性”的现代趋势-  
需要更多的数据来充分说明这些系统的行为。  

但是，在系统工程师，尤其是内核工程师中，最底层的技能是广泛的。   
我已经看到了LKML上的线程，在该线程上，  
开发人员将发布带有堆栈跟踪和寄存器转储的单个崩溃日志，  
以及几个内核日志，来定位错误原因，并根据寄存器转储和编译后的代码之间的映射，  
以及基于他们对内核中处理隐含数据结构的所有位置的理解，    
来做出详细的推断。 (译者:内核工程师，牛逼..)   
当我在Oracle工作时（跟随Ksplice的收购），  
我与那里的一些Solaris内核工程师进行了交谈，并了解到他们进一步采用了这种方法。    
他们显然有一个明确的目标，那就是根据单个崩溃报告，    
就可以100%的找到内核崩溃的根因。  
为了实现这个目标，他们建立了许多精心设计的崩溃报告和调试技术-    
不仅仅是对错误的认真思考-   
但从根本上讲，我认为这个目标来自于人们的深信，    
即他们的系统虽然复杂，但是可以理解的，  
并且大多数是确定性的，并且他们有能力对此进行推理。  
我发现这个故事很有启发性。(译者:是的，对我也很有启发)  

我认为从很多方面来说，内核开发是这种思维方式的主要受众。   
首先，尤其是在现代虚拟化时代之前的十年，  
调试内核崩溃的唯一能力就是检查崩溃转储或日志跟踪  
可能没有调试器，甚至没有断点后继续执行的能力。    
另外，由于OS内核本质上是与硬件最接近的软件，因此  
能够完整解释整个系统的代码，其实相对来说是不太多的，  
或者说，需要了解的layer(上边提到的layer层级概念)，不会特别多。  
 （大多数）只需要了解C编译器/已编译代码以及硬件本身。  
 在用户空间（内核之上）进行开发的任何人都必须严格执行更多的工作层。    
(译者：其实看在哪一层看问题了，kernel主要是比较杂)

```
Pitfalls of this mindset 
I want to include a note here about the pitfalls of 
this mindset, and some places where I’ve observed it 
leading me astray. Overall, the belief in the fundamental 
comprehensibility of software, and the pursuit of 
detailed mental models has served me quite well, 
but I want to be clear that I don’t think it’s the 
only valid or useful approach, and that it comes with 
its own weaknesses.

The need to understand 
A belief in the understandability of software systems 
can very easily become a need to understand the 
systems you work with. I have become very uncomfortable 
working in software systems where I don’t have a good 
model of the underlying layers, and this discomfort can 
sometimes be harmful to accomplishing my goals.

I find it very hard to get started working with a 
complex system by just following a tutorial or two 
and performing small edits or local exploration out 
from that example. I am uncomfortable until I understand 
the roles and relationships of all the components I’m 
interacting with, at least at a high level.

Concretely, the other day I was attempting to stand 
up a single HTTP endpoint backed by Amazon Lambda 
(which I had never worked previously used). There are 
a million tutorials about this task, both from AWS and 
others. I’m quite confident that if I’d taken almost 
any of these and adopted it via trial-and-error I could 
have accomplished my task in something like 30 minutes. 
However, instead, I stubbornly insisted on starting 
from scratch and understanding each component I needed. 
Since performing any task on AWS involves stitching 
together approximately 15 different mind-numbingly-complex 
products, I soon ended up with 30 documentation tabs open, 
an endpoint that returned a server error no matter what 
I tried, and still no particularly better idea what the 
heck was going on. I eventually gave up and decided that 
the problem wasn’t that important to solve anyways.

I do believe that if I had had more time and patience, 
I would eventually arrive at a fairly deep conceptual 
understanding of Lambda and the adjacent AWS products, 
and be much better equipped to debug my deployment or 
solve future problems. However, that wasn’t my goal; I 
just wanted something that worked, within a time budget. 
And so, I instead just ended up without anything that 
worked, and without much of a better understanding of 
anything, either. The need to understand can be seductive 
and harmful when working atop a complex system, where 
your problem does not fundamentally require understanding 
the whole thing.

Do the easy thing first 
I’ve lost track of the number of times that, faced 
with a bug in a dependency, I’ve spent days digging 
deeply into the dependency in order to identify and 
isolate the bug … only to realize that the bug was 
already fixed upstream, and we were pinned to an older 
version. Or when I’ve spent time trying to debug a crash 
in a binary that was built without debug symbols, by 
carefully poring through a coredump and x86 disassembly, 
only for a coworker to find a debug build, reproduce the 
issue there, and traipse through the green pastures of a 
working gdb session1.

I have a particular set of software and systems skills, 
which happen to include binary reverse-engineering and 
rapidly coming up to speed on unfamiliar code bases. I 
have these skills in part because of my obsessive desire 
to understand the systems I work with. However, having 
these skills doesn’t mean they’re always the right skills 
to apply to a problem!

It’s nearly always worth trying the easier approach first 
(upgrading a dependency, reaching for the debugger, a few 
passes of trial-and-error cargo-culting from working examples), 
and only reach for the big guns if those tools fail you.
```
这个心智模型的一些陷阱  
首先是理解的必要性  
如果你接受了这个理论，就得去对你工作的这个软件系统，先有一个模型的理解。  
如果对于这个模型不理解，可能就会觉得很不爽，以至于说对于完成一些特定的任务时，  
会结果达成会有影响。    
我会发现如果我不懂这个系统，或者说只是完成一个初学者的学习，即便是改一些很小的地方就能完成的  
工作，我都会觉得非常不爽，要么我就是完全理解了这个系统，才能开始，或者说起码达到一个  
很高的理解高度，才行。  
比如放说我要通过一个aws lambda的服务，就能搞定一个特定的任务，那么  
aws的lambda有许多的tutrial教程，只要学一下，就会用了，就可以在30分钟之内完成这个任务。  
但是呢，我就得从0开始学，并且把每个地方都得学会。  
所以为了搞定所有的东西，我打开了一票文档，然后这个http的endpoint返回了一个server error，  
而我完全不知道这是什么鬼。甚至于最终放弃了解决这个不是那么重要的server error  

我确实相信，如果我有更多的时间和耐心，  
我将最终对Lambda和相关的AWS产品有一个相当深刻的概念理解，  
并且可以更好地调试我的部署或解决未来的问题。   
但是，那不是我的目标； 我只想要在时间预算内有效的方法。   
因此，我最终只是没有任何有效的方法，也没有任何更好的理解。   
在复杂的系统上工作时，要对整个系统了解的特别透，可能是诱人且有害的，    
在这种情况下，完成任务，或者解决特定的问题从根本上不需要了解整个系统。
(译者:说的也对，让我想起了那个很逗的图，一个像牛顿的哥们，上来看到一个框架  
觉得说我擦这么牛逼的框架，研究一下；然后过了1小时，放弃了)
  
先做简单的事  
我曾经做过很多次，就是花了好几天时间，来定位一个依赖代码里的bug，最终发现    
社区upstream版本已经把它修复了，而我们用的是一个老的版本(译者:😂)   
或者，当我花时间尝试在没有调试符号的情况下调试二进制文件中的崩溃时，    
通过仔细地仔细检查coredump和x86反汇编，其实让同事找到调试版本，    
在那里重现问题然后用gdb来搞定就好了。(译者:😂😂😂)  

我有一套特殊的软件和系统技能，其中包括二进制逆向工程，   
并且可以快速掌握不熟悉的代码库。 我之所以拥有这些技能，    
部分原因是我渴望了解与我一起工作的系统。     
但是，拥有这些技能并不意味着它们总是适用于问题的正确技能！  

所以，杀鸡焉用牛刀！实在搞不定时再用牛逼的东西...  

```
Start with curiosity 
I want to close with some thoughts about how to get 
started with this mindset, and how to begin acquiring 
concrete skill understanding unfamiliar computer systems. 
I’ve learned my toolkit over (at this point) about two 
decades of wrangling computer systems, and I worry about 
inadvertently presenting a story that computers can be 
understood, but only if you have my particular depth of 
experience doing so. While I can only confidently write 
from my own experiences, I do deeply believe the mindset 
discussed here has value no matter how experienced you are.

My advice for a practical upshot from this post would be: 
cultivate a deep sense of curiosity about the systems you 
work with. Ask questions about how they work, why they 
work that way, and how they were built. Ask yourself 
questions like “How would I have built this library?,” 
identify the gaps where you don’t know the answer, and 
add them to your mental backlog of topics to learn.

For an even more tactical takeaway, I might start with 
this: Read the source of your dependencies, if that’s 
not already a habit you have. Do you write webapps on 
React? Try grabbing a checkout and reading through the 
source sometime. Are you working on a Django or Rails 
webapp? Check out the source of the framework in question. 
Even grab a copy of the Python or Ruby implementation, 
and take a look inside. Much of the standard library for 
those languages is written in the language itself, 
so you can even get started without learning much or any C. 
Your goal needn’t be to understand all of it at once, 
or even ever — just to build your understanding, and 
your confidence that you can always understand more tomorrow.

Learning more about software systems is a compounding 
skill. The more systems you’ve seen, the more patterns 
you have available to match future systems against, and 
the more skills and tricks and techniques you develop 
to apply to future problems. Understanding immensely 
complex systems may seem out of grasp at first, but the 
more you try the easier it becomes.

One of my favorite examples of an engineer who publicly 
models this mindset is Julia Evans, who I was fortunate 
enough to work with at Stripe. She is incredibly curious 
about how computers work, and does an amazing job writing 
and talking, not only about what she learns, but how she 
learned it, and conveying a raw sense of curiosity and 
excitement and discovery. Some of my favorite examples:

Her post about how she got into kernel development is a 
great concrete example of taking a scary area and finding a way in.

Her talk on how to become a wizard mirrors many of the ideas in the post, and also comes with practical advice on how to implement them.

Her post on asking great questions is an excellent resource for anyone working with others, or just who’s curious about learning more in computing!
```

我想对如何开始使用这种思维方式以及  
如何开始获得了解不熟悉的计算机系统的具体技能的一些想法做最后的思考。  
我已经在大约二十年的计算机系统争执中学习了我的工具包，  
并且我担心会无意间提出一个可以理解计算机的故事，但是前提是你跟我有一样的经验。  
虽然我只能凭自己的经验自信地写作，但我深信，  
无论您的经验如何，这里讨论的思维方式都是有价值的。  

我对这篇文章的实际建议是：对所使用的系统产生深刻的好奇心。  
询问有关它们如何工作，为什么这样工作以及如何构建的问题。  
多问问自己诸如“我将如何构建这个库？”之类的问题，找出您不知道答案的空白，  
并将其添加到您要学习的主题中。  

为了获得更多可落地的帮助，我可以从以下内容开始：  
如果您还没有习惯，请阅读依赖项的来源。  
您是否在React上编写webapp？   
尝试获取一个结帐并在某个时间阅读源代码。  
您正在使用Django或Rails网络应用程序吗？   
查看有问题的框架的来源。  
甚至可以获取Python或Ruby实现的副本，并深入了解内部。  
这些语言的许多标准库都是用语言本身编写的，  
因此您甚至无需学习任何C或任何C就可以上手。  
您的目标不必是一次或什至永远都不需要理解所有的内容，  
而只是为了构建你的对系统的理解以及对未来能永远理解的自信。  