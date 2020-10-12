---
title: "2016 - The Things Network"
date: 2020-06-10
hideLastModified: true
summaryImage: "ttn-basement.jpg"
showInMenu: false
---

I am very fascinated by the IoT movement. This is why in 2015 I became a regular attendee of the early sessions of
[The Things Network](https://www.thethingsnetwork.org/), a working group based on the nascent LoraWAN technology. 

The goal was to create a distributed network of LoraWAN sensors spread around the city, powered by a backbone that
would allow any number of devices to connect to it and exchange payload. A sort of alternative, local Internet if you want.

The first meetings were held in the basement of the mythical Rockstart venue on Herengracht in Amsterdam. The atmosphere
was that of a total underground hacking team, tinkering around with antennas and electrical components of all kinds. 

Back then we had a MQTT broker that people could use to check the data produced by their devices and collected by our LoraWAN
network. I wrote an [Android SDK](https://github.com/ticofab/The-Things-Network-Android-SDK) to retrieve data from such
server and created a sample app to showcase its use. 

{{< twoFigure src1="ttn-basement.jpg" caption1="An underground basement to tinker away" width1="1024" src2="ttn2.png" width2="500" caption2="The sample TTN App for the TTN Android SDK">}}

It was a lot of fun to work there for a while, but soon it became clear that despite the proclaimed openness and
crowd-ownership, the actual governance was strictly controlled by the two founders. The Things Industries, a for-profit
organization sister of The Things Network, was created some time later. There is nothing wrong with for-profit ventures;
the only issue is claiming a project to be open when it factually isn't. 

From the same period is my blog post about [my first steps with LoraWAN and SodaQ](https://ticofab.io/blog/first-steps-with-iot-and-lorawan/).