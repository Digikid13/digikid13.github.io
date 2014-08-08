---
layout: post
title: Creating and using Objects w/ methods
---

So today we are going to talk about Object creation and the different ways we can add methods to them.

We have a few ways to do this:
###### Static creation
```javascript
var car = {
  speed: 200,
  loc: Math.random()*5,
  drive: function() {
    this.loc += this.speed;
  }
}
```

###### Functional Style
```javascript
function createCar(speed) {
  var car = {};
  car.loc = Math.random()*5;
  car.speed = speed;
  car.drive = function() {
    this.loc += this.speed;
  }
  return car;
}
```

