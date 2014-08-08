---
layout: post
title: Classes and You
---

For today's post I'm going to be going over classes and when I do and don't use them.

####So what are classes?

Classes are objects that contain data and have added on methods used to manipulate that data.

#####E.g.

    function Class(speed, area) {
      this.speed = speed;
      this.loc = Math.random()*area;
    }

    Class.prototype.move = function() {
      this.loc += this.speed;
    }

    car = new Class(20, 500);

Classes have the ability to create objects with data and methods as many times as the programmer wishes.
