---
layout: post
title: Classes and You
---

For today's post I'm going to be going over classes and when I do and don't use them.

##So what are classes?

Classes are objects that contain data and have added on methods used to manipulate that data.

###E.g.

    function Car(speed, area) {
      this.speed = speed;
      this.loc = Math.random()*area;
    }

    Car.prototype.move = function() {
      this.loc += this.speed;
    }

    car = new Car(20, 500);

Here we create a Car constructor that will create a the new object above.

Classes are used to create these objects as many times as it is called.
We can add another car: `car2 = new Car(15, 500);`

Both of these cars do not share properties. `car.speed === 20` while `car2.speed === 15`.

##So where would I use classes and not use classes?

Places I would use a class would be when I plan on creating multiple objects that I want to give initial values and methods that use those values. E.g. The example above, it can be used to create multiple cars in a racetrack.

You can also use them to create dom nodes:

    function Message(message, user) {
      this.node = $('<div class="message"></div>')
      this.message = message;
      this.user = user;
      this.node.text(user + ': ' + message);
      this.friend = false;
    }

    Message.prototype.changeFriend = function() {
      this.friend = !this.friend;
    }

Places I wouldn't use them are for 1 time things like creating objects with methods that aren't user inflenced. An example would be to store all of the functions that help run the app in an object to help make maintenance easier.

    var Board = {
      location: '/games/Diablo_3/',
      user: cookies.get('user'),
      
    }
    
