---
title: "2013 to 2014 - CloudMatch"
date: 2020-03-10
hideLastModified: true
summaryImage: "gestures.png"
showInMenu: false
---

- [The Idea]({{<ref "#product" >}}) 
- [Cloud-Native Architecture]({{<ref "#arch" >}}) 
- [Server Implementation]({{<ref "#server" >}}) 
- [Mobile Clients]({{<ref "#client" >}}) 

## The Idea {#product}

CloudMatch was a side-project that I tried building a company around. Born along the lines of the mobile revolution, the
idea was simple: enable cross-gesture communication between two touchscreen devices. The development of this product is the
reason why I discovered Scala, Akka and the ecosystem of reactive systems that I fell in love with.

{{< figure src="cloudmatch-features.png" width="920" >}}

Business-wise, we envisioned a lot of different use-cases and closed a few fun collaborations - we even had one paying customer!-
but no use-case was compelling enough to sustain a proper business. Ultimately, unable to find a good product-market fit, we
abandoned the idea and moved on. Some ideas that we explored:

- Banking sector (money transfer)
- Exchange of pictures / business card / social contacts / used items
- Educational games
- Videogames (the only paying customer)

These two videos show a couple of use-cases that we built.

{{< twoVideos iJAQg0W9l7U rkY2GclyemU >}}

What remains is an incredible roller-coaster experience and a very solid technical achievement. One of my most successful
conference talk ever was based on the CloudMatch engine that I built for scalability and resilience.

## Cloud-Native Architecture {#arch}

The engine has two main goals:

- establish a link between the matched devices
- allow a fast channel for data exchange

While there would be ways to make two devices communicate directly with one another, the most generic solution would be to
have a common service facilitating these operations. This would allow the magic to happen in the widest range of situations,
whether devices are on WiFi or mobile data, bluetooth, or any other form of connectivity.

The question is then -- what should this service look like? For starters, we need this service to scale A LOT. Millions of
concurrent users will use our system, we know that. We need to embrace distribution. The basic choice is thus between a
stateless or a stateful service, where the first choice implies delegating state to a persistence layer. This would quickly become
a nightmare of reads and writes - incredibly slow and incredibly expensive too.

A stateful service seems the only viable architecture. One where two devices can live on any instance of the distributed
service and communicate directly, like illustrated in the below-right image.

{{< twoFigure src1="cloudmatch-engine.png" width1="360" caption1="We need to link devices. How?" src2="cloudmatch-engine-detail.png" width2="480" caption2="A stateful service allows direct communication between devices." >}}

## Server Implementation {#server}

[Akka](https://akka.io) is a toolkit for the JVM that makes building such distributed services its very mission, and that
is how I first came to learn about its existence. [Actors](https://en.wikipedia.org/wiki/Actor_model) are the fundamental
unit of computation in Akka: stateful entities who live in memory and can message each other directly. Akka provides a
powerful abstraction that makes this possible even when two actors are on different nodes on different physical machines.

This is exactly what my engine needs. Each device using CloudMatch is represented by an Actor, which keeps track of its
state. For example, whether it's paired to another device: this Scala code snippet shows how an actor stores the reference to
the actor representing the matched device when receiving a message with such information.

{{< codeWide language="scala" >}}
  var matchedDevice: Option[ActorRef] = None
  override def receive: Receive = {
    case YouMatchedWith(device) =>
      matchedDevice = Some(device)
      logMatched(self, device)
  }
{{< /codeWide >}}

A complete working version of this product is available [on GitHub](https://github.com/ticofab/cloudmatch). This product
has also being the foundation for a series of talks I did back in 2018, together with [Adam Sandor](https://twitter.com/adamsand0r),
on how Akka is the perfect application-level companion for Kubernetes. [Lightbend](https://www.lightbend.com/), the company
behind Akka, invited me to give it as a webinar on their official channel.

{{< youtube id="FyneQrH-0Rc" >}}

## Mobile Clients {#client}

Any app that wanted to use the CloudMatch features could do so using the CloudMatch SDK, an open-source library for both iOS
and Android. Here is some more memorabilia from back then to close this portfolio entry.

{{< twoVideos OMTsVOx_9JU kNNm525r7Xk >}}

{{< figure src="swipic_feature_image.png" width="1280" caption="Promotional material for Swipic." >}}