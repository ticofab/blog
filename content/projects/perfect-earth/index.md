---
title: "2015 to 2016 - Perfect Earth Animals"
date: 2020-05-10
hideLastModified: true
summaryImage: "perfect-earth-themas.png"
showInMenu: false
---

Perfect Earth Animals is an educational app for kids. Centered around the discovery of biodiversity, it enabled players to
walk in a park and used locations services collect disseminated virtual cards of endangered animals and learn about them.

Animals were divided in themes corresponding to different natural areas such as Rainforest, Desert, Oceans and so on.

{{< figure src="android-screens.png" width="1280" >}}

The system was quite straightforward: a Play app built in Scala would store and serve all data from a persistence layer
in MongoDB. An Angular admin website allowed the client to insert new content, such as new animal cards, images or 
coordinates where a card would be available.  

This project was incredibly special as it has been the one and only paying customer *ever* for my own startup [CloudMatch]({{< relref "../cloudmatch/index.md" >}} "CloudMatch")!
Christian, the mind behind the entire Perfect Earth ecosystem, saw the playful potential of exchanging items with gestures
across touchscreens and believed in it enough to make it a unique feature of his card game. I'm not sure if I ever told him,
but I am very grateful for having believed in it. Below you can see a recording of an excited myself showcasing a working
prototype with the exchange mechanics in place.
 
{{< imageVideo src1="perfect-earth-phones-next.png" width1="430" id1="O9U3tdSMx6g" >}}

The app was visually beautiful, thanks to the gorgeous illustrations. It was a lot of fun to build too. The current app
is an improvement over the one that I built and I don't know how much of the logic has stayed, either on the servers or
on the mobile client. What I know for sure is that CloudMatch is no longer part of it.

{{< figure src="ios-screens.png" width="1024" >}}
 


