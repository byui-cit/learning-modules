---
title: Array Methods - Core concepts
description: Most array methods follow a similar pattern. This activity will show this pattern and how to read technical documentation to apply the pattern to any of the methods.
date: 2021-10-15

layout: layouts/post.njk
---

## Built in functions

Most programming languages are faced with similar problems that need to be solved. Eventually solutions to some of the most common problems get added directly into the language as built in functions. Some of the common areas where you will see this in JavaScript are [Dates](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date), [Math operations](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math), and [Arrays](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)

## Array built in functions

If we enter something like `[1,2,3]` in the console of a browser we will see our array show up with an arrow, if we expand the array by clicking on the arrow we see the values in our array and something that looks like this: `Prototype` or `__proto__`. Open that up and we see a bunch of stuff associated with every array. Most of the list is helper functions, methods that do useful things with arrays.

An easier way to see that list is to refer to the [Array Documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array) at MDN.

## MDN documentation

These modules pull heavily from the documentation at MDN. There are certain patterns seen commonly in coding documentation. Understanding these patterns is an important step on our journey to learn how to learn.

For example if we take a look at the [MDN page for push](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/push) we will see this:

> ## Syntax
>
> ```javascript
> push(element0)
> push(element0, element1)
> push(element0, element1, ... , elementN)
> ```
>
> ### Parameters
>
> **elementN**
> The element(s) to add to the end of the array.
>
> ### Return value
>
> The new length property of the object upon which the method was called.

The parameters and return type are particularly important. They give us the blueprint for understanding how to use the method. This is a simple one. We can send the method one or more items to be inserted into the array as parameters, and we will get back the new length of the array as a result.

Let's look at a more complex example: `forEach`

> ## Syntax
>
> ```javascript
>   arr.forEach(callback(currentValue [, index [, array]])[, thisArg])
> ```
>
> ### Parameters
>
> **callbackFn**
> Function to execute on each element. It accepts between one and three arguments:
>
> 1. element
>    The current element being processed in the array.
>
> 2. index Optional
>    The index of element in the array.
>
> 3. array Optional
>    The array forEach() was called upon.
>
> **thisArg** Optional
> Value to use as this when executing callbackFn.
>
> ### Return value
>
> Undefined

That is the official syntax for the method. How do we read that?

1. First note that we will call this method from an existing array.
2. Second notice that it expects a callback function as it's first argument. This callback can be a named function or an anonymous function.
3. The callback is where the action takes place...it defines what we want to happen for each item in the array. .forEach() will handle the looping, where to start, where to stop, and will automatically pass each item in the array one at a time into the callback function.
4. That callback function will have up to three parameters passed in that we can use.
   1. First and required is the current array value.
   2. Second (optional) the index of the current array value
   3. Third (optional) the entire array.
5. Nothing will be returned from this method.

## Callback functions

We have mentioned that in Javascript functions are special objects...but since they are objects we can do anything with functions that we can a normal object. This includes assigning functions to variables, and passing functions into other functions as arguments, as well as returning functions from functions.

When we pass a function into another function we call it a 'callback'. Many of the Array methods we will be looking at use callbacks.

The basic form for a function declaration in JavaScript is below.

```javascript
// function declaration
function square(number) {
  return number * number;
}
```

A function declaration starts with the `function` keyword, then a name, then `()` with zero or more parameters. Then there is a block `{}` where the code that we want executed when we call the function goes.

We can also make an anonymous version of this function. We just leave off the name. We could then assign that anonymous function to a variable (this is called a function expression) or pass it as an argument to a function.

```javascript
// function expression
const square = function (number) {
  return number * number;
};
```

There is also one more form functions can take that is often used in callbacks. That is the [Arrow function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions). It would look like this:

```javascript
// arrow function
const square = (number) => {
  return number * number;
};

// or when your function is simply returning a value
// it can be simplified even further:
const square = (number) => number * number;
```

Anonymous functions and arrow functions are used very often as callbacks. See examples below.

## Examples

```javascript
// example 1
const steps = ["one", "two", "three"];
// callback declaration
function makeList(item) {
  const listElement = document.getElementById("myList");
  listElement.innerHTML += `<li>${item}</li>`;
}
steps.forEach(makeList);

// example 2
// is the luckyNumber in the list?
const myArray = [12, 34, 21, 54];
const luckyNumber = 21;
let luckyIndex = -1;
myArray.forEach(function (item, index) {
  if (item === luckyNumber) {
    luckyIndex = index;
  }
});
```
