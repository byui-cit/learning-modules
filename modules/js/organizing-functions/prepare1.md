---
title: Function Basics - Introduction to Functions
description: What is a function? and how do functions in JavaScript compare with other languages like Python?
date: 2021-10-15

layout: layouts/post.njk
---

## Organization and Access

All computer languages are ways to organize your communication and thinking. In this, they are very similar to spoken languages. Each spoken language, or family of spoken languages, does this organization differently. English sentences often have a structure of Subject-Helper Verb-Verb-Predicate...The boy will bite the dog, for example. German, a language closely related to English, organizes things differently. Sometimes German sentences have a Subject-Helper Verb-Predicate-Verb structure... <span lang="de">Ich werde das Buch bald lesen</span>, which if translated word-by-word is "I will the book soon read." Spanish has adjectives after the nouns they modify.

While each language has its own organizational rules, they all do the same thing. They allow us to organize and express our thinking.

## Built in Functions

Functions are used all over the place. In fact, certain tasks are so common to development that they are added to the language for all to use instead of forcing the developer to "reinvent the wheel" over and over. If you have ever added an item to an array with `push()` you have used one of these pre-built function provided as part of JavaScript. If you need a review of some of the other built in functions for Arrays visit [Array Built in methods](../../array-methods/).

## Functions - a fundamental organization concept of JavaScript

Python and JavaScript, being related languages, both have functions as a fundamental organizational structure. When you truly begin thinking in JavaScript, you will be thinking in functions. You will think of how functions are related to each other. You will have thoughts along these lines, "If this function calls that one..." You will be able to do this since you will eventually realize that when you are designing solutions in JavaScript, how a function accomplishes something is not as important as that it will, and that you can wait to figure out how to complete the function later.

### Well built functions

A well thought out and constructed function should be rather small. A function should ideally do **one** thing, and do it well. As you are writing functions, stop often to evaluate how many different things your functions are being asked to do. If the list becomes long, stop and break some of the functionality out into another function.

## Declaring functions

In Python and JavaScript there are similarities and differences between the languages regarding how you declare functions. In JavaScript, the 'function' keyword is used instead of 'def'. Also, in JavaScript the convention usually used for names of functions and variables is called 'camel case'. To create a name, the first word of the name starts with a lower-case letter, and the first letter of all the rest of the words making up the name begin with an upper-case letter. For example, a function that averages two numbers could be defined like this.

```javascript
function averageTwoNumbers(firstNum, secondNum) {
  return (firstNum + secondNum) / 2;
}
```

Notice the '{' and '}' operators. These are the JavaScript scope operators. These are used instead of the white-space scope operator used in Python. In JavaScript, white space means nothing but when writing your code, it is important to use white space to help make your code easier to read. Never left justify your code.

As with Python, JavaScript functions can have more than one line of code. The previous example could be written as

```javascript
function averageTwoNumbers(firstNum, secondNum) {
  let sum = firstNum + secondNum;
  let avg = sum / 2;
  return avg;
}
```

It does exactly the same thing, it's just broken up into multiple lines of code. There is something of great importance to note in his little example. JavaScript and Python share the same scope rules. When let or const are used within the scope operators in JavaScript, the variable or constant exists only within that scope. In other words, the sum and avg variables declared between the scope operators for this function cannot be accessed outside of this function.

JavaScript does have another keyword, var, that can be used to [hoist](https://developer.mozilla.org/en-US/docs/Glossary/Hoisting) the variable outside of its declaring scope, but it can cause logic errors in your code and has fallen out of favor with most developers and engineers. You should rarely use it, and only when you have a great deal of experience with JavaScript.

## Another Way to Write Functions

Having seen the traditional way of declaring a function, it is important that you know there are other ways to create functions. In JavaScript functions are Objects. That means that anything we can do with an Object, we can do with a function. Including assigning them to variables. When we do this it is called a 'function expressions' in the JavaScript community. Here is the averageTwoNumbers function written using the expression type syntax.

```javascript
let averageTwoNumbers = function (firstNum, secondNum) {
  let sum = firstNum + secondNum;
  let avg = sum / 2;
  return avg;
};
```

There is also now a shorthand form of an anonymous function called an Arrow function. It would look like this:

```javascript
let averageTwoNumbers = (firstNum, secondNum) => {
  let sum = firstNum + secondNum;
  let avg = sum / 2;
  return avg;
};
```

Arrow functions have become very popular when used as callback functions (a function passed into another function), but you may also see them used for function expressions.

Regardless of which method you use to create it, you would still call averageTwoNumbers using exactly the same syntax, `averageTwoNumbers(15,10)`. So what then is the difference? Why would you choose one way over the other?

The JavaScript language has a concept called 'global scope'. When you use the traditional function declaration syntax, your function is created and lives in this global scope. An advantage of this is that you could write code using the function declaration that used the function BEFORE the function declaration like many other languages allow. Here's a simple, syntactically correct example.

```javascript
averageTwoNumbers(15, 20);
/*
 *
 * a bunch of other code goes here
 *
 */

function averageTwoNumbers(firstNum, secondNum) {
  let sum = firstNum + secondNum;
  let avg = sum / 2;
  return avg;
}
```

Wow. This does seem pretty good. It does come with a drawback. When the global space becomes too cluttered, the speed of code execution is impacted. Too many global functions produces slow code.

OK then, why not just use the expression syntax? If you tried to do this...

```javascript
averageTwoNumbers(15, 20);
/*
 *
 * a bunch of other code goes here
 *
 */

let averageTwoNumbers = function (firstNum, secondNum) {
  let sum = firstNum + secondNum;
  let avg = sum / 2;
  return avg;
};
```

your code will fail to run since the averageTwoNumbers function doesn't exist prior to calling it. To make it work you would need to do this instead.

```javascript
let averageTwoNumbers = function (firstNum, secondNum) {
  let sum = firstNum + secondNum;
  let avg = sum / 2;
  return avg;
};
/*
 *
 * a bunch of other code goes here
 *
 */
averageTwoNumbers(15, 20);
```

When you use the function expression syntax (with a normal anonymous function OR an arrow function), the use of the function has to happen *after* the function is created.

One question that usually comes up when using the expression syntax is, "Hey...aren't we just storing a function in a variable? If so, could we change the function stored in the variable?" The answer is yes though this is often an advanced JavaScript programming concept. If, on the other hand, your variable was a const instead of a let, no such change could be made.

So which way should we use to create functions? There are lots of opinions on that topic. This short article expresses one common opinion: [function expressions vs function declarations](https://gomakethings.com/function-expressions-vs-function-declarations/).

## Functions under the hood

It can be helpful to understand how Javascript works under the hood when you write your code. Codesmith created a wonderful video series that explains what happens when your Javascript code is executed. Watch the first segment now:
[An Introduction to Functions, Execution Context and the Call Stack](https://www.youtube.com/watch?v=exrc_rLj5iw). (22min)
