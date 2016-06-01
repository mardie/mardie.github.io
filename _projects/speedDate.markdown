---
layout: project
title:  "SpeedDate. Very fast relations."
subtitle: "Very fast (redis) relations"
status: "done"
image: "/images/speeddate.png"
---
I love redis for storing fast data. Of course it is not a silver bullet and even it could be easier a misuse it than others. But I love its speed and simplicity.It isn’t a end to end solution (not always) instead it is a toolset to model your solution. Some people use only the pubsub, others use only the cache (GET/SET). Continuing this modularity SpeedDate could be a solution for your relations (not necesary between redis elements).

## How It works

By design redis is extremely simple and nothing is wrong with that.But sometimes when you use redis you miss relations for your data. One aproach is to use ORM(HRM, xRM) but it adds a lot of background weight. I think this works in the oposite direction of this kind of datastructures and finally they become slow. Another way is using sets and strings for storing the related keys. This is much more efficient but you face with all the boilerplate in every entity/model . Here it comes SpeedDate that uses the last implementation and wrap it in a module for easy and fast use. You will spend more time in your functionality and less in logistics.

## Init/Config

```javascript
var redis = require("redis"),
client = redis.createClient(),

SD = require("speeddate");
SD.con(client);

//<<YOUR CODE>>
```

## Inspiring ideas:

Here ara a few ideas. Remember that they are just ideas and code may not work because of over simplification.

*Don't forget the config block. See Init/Config below.*

A Blog. User has many posts. User 1 has Post 2.

```javascript
var posts = SD.hasMany("User","Post","PostByWriter");

//Setting data
posts.set( user, post );
//user and post can be a String, a id or whatever....

//Retrieving data
posts.get( user, function(data){
//do something with data
});
```

Does the given user token belong to the admin group?

```javascript

var roles = SD.hasMany("Rol","User");

roles.contains( "admin", userToken, function(isAdmin){
  if(isAdmin){

  }
});

```

Similar to the last. Is the ip banned?

```javascript
var roles = SD.hasMany("BlackList","IP");

roles.contains( "blacklist", ip, function(isBanned){
  if(!isBanned){
    //200
  }else{
    //403
  }
});

```

## ‘Half relation’

What does this half relation thing is? Sometimes you know you will not query one of the parts of the relations. Let’s see:

A user can repport issues. But for us will not be important what isues a user reported.

```javascript
var issues = SD.belongTo("Issue","User");

//On reporting issue
issues.trac(issue,usermail);

//...

issue.get(issue,function(usermail){
//Mail the user
});

```

Its the same as other examples but internally isn’t stored the opposite index for querying the users. Optimization. Freeing memory. This can be made with trac and free commands

## But I haven’t see the word DB anywhere.Why?

As you could have noticed throught examples you can relate data but you are free for storying it wherever you what. SpeedDate just stores the relation.


[https://github.com/mardie/SpeedDate](https://github.com/mardie/SpeedDate)
