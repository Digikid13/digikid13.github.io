---
layout: post
title: 'Perfection Kills: Javascript Hell'
---

I came across this interesting [javascript quiz](http://perfectionkills.com/javascript-quiz/) (and did terrible) and wanted to go over exactly how all the questions work.

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
