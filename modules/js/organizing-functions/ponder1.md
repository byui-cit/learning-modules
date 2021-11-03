---
title: JS Functions - Ponder activities.
description: Practice using JS functions to accomplish a task in an organized and DRY manner.
date: 2021-10-15

layout: layouts/post.njk
---

## Preparation

Encapsulation: "The goal of encapsulation is the bundling or co-location of information (data) and behavior (functions) that together serve a common purpose."

"The idea is to group alike program bits together, and selectively limit programmatic access to the parts we consider private details. What's not considered private is then marked as public, accessible to the whole program."

There is a concept in programming called DRY. Don't Repeat Yourself. Which means that if we are coding and find ourselves doing the exact same thing more than once...we should find a way to re-use. Functions are made for this.

Make sure you read through the Prepare section for this topic. In particular remember the three ways to declare functions in JavaScript:

1. Function Declaration

```javascript
function mySuperFunction() {
  // Do stuff here
}
```

2. Function Expression

```javascript
const mySuperFunction = function () {
  // Do stuff here
};
```

3. Arrow Function (Lambda)

```javascript
const mySuperFunction = () => {
  // Do stuff here
};
```

## Activity 1

## GPA Calculator

If we think about a gpa Calculator app that runs in the browser, how would we organize the code for that? What does it need to do?

1. Display the options for the user
2. Accept input from the user
3. Perform the requested operation with the user provided arguments
4. Display the result of the operation

Our program could be organized into two sets of functionality: code that is responsible to receive and display information, and code that will calculate the GPA with the user supplied input.

Let's break down our functionality a bit further:

1. Display input box for user to enter grades along with a button to kick off the calculation.
2. Add an event listener to the button that will do the following when clicked:
   1. Get the string of grades from the input
   2. Convert the string to an array (String.split(',')), clean up any extra spaces, and make the grades all uppercase.
   3. Do a lookup on each grade to convert it to it's point value (ie A = 4.0)
   4. Total up all the point values, and divide by the number of grades to get the GPA
   5. Output the GPA to the browser

## Steps

1. Start by creating two files in the sandbox: gpa.html, and gpa.js. Just like before add the HTML for a basic page, and a script element linking our JS to our HTML
2. Copy the following HTML into the <body> of your HTML file:

```html
<h1>GPA Calculator</h1>
<p>Enter a comma separated list of grades.</p>
<p>
  <label for="grades">Grades</label>
  <input type="text" id="grades" placeholder="comma separated list of grades" />
</p>
<button id="submitButton">Generate</button>
<p id="output"></p>
```

3. If we review our list of steps above, we have many things to accomplish. Think about how you might organize all of that into functions. How many do we need? what should each function do? After you have considered this and formed a few opinions check out one possibility below.

<details>
<summary>Function List</summary>

```javascript
function getGrades(inputSelector) {
  // get grades from the input box
  // split them into an array (String.split(','))
  // clean up any extra spaces, and make the grades all uppercase. (Array.map())
  // return grades
}

function lookupGrade(grade) {
  // converts the letter grade to it's GPA point value and returns it
}

function calculateGpa(grades) {
  // gets a list of grades passed in
  // convert the letter grades to gpa points
  // calculates the GPA
  // return the GPA
}

function outputGpa(gpa, selector) {
  // takes a gpa value and displays it in the HTML in the element identified by the selector
}

function clickHandler() {
  // when the button in our html is clicked:
  // get the grades entered into the input
  // calculate the gpa from the grades entered
  // display the gpa
}
```

</details>

4. Start by seeing if you can implement `getGrades()`. If you are having a hard time remembering how to select an HTML element review [JS DOM Basics](../../dom-basics/). Then note that the value that is entered into an HTML `input` element can be found in it's `.value` property.

5. Add an event listener to the button in our HTML. It should call our `clickHandler` function when a click occurs. Go ahead and call the `getGrades()` function in `clickHandler` We can use that to test getGrades.

6. Move onto the 'lookupGrade()` function. In this case a long if-else statement should work. To keep it simpler don't worry about the + and - grades. Make sure to test your function to make sure it works!

7. Next is the `calculateGpa()` function. It should use the `lookupGrade()` function that we just finished. We will need to loop through our list of grades and call lookupGrade on each. Then we will need to **reduce** the list of gpa points to a total and divide it by the number of grades to get the average. Finally round the gpa to 2 decimal points.

8. The last step is to write the `displayGpa()` function, then pull it all together in the `clickHandler`

<details>
<summary>Solution (gpa.js)</summary>

```javascript
function getGrades(inputSelector) {
  // get grades from the input box
  const grades = document.querySelector("#grades").value;
  // split them into an array (String.split(','))
  const gradesArray = grades.split(",");
  // clean up any extra spaces, and make the grades all uppercase. (Array.map())
  const cleanGrades = gradesArray.map((grade) => grade.trim().toUpperCase());
  console.log(cleanGrades);
  // return grades
  return cleanGrades;
}

function lookupGrade(grade) {
  // converts the letter grade to it's GPA point value and returns it
  let points = 0;
  if (grade === "A") {
    points = 4;
  } else if (grade === "B") {
    points = 3;
  } else if (grade === "C") {
    points = 2;
  } else if (grade === "D") {
    points = 1;
  }
  return points;
}

function calculateGpa(grades) {
  // gets a list of grades passed in
  // convert the letter grades to gpa points
  const gradePoints = grades.map((grade) => lookupGrade(grade));
  // calculates the GPA
  const gpa =
    gradePoints.reduce((total, num) => total + num) / gradePoints.length;
  // return the GPA
  return gpa.toFixed(2);
}

function outputGpa(gpa, selector) {
  // takes a gpa value and displays it in the HTML in the element identified by the selector passed in
  const outputElement = document.querySelector(selector);
  outputElement.innerText = gpa;
}

function clickHandler() {
  // when the button in our html is clicked
  // get the grades entered into the input
  const grades = getGrades();
  // calculate the gpa from the grades entered
  const gpa = calculateGpa(grades);
  // display the gpa
  outputGpa(gpa, "#output");
}

document.querySelector("#submitButton").addEventListener("click", clickHandler);
```
