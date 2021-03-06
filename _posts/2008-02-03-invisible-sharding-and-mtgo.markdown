--- 
layout: post
title: Invisible Sharding and MTGO
tags: 
- think
- hack
- mtgo
- servers
- networking
date: 2008-02-03 16:34:18 -06:00
---
Lately I have been playing a lot of Magic: The Gathering.  While most people who play the game are content to go to a shop and play with paper cards, I'm much more geeky than that, and don't really have the time to go to a game store.  I play on the Magic Online.   I've detailed before how the server architecture of the Magic Online servers is not good - there is a single, monolithic server which is handling most of the game functions which users take part in.   Because of this horrible server architecture, Wizards of the Coast decided to make a new version, throwing out the code base that they had before.  While this is not necessarily a good idea, I understand why they did it.

They can solve the problem of their server setup by using the Invisible Sharding method, and they are possibly one of the only games that can do such.  Sharding is when a game server is split into multiple servers, which are separated from each other.  This is why there are many different "realms" on World of Warcraft, and many of the other MMORPGs.  Servers can only handle a certain amount of load at once, and splitting all the users across multiple server lets you still have a Massively Multiplayer experience while being infinitely scalable to more users.   It works out pretty well, but it comes with some problems as well.  If I want to join World of Warcraft and play with my friends, I need to know which server to start my character on in order to join with them.  This can cause problems due to the way that social networks are very tightly wound.  If you take you and three levels of friends, you have a very large amount of people.  As a game grows, more people want to play with their friends and that means more people are on the same server.   I heard that recently Blizzard had planned to migrate people from one server to another, which was a major event and then they improved their servers so they cancelled that migration.  In a perfect world, no migration would be needed - everyone would be on the same server.

MTGO is the perfect world, but they suffer from the problem that the MMORPGs would have if everyone was logged onto the same server now - they have a server overload.  So how do you solve this problem?  The solution hinges on the good parts of the current architecture:  games are separated from the main server.   The main server can now be separated from the games, and we have a situation which is similar to a distributed consensus problem.  The solution is to reduce the size of the data which needs to be consensus.  There are two ways to do this.  The first is to reduce the overall size of the set by limiting interaction between players - this is the sharding solution.  The second way to do it is to be more intelligent with the data that you choose to pass between your servers.  MTGO is unique in this respect because there is really a small amount of data which needs to be replicated in order for the system to run smoothly.

Version 3 of the program is launching in less than 2 weeks according to the timer - here's hoping that they got the new architecture right, and we can see many thousands of players on at the same time.
