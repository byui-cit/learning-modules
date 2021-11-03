---
title: Array Methods - Ponder activities.
description: Practice using Array methods
date: 2021-10-15

layout: layouts/post.njk
---

## Preparation

Make sure you read through the Prepare section for this topic. You will also need your editor open with some html:

### html

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

These activities will be most effective if you TRY them first before you look at the solution. And after you do look at the solution...DO NOT copy and paste the code. Read through it, try to understand what it is doing...then go fix your code.

## Activity 1 - Map

[map](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map) is great when we need to change each item in an array somehow. It returns a new array and does NOT modify the original array.

```javascript
let new_array = arr.map(function callback( currentValue[, index[, array]]) {
    // return element for new_array
}[, thisArg])
```

The syntax looks very similar to `forEach`, but notice that it needs a variable to store the new array it will return. We also need to make sure that the callback function we provide returns a value...usually the modified version of the array element.

1. Declare an array with value = `['one', 'two', 'three']`
2. Convert our array of strings into an array of HTML strings. Each string should be turned into a list item. For example: "&lt;li&gt;one&lt;/li&gt;"
3. Set our list of HTML strings into the **myList** list. (Hint...checkout the [.join()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/join) method.)

<details>
<summary>Solution 1</summary>

```javascript
// example 1
const steps = ["one", "two", "three"];
const stepsHtml = steps.map(function (step) {
  return `<li>${step}</li>`;
});
document.getElementById("myList").innerHTML = stepsHtml.join();
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
2. Using `filter` keep only the fruits that are longer than 6 characters.

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
2. Declare a luckNumber variable with the value 21;
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
