---
title: "2016 to 2018 - Weeronline"
date: 2020-05-10
hideLastModified: true
summaryImage: "weeronline-symbols.png"
showInMenu: false
---

[Weeronline](https://www.weeronline.nl/) is one of the leading weather forecast platforms in the Netherlands. 'Weeronline'
literally translates to 'Weather online'. Mostly ad-funded, Weeronline is a very successful business. In fact, I wsa 
quite shocked to learn the yearly revenues, but it all made sense when I realized that weather services are most valuable
in places where the weather is very uncertain and fluctuating. For example: in Sicily, where you would expect the sun to shine
on most days throughout the day, you would rarely check a forecast app. The Netherlands, with its famously unpredictable
'four seasons in one day' weather, these apps are literally among the most useful of all.

{{< figure src="dutch-weather-if-you-re-a-plant-you-will-love-it.jpg" width="560" >}}

During my years at Weeronline I covered three different roles and each one gets its own section.

## Java Android Developer

I worked on the release of the second version of the Android app. My main achievement was introducing dependency injection
with Dagger, which lead to a cleaner codebase. Beside that huge effort, the rest was the usual app development that you would expect: 

* HTTP interaction with data sources, managing latency and errors
* Asset management for different screens and resolutions
* UI navigation

 
{{< figure src="weeronline-android-app.png" width="920" >}}

## Scala Backend Developer

The company Weeronline was part of a bigger German holding called HolidayCheck (which sold it in 2020). They used Scala as
main backend language and there was an effort to unify the tech stack.

The challenge was immense as Weeronline's legacy servers were written in Visual Basic 6, which nobody really understood.
One of my first tasks was indeed to map all that incredible legacy, spread across dozens of servers managed by a local provider.
The result of that effort were the infamous 'lanes'. I covered an entire wall with these flows linking data sources, processing
logic, outcomes and their business value. 

{{< figure src="weeronline-war-room-lanes.png" width="1024" caption="Johnny is mind-blown by the lanes.">}}

Mapping those ETL flows was a huge effort, but it paid off in terms of visibility and prioritization of the work to do.
Two features emerged as the most valuable ones within the system: the 2-hour precipitation radar and the global forecast 
up to 14 days in the future. Had the current implementations gone down, that would have meant great losses for the company.

{{< figure src="radar-anim.gif" width="460" >}}

The precipitation radar was the fist one to tackle. The Dutch Meteorological Institute (KNMI) releases regularly satellite 
images of the Dutch sky. Combining those with wind, humidity and other factors, it's possible to generate reliable precipitation
predictions for the coming 120 minutes. You still need to remove noise and other steps, but the process looks roughly like this:

{{< figure src="radar-image-processing.png" width="1024" >}}

The other massive piece of work was the weather forecast up to 14 days in the future. Data was regularly ingested from a
third party provider - a German company that has 16.000 weather stations all around the globe. This immense amount of
information was processed through a lot of different formulas to output worldwide forecasts, wind information, activity
suggestions based on weather and a lot more. It would look like this in the frontend.

{{< figure src="weeronline-mos05-days.png" width="800" >}}

Both features were built using Scala and Akka (Streams), packaged as a Docker container and deployed on Kubernetes, using
mostly Kafka as glue between the different services.

## Tech Lead

At some point at the end of 2016 I was made Tech Lead, and the entire development department reported to me. I stopped coding
and became instead more involved in high-level architectural discussions spanning the entire spectrum, from backend services to
mobile and web frontends. I became a connection between stakeholders, product owners and developers and actively helped
to shape roadmaps based on required development efforts and business value. 

I did a lot of hiring and people management too, growing the department to 16 developers at its peak, divided in three
teams, each one with its own leader. I fought and won some free creative time (a monthly internal event named Freaky Friday).
I did my best to foster community engagement within my departments, hosting a few meetup events (I [spoke](https://youtu.be/MQGXrrhGUTw)
at two of them).

{{< figure src="reactive-amsterdam-weeronline.png" width="1024" >}}

This career change definitely took me out of my comfort zone. All of a sudden I was in meetings all day, and 'time management'
acquired an entire new meaning. Looking back at the experience, I think I did an honest job, but I can also see so many
things I could have done differently. Letting go of the technical side wasn't easy, and I should have definitely delegated
more. I worked hard to get my vision realized, while what matters is the team's vision. I tried to be on top of too many
things at the same time, which resulted in a lot of stress. The hardest part was the leader's loneliness. After being a
'brogrammer' throughout my career, in the new role I felt disconnected from the devs in my team, like if an invisible wall
was standing right in between. I had to manage a few very difficult cases: a despotic developer with sociopathic traits,
a poorly skilled one, making someone redundant (dealing with laws and lawyers), and all the internal conflict that ensued.
This all took a toll and after exactly one year I went back to software development.

As the saying goes tho, experience is the best teacher. I really have learned a lot from my mistakes and I worked hard
on my empathy and compassion. As I write, I am in a leading position again - and I can see the huge difference.
I am finally able to put in practice all the good advice by my manager at the time, to delegate and let go, focusing on the longer
term wins rather than the daily reward of fixing a bug or adding a feature. I have my side projects for those kinds of
tech achievements!

Approaching my job with a different perspective lets me embrace both pains & joys of being a leader, and I am actually
even having fun! Without the experience at Weeronline I wouldn't have been able to tackle the current one with this spirit.
And I can only be all the more thankful to everyone that I met there, difficult people included. 🙂
   
 

 