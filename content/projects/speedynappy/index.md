---
title: "2016 - SpeedyNappy"
date: 2020-07-10
hideLastModified: true
summaryImage: "speedynappy.png"
showInMenu: false
---

SpeedyNappy is a side project that I run with my friend and **AWESOME** illustrator [Chiara Vercesi](https://www.behance.net/chiaravercesi).
The mobile app lets users:

- Log in with Facebook credentials
- Search for the closest venue with changing table
- Get directions to that venue via the Google Maps API
- Rate the venue and add details about it
- Insert a new venue
- Curate a list of favorite venues

{{< figure src="speedynappy.png" width="1024" >}}

The server was a CRUD service built with Scala and Play, deployed on CleverCloud. The client was the most interesting
part to develop. I wrote a custom UI rating component using the stars icons from the Material Design pack.



