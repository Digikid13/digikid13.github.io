---
layout: post
title: Perfection Kills: Javascript Hell Part 2
---

I came across this interesting [javascript quiz](http://perfectionkills.com/javascript-quiz/) (and did terrible) and wanted to go over exactly how all the questions work. This part is going to go over questions 5 - 9.

## Question 5

    (function f(f) {
      return typeof f();
    })(function(){ return 1; });

In this one you pass in a function ```function() { return 1; }``` so here f is equal to that function. The tricky part comes in when you add the '()' on line 2.
If you wanted to see if the input was a function you might want to type ```return typeof f;```, but since it has the '()' that means that it is going to be invoked.
Then it will run ```return typeof``` on whatever is returned by the function. That is why this function will return 'number'.

## Question 6

    var foo = {
      bar: function() { return this.baz; },
      baz: 1
    };
    (function(){
      return typeof arguments[0]();
    })(foo.bar);

&&

## Question 7

    var foo = {
      bar: function(){ return this.baz; },
      baz: 1
    }
    typeof (f = foo.bar)();

We can take care of both of these at the same time. If you look at what is being passed in it's foo.bar's function ```function() { return this.baz; }```. Now when the function is ran, it doesn't know what foo is and this refers to the window. So if you run this function this.baz === undefined and typeof undefined === "undefined".

## Question 8

    var f = (function f(){ return "1"; }, function g(){ return 2; })();
    typeof f;

When you do (x, y, z) z is what is returned no matter what. Example: Run ```(1, 5, 8, 2, 9, 4)``` in your console what get's returned? It's the same thing as this above code. Only the g() function is being ran and that is what is returned to f.

## Question 9

    var x = 1;
    if (function f(){}) {
      x += typeof f;
    }
    x;

When you run this the function f is not stored anywhere you are basically saying if(truthy) run this. If you pass in something that exists 'if' will assume it's truthy as long as what you put in doesn't return false. Because f() isn't actually stored typeof f will end up being "undefined".


To be continued in Part 3.