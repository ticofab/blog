---
title: Scala Days 2019 with the Lunatech crew!
date: 2019-07-19T23:53:00+01:00
summary: "My first Scala Days was the 10th year anniversary"
summaryImage: "lunatech-let-luna-shy-scala-days.png"
keepImageRatio: true
tags: [scala, akka, akka-http, Websocket]
---

I had never attended a Scala Days conference before - not even when it was hosted in the city
[where I live](http://event.scaladays.org/scaladays-amsterdam-2015). Shame on me! 

This year 2019 marked the 10th yearanniversary of the conference, and I was able to attend thanks to 
the support of [Lunatech](https://lunatech.com/),
an agency that embodies the Reactive soul in every service that they provide. I have known them for a while as I run 
the [Reactive Amsterdam](https://www.meetup.com/Reactive-Amsterdam/) meetup and they are very active with the community
at large. I met them back in March at a meetup where their Xavier Tordoir gave us an introduction to 
[Tensorflow in Scala](https://www.youtube.com/watch?v=83iprWIhjMM) (this links is to the same talk he gave at another conference)
and they offered me the opportunity to tag along to the upcoming Scala Days 2019 in Lausanne. Where can I find the _eternal gratitude_ emoji? 🙂

Attending was a great experience, especially as I am currently other technologies in my day-to-day work. 
In this post I want to go over my most important tech takeaways, interlaced with random pictures. I wrote more 'personal'
remarks in a [short thread](https://twitter.com/ticofab/status/1139918004806967297) on Twitter.

* *It is time to try out GraalVM.*
* *Akka Streams keeps leading the streaming world.*
* *Scala 3 is _almost_ there!* 

## It is time to try out GraalVM

I had certainly read about [GraalVM](https://www.graalvm.org/), but the two talks I attended managed to fully convince me.
GraalVM is a universal VM to run code written in different languages. For the JVM family of languages, the most important bit
is a different JIT compiler which performs a powerful code analysis that results in advanced optimizations.

The first one was by Vojin Jovanovic, "[Run Scala Faster with GraalVM on Any Platform](https://scaladays.org/schedule/run-scala-faster-with-graalvm-on-any-platform)":
a benchmark-fueled deck which introduces GraalVM and their offerings (notably the community vs paid supported version).
 
The second one was a perfect complimentary talk, from Chris Talinger, 
"[Performance Tuning Twitter Services with Graal and ML](https://scaladays.org/schedule/performance-tuning-twitter-services-with-graal-and-ml)".
Chris went over the scale of Twitter's production system, which is simply astounding for its magnitude. The amount of services
is in the thousands, while the amount of instances per service goes in the hundreds, for a mass of instances of O(10^5) 😮. 

This talk is truly inspiring and funny (plus you hear me laugh loudly at 55:13). It turns out that the GraalVM
optimisations are very effective with Scala code as Scala has lots of constructs and hidden object instantiations. It turns out
that the classic C1 and C2 JIT compilers were not written with other languages than Java in mind, which is kinda obvious as most
of them did not exist at the time. Twitter runs its services in its own data centers: little tweaks and optimisation can
have a tremendous impact on costs.

If you are using Java 11, enabling GraalVM is as simple as adding three compilation options:

```java
java [your other options]
     -XX:+UnlockExperimentalVMOptions \
     -XX:+EnableJVMCI \
     -XX:+UseJVMCICompiler
```

_Picture below: enjoying the real Swiss fondue with the Lunatech crew!_

![When in Switzerland, enjoy the real fondue.](lunatech-fondue-lausanne-scala-days-2019.png)

## Akka Streams keeps leading the streaming world

This does not come as a surprise. I am a huge fan of Akka Streams and have used it for many projects, both
[personally](http://ticofab.io/Caterina-side-project/) and professionally. I have given
[talks](https://www.youtube.com/watch?v=MQGXrrhGUTw&t=5s) and workshops about it. 
I am currently working on a .NET environment and I find nothing comparable in terms of flexibility, power and ease of use.
The talk I attended by Heiko Seeberger, "[Akka Streams to the Extreme](https://scaladays.org/schedule/akka-streams-to-the-extreme)",
was a good way for me to catch-up on the latest best practices and new features about this great piece of technology. Check it out!

_Picture below: Lunatech organised a support funding for the [Let Luna Shine](https://www.gofundme.com/let-luna-shine) cause,
and they would donate 1 euro for each picture taken with their mascotte._ 

![Let Luna shine](lunatech-let-luna-shy-scala-days.png)

## Scala 3 is _almost_ there!

Martin Oderski opened the conference (who else could have done it?) and his keynote "[A Tour of Scala 3](https://www.gofundme.com/let-luna-shine)"
went over the features that he believes will bring the largest benefits to Scala practitioners more. Enums, union types,
a rework of the concept of implicits (future `delegates`) to name a few. I am very much looking forward to this change, and
there is no risk of 'Python syndrome', mostly thanks to the fact that Scala is strongly typed! ✌️

I hope that Scala 3 will contribute positively to its adoption, but my heart is somehow a little doubtful. I do not see people who
would not consider the language earlier now embracing it because of union types or delegates. Maybe it is just me not seeing
an ocean of possibilities. To me Scala is already a fantastic tool with an unparalleled ecosystem, so I welcome any improvement.
My question is more if the new features will be impressive for people who have not turned to the light yet 😇
In fact, I believe that for the average Joe (like me), the ecosystem around Scala is a bigger selling point than the 
language features themselves. We will see what happens! Our hearts are with Scala.

I would have liked to highlight more content and probably I have missed lots of great content too - that happens when 
you have four parallel tracks!