---
title: Array Methods - Ponder activities.
description: Practice using Array methods
date: 2021-10-15

layout: layouts/post.njk
---

## Preparation

Make sure you read through [Array Methods: core concepts](../prepare1). You will also need your editor open with some HTML and JS:

### HTML

```html
<!-- arrays.html -->
<html>
  <head>
    <title>Array Activities</title>
    <script src="arrays.js"></script>
  </head>
  <body>
    <ul id="myList"></ul>
  </body>
</html>
```

### JS

```javascript
//  arrays.js
const steps = ["one", "two", "three"];
function listTemplate(step) {
  return //the html string made from step
}
const stepsHtml = // use map to convert the list from strings to HTML
document.querySelector("#myList").innerHTML = // set the innerHTML
```

These activities will be most effective if you **try** them first before you look at the solution. And after you do look at the solution...**do not** copy and paste the code. Read through it, try to understand what it is doing...then go fix your code.

## Activity 1 - Map

[map](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map) is great when we need to change each item in an array somehow. It returns a new array and does NOT modify the original array.

```javascript
let new_array = arr.map(function callback( currentValue[, index[, array]]) {
    // return element for new_array
}[, thisArg])
```

The syntax looks very similar to `forEach`, but notice that it needs a variable to store the new array it will return. We also need to make sure that the callback function we provide returns a value...usually the modified version of the array element.

You were given some of the code to complete activity 1. Look through it then follow the instructions below.

1. The `listTemplate` function should take a step and return the HTML to turn that step (a string) into a list item (HTML). For example: "one" will get converted to "&lt;li&gt;one&lt;/li&gt;" Template literal strings are great for this.
2. Use your template function and the `map` method to convert the whole list to HTML. Store the result in a variable.
3. Set our list of HTML strings into the `myList` list. (Hint...checkout the [.join()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/join) method.)

<details>
<summary>Solution 1</summary>

```javascript
// example 1
const steps = ["one", "two", "three"];
const listTemplate(step) {
  return `<li>${step}</li>`;
}
const stepsHtml = steps.map(listTemplate);
document.querySelector("#myList").innerHTML = stepsHtml.join();
```

</details>

## Activity 2 - Map

1. Declare an array with letter grades in it: `['A', 'B', 'A']`
2. Write a function that will take one letter grade, and return the appropriate gpa points for that grade. IE if we send in 'A' it should return 4.
3. Use `map` and our conversion function to convert the array in step 1 to gpa points.

<details>
<summary>Solution 2</summary>

```javascript
// example 2
const grades = ["A", "B", "A"];
function convertGradeToPoints(grade) {
  let points = 0;
  if (grade === "A") {
    points = 4;
  } else if (grade === "B") {
    points = 3;
  }
  return points;
}
const gpaPoints = grades.map(convertGradeToPoints);
```

</details>

## Activity 3 - Reduce

[reduce](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce) is useful when we need to compress an array into a single value. It is most often used when the array has at least one value that can be mathematically flattened

1. Using the function from the previous activity, convert an array of grades into an array of gpaPoints.
2. Using `reduce` calculate the GPA from the array of gpaPoints.

<details>
<summary>Solution 3</summary>

```javascript
const gpaPoints = grades.map(convertGradeToPoints);
const pointsTotal = gpaPoints.reduce(function (total, item) {
  return total + item;
});
const gpa = pointsTotal / gpaPoints.length;

// example 2
// this is the same thing as above, but with an arrow function
const pointsTotal = gpaPoints.reduce((total, item) => total + item);
const gpa = pointsTotal / gpaPoints.length;

// this could be further simplified as
const gpa = gpaPoints.reduce((total, item) => total + item) / gpaPoints.length;
```

</details>

## Activity 4 - Filter

[filter](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/Filter) is similar to map in that it returns a new array of elements. The elements in the calling array will be included in the new array if they pass a test that you include in the callback you pass in.

1. Declare an array with the following value: `['watermelon', 'peach', 'apple', 'tomato', 'grape']`
2. Using `filter` keep only the fruits that are smaller than 6 characters.

<details>
<summary>Solution 4</summary>

```javascript
const words = ["watermelon", "peach", "apple", "tomato", "grape"];
const shortWords = words.filter(function (word) {
  return word.length < 6;
});

//same thing with an arrow function
const shortWords = words.filter((word) => word.length < 6);
```

</details>

## Activity 5 - indexOf

[indexOf](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/indexOf) returns the first index at which a given element can be found in the array, or -1 if it is not present.

1. Declare an array with the following value: `[12, 34, 21, 54]`
2. Declare a luckyNumber variable with the value 21;
3. Use `indexOf` to see if the luckyNumber is in the Array.

<details>
<summary>Solution 5</summary>

```javascript
// improved luckyNumber
const myArray = [12, 34, 21, 54];
const luckyNumber = 21;
let luckyIndex = myArray.indexOf(luckyNumber);
```

</details>
