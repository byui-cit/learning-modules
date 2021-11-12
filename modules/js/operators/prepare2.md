---
title: JS Operators - Conditionals and Branching
description: How we can use conditionals to create branches in our code.
date: 2021-10-15

layout: layouts/post.njk
---

## Choice Making and Computational Flow

JavaScript and Python share a set of structures used to control which part of your code is executed, based on specific situations. The idea of situational 'computational flow' control isn't unique to Python or JavaScript. It is found in all languages though the way it is accomplished can be different. The boolean operators you studied in [part 1](../prepare1/) of this module are used by the control structures you will see below.

## If

In JavaScript, the [if...else if....else](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/if...else) statement takes this form,

```javascript
if(boolean expression){
	//code if true
}
else if(boolean expression){
	//code if true
}
else{
	//code if no other match
}
```

Notice the boolean expressions have parenthesis around them, and the JavaScript scope operators are used to indicate what lines of code executes in each condition. Here is a code example that evaluates the number of sales of product a company has for one day. The first condition checks if the number of sales is less than or equal to 50. Since the first check has been done, the second actually tests if the number of sales is greater than 50 and less than or equal to 1000. The default, 'else', is the number of sales being greater than 1000.

```javascript
if (numSales <= 50) {
  console.log("Way to few sales");
} else if (numSales <= 1000) {
  console.log("Average number of sales");
} else {
  console.log("A good number of sales.");
}
```

## Switch

There is another way to control your code that behaves similar to an if-else if-else statement. It's called a [switch](https://www.w3schools.com/js/js_switch.asp). It can be very helpful if you have large numbers of cases to check. Just be careful using it. It is VERY easy for those not familiar with them to put logic errors in their code using switches.

Switch is an alternative to if...else It's useful when you have a known set of values that you need to check.

```javascript
let grade = "A";
let gpaPoints = 0;
switch (grade) {
  case "A":
    gpaPoints = 4;
    break;
  case "B":
    gpaPoints = 3;
    break;
  default:
    gpaPoints = -1;
}
```

With a switch the `break;` is very important to understand. Look at the example below

```javascript
function gpaPoints(grade) {
  let gpaPoints = 0;
  switch (grade) {
    case "A":
      gpaPoints = 4;
    // break removed
    case "B":
      gpaPoints = 3;
      break;
    case "C":
      gpaPoints = 2;
    default:
      gpaPoints = -1;
  }
  return gpaPoints;
}

gpaPoints("A"); // returns 3!
gpaPoints("B"); // also returns 3
gpaPoints("C"); // returns -1!
gpaPoints("X"); // returns -1
```

Once the switch finds a match, it will continue evaluating the cases that follow until it sees a `break`
