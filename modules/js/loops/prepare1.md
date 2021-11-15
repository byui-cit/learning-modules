---
title: Javascript Loops
description: Becoming familiar with the methods or looping in JavaScript
date: 2021-10-15

layout: layouts/post.njk
---

## Getting Loopy

One thing that often confuses people learning how to program in any language is that there is often many different ways to accomplsih something. Loops in JavaScript are no exception. This module will review some of the more common and talk about when each might be appropriate.

## Looping over Arrays

One of the most common looping tasks is that of taking a list of things, and looping over them doing something with each item in the list. JavaScript has built in map, reduce, and filter functions for arrays. It also has a forEach loop that is used with arrays. Visit the [Array Methods](../../array-methods/) module if you need a review.

Maybe, you are asked to print each of the like values from a list to the console. You could use the forEach function to do this.

```javascript
likeCounts.forEach((aCount) => console.log(aCount));
```

Here is an important piece of advice. If you are looping over an array use map, filter, reduce, forEach, or some combination of them to accomplish your task. `forEach` should probably be the last one you reach for as well. It should rarely ever be used.

## The for-in Loop

This is NOT the same as the python for-in loop. Its purpose is to iterate over the properties of an object, allowing you to manipulate or print out the property values associated with each key. We'll use the Lactated Ringers medication object from last week in this example. You could print out each of the values for Lactated Ringers like this.

```javascript
let medications = {
  "Lactated Ringers": {
    id: "13ab7",
    amount: 100,
    amountType: "L",
    expDate: "12/30/2029",
  },
  Levothyroxine: {
    id: "at342",
    amount: 2000,
    amountType: "ct",
    expDate: "03/18/2021",
  },
  Rosuvastatin: {
    id: "gr5423",
    amount: 1500,
    amountType: "ct",
    expDate: "09/01/2020",
  },
  Albuterol: {
    id: "iuy6532",
    amount: 1325,
    amountType: "ct",
    expDate: "01/01/2023",
  },
  Esomeprazole: {
    id: "mnb78932",
    amount: 23145,
    amountType: "ct",
    expDate: "10/01/2021",
  },
};

let aMedication = medications["Lactated Ringers"];
for (propertyName in aMedication) {
  console.log(aMedication[propertyName]);
}
```

`for-in` is very helpful when you do need to loop over an object, but if you find yourself needing it often you might want to review how your data in structured in your application. Try to structure it in such a way that you do not need to iterate over objects often.

## The for-of Loop

The for-of loop IS the same as the Python for-in loop. It can, but shouldn't, be used to iterate over the elements of a list, set, map, or other type of data structure. It won't iterate over the properties of a defined object.

```javascript
let ages = [3, 5, -1];
for (anAge of ages) {
  console.log(anAge);
}
```

## The for Loop

Here is the traditional C-like for loop. If you are looping over an array (the most common thing we do with loops) please don't use this! You should really look at .map, .filter, .reduce or .forEach as they are MUCH better suited to that. Sometimes you just need to do something (not dealing with arrays) a known number of times. The for loop is good for that.

```javascript
for(let i = 1, i <=10, i++){
	console.log(i)
}
```

## The while Loop

Like Python's while loop, JavaScript's while loop works with a single boolean logic check to assess the state of your application by assessing one or more boolean logic statements. As long as the logic statements are true, the loop continues looping. Otherwise it stops. This is useful when you need to loop an unknown number of times, but again, you will rarely need to use this loop if you wisely apply map, filter, and reduce.

```javascript
let total = 0;
while (total < 10) {
  console.log(total);
  total++;
}
```
