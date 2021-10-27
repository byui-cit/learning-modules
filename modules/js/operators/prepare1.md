---
title: JS Operators - Operators and comparisons
description: Understanding comparisons in JS and the role type coercion plays.
date: 2021-10-15

layout: layouts/post.njk
---

## Operators

### Arithmetic and Assignment Operators

Make sure you have reviewed the [JS operators](https://www.w3schools.com/jsref/jsref_operators.asp).

### Comparison Operators

Javascript has two equality comparison operators..."==": loose equality, and "===": strict equality. Both of these do approximately the same thing...they let you know if two values are the same. The difference in them is that the double equal allows for the values to be coerced (changed) before the comparison is made, while the triple equals does not.

Note that neither equality operator will allow you to check to see if the contents of an Array or other Object is the same as another. It can only check if two Arrays are the same...ie they are both bound to the same value in memory. See example below.

## Coercion

Coercion is simply the process Javascript uses when it has to do a comparison or arithmetic operation between two values that don't match. It is important to understand that it happens...and that JS has a few guidelines it follows as it is doing it.

1. Javascript prefers numeric comparisons and will coerce to a primitive numeric value if it can
2. In the case of '+' (addition or concatination). If there is a string involved...all values will be converted to strings. That's the only way JS knows to combine mixed values.

Why coercion? Javascript needs the ability to coerce values because it is [weakly typed](../../variables/prepare1/#strongly-typed-weakly-typed-what-does-that-even-mean)

## Examples

```javascript
// These would also be true with a double equals
3 === 3.0; // true
"yes" === "yes"; // true
null === null; // true
false === false; // true

42 === "42"; // false
"hello" === "Hello"; // false
true === 1; // false
0 === null; // false
"" === null; // false
null === undefined; // false
//note the difference in a double equal comparison
42 == "42"; // true...the string "42" gets coerced into the number 42
"hello" == "Hello"; // false...are you surprised at this one?
1 == true; // true...the boolean value true gets coerced into the number 1
null == undefined; //  true
```

```javascript
10 < 11; // true
42 > "42"; // false
43 > "42"; // true!  what is going on?
"a" < "b"; // true
```

```javascript
// array example
var x = [1, 2, 3];

// assignment is by reference-copy, so
// y references the *same* array as x,
// not another copy of it.
var y = x;

y === x; // true...both variables are bound to the exact same array.
y === [1, 2, 3]; // false...it might look the same, but this is NOT the same array that y is bound to.
x === [1, 2, 3]; // false
y == [1, 2, 3]; // false...doesn't work with double equal either :(
```

## Which should I use?

In most cases you should use the strict equality (triple equals) for your comparisons. The double equals is helpful when you are comparing two values where the result will be the same whether coercion happens or not, or when you don't care if the value is the same type...sometimes you want things to be coerced.

## Manual coercion

Sometimes we know that the data is in the wrong format, and need to change it to the correct type. For example if you have a user input some information in an HTML input element, and then get that information with javascript it will always be a string. What if the form was asking for the person's age so that we could tell them how old they will be in 10 years?

```html
<!-- HTML -->
<label for="age">Enter your Age</label>
<input id="age" />
```

```javascript
// get age from input
const age = document.getElementById("age").value; // assume 21 was entered
// add 10 years
const agePlus10 = age + 10;
console.log(agePlus10); // would give something like 2110 (21 + 10)
```

Remember that if Javascript is asked to add a string and a number it will coerce the number to be a string. We need to manually change the type to get this to work correctly.

```javascript
// get age from input
const age = document.getElementById("age").value; // assume 21 was entered
// add 10 years
const agePlus10 = parseInt(age) + 10;
console.log(agePlus10); // success! 31
```

There is also a `parseFloat()` function for decimal point conversion.

Much of the detail above comes from [You Don't Know JS Yet Ch 2](https://github.com/getify/You-Dont-Know-JS/blob/2nd-ed/get-started/ch2.md). Highly recommend reading to learn more.
