---
layout: post
title: Perfection Kills - Javascript Hell Part 3
---

I came across this interesting [javascript quiz](http://perfectionkills.com/javascript-quiz/) (and did terrible) and wanted to go over exactly how all the questions work. This part is going to go over questions 10 - 14.

## Question 10

    var x = [typeof x, typeof y][1];
    typeof typeof x;

Here the array is created and then indexed but it's not stored in x. What is stored in x is 'typeof y' which returns "undefined". So when you run ```typeof typeof x``` the typeof x returns "string" and the second one returns "string" as well. Since at first x === "undefined" which is a string.

## Question 11

    (function(foo){
      return typeof foo.bar;
    })({ foo: { bar: 1 } });

This one is another trick question, if you type everything out it'll make it much easier. Here ```foo = {foo: {bar: 1}}``` so foo.foo.bar === 1, but in the function it tests for foo.bar. This doesn't exists so typeof something that is undefined returns "undefined", which is the answer to this question.

## Question 12

    (function f(){
      function f(){ return 1; }
      return f();
      function f(){ return 2; }
    })();

This one is just testing your knowledge of function hosting. Here both f()s get pulled to the top and the ```function f(){ return 2; }``` overwrites the first one. There is also something else you need to know about scoping that helps. When ```return f();``` is ran, it first checks the current scope it is in (the function). If it can't find it there it will check the scope above, and the one above that, and the one above that until it get's to the global scope. If it finds what it's looking for it will use it. That is why this doesn't become a recursion problem cause f() exists in the scope. (NOTE: This is bad practice and you shouldn't write like this.)

## Question 13
    function f(){ return f; }
    new f() instanceof f;

Now what instanceof does is check to see if a variable exists in the scope on the left. In the function f(), f is undefined therefore there is no instance of it. So instanceof will return false.

## Question 14
    with (function(x, undefined){}) length;

This is a really weird one that you should NEVER NEVER use. 'with' assumes a lot of things or atleast tries to. Here it looks for things that have length in them, in the scope of the function. Since the only thing that has a length in the scope is arguments, arguments.length is what is returned here. So the answer to this one is 2. Do not do this, if you want something like it program it specifically!


And that's it, if you have any questions or changes feel free to E-Mail me at: Digikid13 [ at ] gmail.com
