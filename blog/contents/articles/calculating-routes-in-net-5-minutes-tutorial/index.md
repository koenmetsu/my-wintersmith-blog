---
title: "Calculating Routes in .NET: 5 minutes tutorial"
author: koenmetsu
date: 2010-01-18 12:00
template: article.jade
filename: /:year/:month/:day/:title/index.html
---

Calculating the 'road distance' between two points can come in handy when you want to calculate the transport costs between your company and your customers.

Google Maps is great for calculating a single route, but when you want things automated, you need some kind of web service for this, which Google doesn't provide.

A lesser known competitor of Google Maps is Microsoft's Bing Maps, which has a great SDK that you can get up and running in about 5 minutes, and 4 easy steps.
<h2>1. Create a Bing AppID</h2>
To be able to use the Bing Web Services, Microsoft requires you to request a unique key through <a href="http://www.bing.com/developers/createapp.aspx">this website</a> ( you will need a Live ID ).
<h2>2. Add a Service Reference</h2>
Add the following service reference to your project:
http://dev.virtualearth.net/webservices/v1/routeservice/routeservice.svc?wsdl

<img src="http://koenmetsu.files.wordpress.com/2010/01/011510_1704_calculating12.png" alt="" />
<h2>3. Setting up your request</h2>
Next thing we do is set up the RouteRequest.

In this example I provide the latitude and longitude myself ( from a random geocoding site ), but you could use Microsoft Bing's or Google's geocoding service as well, to get the lat/long from any address you like.

I've added some commentary in the code, so it should be self-explanatory.

    // Get a key at http://www.bing.com/developers/createapp.aspx
    string key = &amp;quot;xxx&amp;quot;;
    
    BingRoutingService.RouteRequest request = new RouteRequest();
    request.Credentials = new Credentials { ApplicationId = key };
    
    // the actual waypoints, from start to finish.
    request.Waypoints = new Waypoint[]
    {
      // Brussels
      new Waypoint(){ Location= new Location(){ Latitude = 50.8462807, Longitude= 4.3547273}},
      // Paris
      new Waypoint(){ Location= new Location(){ Latitude = 48.8566667, Longitude= 2.3509871}},
    };
    
    // For the international crowd, you can also switch this to miles.
    request.UserProfile = new UserProfile
    {
      DistanceUnit = DistanceUnit.Kilometer
    };
    
    // some optional parameters
    request.Options = new RouteOptions()
    {
      Mode = TravelMode.Driving,
      Optimization = RouteOptimization.MinimizeTime
    };


<h2>4. Getting the results</h2>
Last thing on the to-do list is setting up our RouteServiceClient. This will send the actual request, and get the results back in a nice RouteSummary object.

    RouteServiceClient client = new RouteServiceClient();
    
    RouteResponse response = client.CalculateRoute(request);
    RouteResult result = response.Result;
    Console.WriteLine(result.Summary.Distance);



The distance will be in the unit specified in the UserProfile object.
The RouteSummary object will also contain the time needed to drive in seconds.

If you like you can even get the full route path from the RouteResult object, and a lot more, but I'm not going to be able to cover that in a 5 minute post ;-)


