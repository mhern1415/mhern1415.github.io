---
layout: post
title:      "Exploring The Concepts of Scope and Hoisting"
date:       2020-04-27 22:12:15 -0400
permalink:  exploring_the_concepts_of_scope_and_hoisting
---


When taking a look at the concepts of scope and hoisting, the most important thing to understand is that a Javascript program works in two phases. Simply speaking, the first phase is where the code is processed and analyzed. During this phase, all function/variable declarations are stored in memory before the second phase occurs where the code is executed. For this reason, the first phase is often called the parsing/compilation phase or the creation phase. Below, we'll explore what is going under the cover of our programs. 

As a new Javascript developer, hoisting has easily been one of the harder concepts to wrap my head around. An easier way to understand hoisting is to think of it as a mechanism where JS "hoists" variable and function declarations to the top of their current scope. Before we can dive into hoisting into more detail, we'll look at scopes and how they relate to hoisting. 

**Scope**

Scope defines the region within which a function or variable can be used or the "visibility" of said function or variable. 

```
let globalVar = "I'm a global variable!"

function scopeFunction(){
    return globalVar;
}

scopeFunction(); // outputs:  "I'm a global variable!"
```

In the above example, the variable was declared in the global scope which made it available to any and all functions in the current global scope. 

In the next example, we'll declare a variable within a function.

```
var globalVar = "I'm a global variable!"

function scopeFunction(){
var localVar = "I'm a local variable!";
}

globalVar; // outputs:  "I'm a global variable!"

localVar; // outputs: Uncaught ReferenceError: localVar is not defined
    at <anonymous>:1:13

```

Again, we call on our global variable of `globalVar` and the output is as expected. This time, we also call on our local variable outside of the function but we get an error. Why is that? 

Since `localVar` is declared within the `scopeFunction`, it only exists within that scope. In the global scope, it doesn't exist! For that reason, an error is thrown when we try to access `localVar` in the global scope. 

Once you can determine where a function or variable is available, the idea of scope will be easier to comprehend. 

In regards to block scoping, it is important to note the difference between `let`, `const`, and `var` declarations. 

```
function myGames(){
    if(true){
        var game1 = "Animal Crossing";        // var declarations exist in the scope of the function.
        const game2 = "Mario Kart";     //const declarations exist only in the block scope. 
        let game3 = "Stardew Valley";   //let declarations exist only in the block scope.

    }
    console.log(game1);
    console.log(game2);
    console.log(game3);
}

myGames(); //outputs: Animal Crossing
Uncaught ReferenceError: game2 is not defined
Uncaught ReferenceError: game3 is not defined
```

In the example above, `game1` is declared with var and is *not* block-scoped while `game2` and `game3` *are* block scoped and not able to be defined. 

Equipped with this knowledge, the idea of variable and function *hoisting* will come easier.

**Hoisting**

After spending some time reviewing how scoping works, we know that any variable declared within a scope belongs to that scope. With hoisting now in the mix, variable and function declarations are "hoisted" to the top of the function scope or global scope if outside of the function. This makes sense when we refer to the beginning of this post where I wrote about Javascript programs consisting of two phases. 

During the first phase (compilation phase), the code is fully parsed before any of the execution begins.

First, it is important to understand the difference between variable declarations and variable assignments. 

```
var myVar; //This is a declaration.

myVar = "Hello World!" //This is a an assignment.

var myVar = "Hello World!" //This is the most common. A declaration and assignment on the same line. 
```

In the last example, we have a declaration and assigment on the same line. Let's take a look at what is going on under the hood. 

```
var myVar = "Hello World!"
```

... is the same as

```
var myVar; // Compilation phase with a declaration. 

myVar = "Hello World" //Assignment occurs in execution phase. 
```

Let's see this working within a function. 

```
function myGames() {
console.log(game);
var game = "Animal Crossing";

}

myGames(); // output: undefined
```

At first glance, the explanation for the output is simple. I declared `game` after `console.log()` so it *should* be undefined. Wait, what about variable hoisting? Well, it *was* hoisted. 

```
function myGames() {
var game;
console.log(game);
game = "Animal Crossing";
```
Above, we see what's really going on. The reason the output is undefined is because even though the variable`game` is hoisted, it is still initialized as undefined and stays undefined during the `console.log()`. It isn't until *after* when it is assigned the value of "Animal Crossing". 

Let's see what happens when we add another `console.log()` after the variable assignment.

```
function myGames() {
console.log(game); 
var game = "Animal Crossing";
console.log(game);
}

```

What's going on under the hood this time? What will our output be?

```
function myGames() {
var game; // Hoisted to the top
console.log(game); // game is still undefined
game = "Animal Crossing"; // Here, game is defined.
console.log(game); // Now that game is defined, our output will have a value of "Animal Crossing"
}

myGames(); 
/// output: undefined
/// output: "Animal Crossing"
```

As you can see above, by the time our program reaches our *second* `console.log()`, `game` has been defined! This proves that even though `game` was hoisted, it still wasn't *defined* in the first `console.log()`. 

**Conclusion**

While this might be a lot to take in, understanding the difference between each of the two phases in a Javascript program has helped me immensely. Seeing our own code being broken down into two phases has lead to a better understanding of how our variables and functions are hoisted and can lead to our own bugs being corrected in a timely manner. If you ever find yourself struggling to get a better grasp on hoisting and scope, break down your code line by line and separate the code into the two phases of Javascript programs. Hopefully, this post will help clear up any confusion you may have in regards to scope and hoisting. 

Thanks for reading!

**Sources:**

[You Don't Know JS Yet](https://github.com/getify/You-Dont-Know-JS/blob/2nd-ed/scope-closures/ch1.md) by Kyle Simpson


[The Ultimate Guide to Hoisting, Scopes, and Closures in JavaScript](https://tylermcginnis.com/ultimate-guide-to-execution-contexts-hoisting-scopes-and-closures-in-javascript/) by Tyler McGinnis



