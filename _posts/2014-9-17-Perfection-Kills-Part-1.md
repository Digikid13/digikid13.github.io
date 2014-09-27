---
layout: post
title: Perfection Kills: Javascript Hell Part 1
---

I came across this interesting [javascript quiz](http://perfectionkills.com/javascript-quiz/) (and did terrible) and wanted to go over exactly how all the questions work. This part is going to go over questions 1 - 4.

## Question 1

    (function() {
      return typeof arguments;
    })();

This function will return "object", this one is pretty simple. In every function there is an arguments object. Even if there are no arguments being passed in it is still created as part of the function scope.

## Question 2

    var f = function g() { return 23; };
    typeof g();

Here this results in an error, g is not defined. On the line ```var f = function g() { return 23; };``` the variable f is being assigned a function. That overrules the ```function g()``` and assgins the function to f instead. As it turns out you can type whatever you want instead of g and it will still be assigned to f.

## Question 3

    (function(x) {
      delete x;
      return x;
    })(1);

This is going to return 1 for one simple reason, delete only works on objects to get rid of a property. If you had the object ```var x = {a: 1};``` and typed ```delete x.a```
```x.a === undefined``` would be true.

## Question 4

    var y = 1, x = y = typeof x;
    x;

This one can be a bit tricky, let's break it down in terms of how it's processed.

### Step 1
    var y = 1
### Step 2
    var x = y = typeof x;
      y = typeof x; // x is currently undefined so typeof will be "undefined"
      x = y // y is currently "undefined" from above so we set x to that
### Step 3
    x; // "undefined"

When you run into things like ```x = y = z = 4```, it's best to think of it like this. ```x = (y = (z = 4))``` where the parenthesis are evaluated and return that value. So it turns out like this:

    x = y = z = 4;
            z = 4; // 4
        y = z;     // 4
    x = y;         // 4

It's important to note that if you run the above and do ```z = 5```, x and y are still going to be set to 4. Right most thing is assigned to everything on the left.


To be continued in Part 2.