---
title: Akka Cluster Singleton Example
date: 2017-10-04T23:53:00+01:00
summary: "An example app using Akka ClusterSingleton and ClusterRouterPool."
summaryImage: "2017-10-04-akka-cluster-singleton-example-sample-image.png"
keepImageRatio: true
tags: [scala, akka, akka-cluster]
---

**What are Actors in Akka?**

Akka is a toolkit to build scalable, resilient systems. The building blocks are [Actors](https://doc.akka.io/docs/akka/current/scala/actors.html), on top of which Akka builds lots of abstractions ready for us to use. One such abstraction is the _clustering_ functionality.

Actors are entities that communicate with each other via messages, just as much as you and I communicate by asking things and answering. If you're curious about my age, there is no way to plug into my body and perform something such as

```scala
int age = fabio.getAge();
```

What you will do instead is sending me a message (either via voice, or via written form), asking:

```scala
What is your age?
```

, to which I will reply:

```scala
22
```

Actors communicate in the exact same way. This separation enables a great deal of benefits, one of which is _location transparency_. Think about sending me an email: you don't need to know where I physically am, as long as you know my email address. I might be in New York or in Tokyo, but you would still be able to ask my age and I would be able to reply.

**Enter Akka Cluster**

The very same thing holds for Actors: as long as you know their address, you can get in touch with them. This functionality is called _remoting_: an actor can communicate with another one even if it resides on a different node/machine, as long as the recipient's address is known. On top of this, Akka builds the _clustering_ functionalities: an abstraction that lets you be in control of your cluster of nodes, getting notified when someone joins or leaves the party. It is very simple to establish a cluster and we're going to show it with a simple yet fascinating example.

Our goal is to create a unique __Master__ node that will distribute messages to any __Worker__ actor that joins.

After importing the correct dependency, which at the moment of writing is

```scala
"com.typesafe.akka" %% "akka-cluster-tools" % "2.5.6"
```

, the first thing to do is configuring your system. For this, check the [official documentation](https://doc.akka.io/docs/akka/current/scala/cluster-singleton.html). 

Akka comes with another very useful feature: the ability for a node to _create_ actors on other nodes. We will use it together with the abaility to route messages to all the created actors in a round-robin fashion. This is extremely useful in many situations where you can distribute work across nodes.

The worker actor is very simple: it will simply log anything that comes in.

```scala
class Worker extends Actor {
  override def receive = {
    case s: String => println(s)
  }
}
```

Now on to the master actor. As soon as the master starts, it will subscribe to cluster events to be notified when a new node joins (or leaves). This is achieved with 

```scala
Cluster(context.system).subscribe(self, classOf[ClusterDomainEvent])
```

The master actor will also keep track of the current amount of connected nodes in a variable called workerCounter. This is used to create the round-robin router I mentioned earlier. The code to create such a router is

```scala
val router = context.actorOf(
  ClusterRouterPool(
    RoundRobinPool(workerCounter),
    ClusterRouterPoolSettings(
      totalInstances = 1000,
      maxInstancesPerNode = 1,
      allowLocalRoutees = false
    )
  ).props(Props[Worker]),
  name = "worker-router"))
```

At this point the master node will send messages to the router, which in turn will distribute them on the Worker actors created on the remote nodes. This is the receive method of the master:

```scala
override def receive: {
  case s: String => router ! s
}
```

The actual implementation is a little more complex, but this is the essence of the whole thing! Check out the [code on github](https://github.com/ticofab/akka-cluster-singleton-example) and test it on your machine. Create first the master node at port 2551 using:

```scala
sbt run
```

And then create one or more workers specifying a different port and the "worker" role like this:

```scala
sbt -DPORT=2552 -DROLES.1="worker" run
```

Add more workers as pleased, then relax and check the magic happening!

