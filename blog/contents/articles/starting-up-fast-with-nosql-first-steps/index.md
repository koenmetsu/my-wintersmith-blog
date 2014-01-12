---
title: "Starting up fast with NoSQL: first steps"
author: koenmetsu
date: 2012-03-26 12:00
template: article.jade
filename: /:year/:month/:day/:title/index.html
---

After reading up a bit on NoSQL, I decided it was time for me to do some experimenting and see how quickly I could set up an application using NoSQL. One of the things I like about NoSQL is that it supposedly supports very low-friction development, which I'm going to try and find out soon.

I'm not going to talk about [whether or not NoSQL is right for you](http://stackoverflow.com/q/2875432/367388), [which NoSQL implementation/provider is best](http://blog.nahurst.com/visual-guide-to-nosql-systems) or [whether or not NoSQL is better or worse than SQL](http://stackoverflow.com/q/2571098/367388). I'm just having some fun with it, and seeing how easy this goes. I will focus on [document store databases](http://ayende.com/blog/4459/that-no-sql-thing-document-databases) and C# .NET. 

Personally, I'm also hoping to find out if NoSQL is a better match for quick and dirty personal projects than Plain Old SQL.

# Choosing a NoSQL for .NET
After reading up on what NoSQL databases are most popular for .NET, the choice came down to [RavenDB](http://ravendb.net/), [CouchDB](http://couchdb.apache.org) and [MongoDB](http://www.mongodb.org).

##RavenDB
RavenDB is made by [Ayende](http://ayende.com/blog) ( among others, I suppose ), and has the reputation of having a very nice and clean API plus a very good-looking management application made in Silverlight ( perhaps Silverlight isn't dead yet after all ). RavenDb however has a commercial license for non-open-sourced projects, and since I wanted to use NoSQL for one of my personal ( non-OS ) projects, I decided to let this one go for the moment. It's definitely worth taking a look at though, so it stays on my list for later projects.

## CouchDB and MongoDB
This left me with the other 2 competitors. I didn't put much effort into comparing the two in terms of functionality since I'm only exploring the the subject of NoSQL, and decided on a "community knows best" approach.

A quick [NuGet Fight][1] ( somebody should make this into a website, [which we now did][2] ) gave the advantage to MongoDb ( aka Mongo ), and off I went.

![nuget fight](http://koenmetsu.com/get/images/nuget_fight.png "Mongo vs Couch")

I usually don't let a simple NuGet Fight [decide which libraries I use](http://davybrion.com/blog/2012/01/how-do-you-pick-open-source-libraries/), but since this is only experimentation, it's good enough for me.

##Setting up Mongo ( the very easy way )
The whole point of this exercise was to have a no-friction-at-all experience. Setting up a mongoDb locally? Aaah, friction, get it away! 

But seriously, I wanted none at all.

##Mongo in the cloud
This matches my philosophy of "somebody probably already did this better than me", and since a lot of these providers offer a free sample of their services, how much less friction can you have?

I decided to use MongoLab, mostly because their free offer was the best I could find. They offer 240MB for free, all you need to do is sign up.

![sign up](http://koenmetsu.com/get/images/mongoloab_sign_up.png "sign up")

How can you resist?

##Creating your database
MongoLab offers a nice web interface for all creation and management of your MongoDB. 

![mongolab overview](http://koenmetsu.com/get/images/mongolab%20databases.png "mongolab overview")

Creating a new database is easy, you can even choose your provider. I also like the fact you can get different pricing schemes for different databases. For now, we'll test our luck with the free version.

![create new db](http://koenmetsu.com/get/images/mongolab%20create%20new%20db.png "create new db")

Et voila! We have our new database. You can see the connectionString in the overview, which we'll use in our application later.

![my first mongo db](http://koenmetsu.com/get/images/mongolab%20myfirstmongodb.png "my first mongo db")

All we have to do now is create some collections ( aka tables in other environments ) to put our data in. We can do this via the web interface as well as in code. For now, we'll stick to the web interface.

![add collection](http://koenmetsu.com/get/images/mongolab%20add%20new%20collection.png "add collection")

I want to create a small exhibitor website for this demo, but I don't know which properties I will store for each entity. With document store database, you do not have to define any columns on your table (because there is no table, only a collection of documents), so I can choose  what to store later instead of having to decide right now. This once again removes some friction, and more importantly: it delays design choices to when I'm ready for it.

#Consuming Mongo
A small controller and an entity class later, and my little expirement is already taking form. 

    public class HomeController : Controller
    {
        readonly MongoServer server;
        readonly MongoDatabase mongoDb;
        readonly MongoCollection<Exhibitor> exhibitors;
        public HomeController()
        {
            server = MongoServer.Create(string.Format("mongodb://{0}:{1}@ds031587.mongolab.com:31587/myfirstmongodb", ConfigurationManager.AppSettings["MongoUser"], ConfigurationManager.AppSettings["MongoPwd"]));
            server.Connect();

            mongoDb = server.GetDatabase("myfirstmongodb");
            exhibitors =
               mongoDb.GetCollection<Exhibitor>("exhibitors");
        }
        public ActionResult Index()
        {
            return View(exhibitors.FindAll());
        }
    }        
    
#Conclusion
So far, everything is still going well for me. I've set up a small database in a couple of minutes and got a simple piece of code working.
Next post, I'll be going deeper into the code and create a simple CRUD application using our newly created Mongo database.


  [1]: http://www.nugetfight.com
  [2]: http://kevinpelgrims.com/blog/2012/05/21/introducing-nugetfight
