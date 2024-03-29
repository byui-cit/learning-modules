---
title: Debugging - Ponder activities.
description: Practice Debugging
date: 2021-10-15

layout: layouts/post.njk
---

## Preparation

You will need your editor open with some html and the code:

### html

```html
<!-- debugging.html -->
<html>
  <head>
    <title>Debug Activities</title>
    <script src="debugging.js"></script>
  </head>
  <body></body>
</html>
```

### Javascript

```javascript
const PI = 3.14;
const radius = 3;
let area = 0;
area = radius * radius * pi;
radius = 4;
area = radius * radius * pi;
```

These activities will be most effective if you **try** them first before you look at the solution. And after you do look at the solution...**do not** copy and paste the code. Read through it, try to understand what it is doing...then go fix your code.

## Activity 1

We have a few errors to fix in the code above.

1. First we must address the initial syntax error: "pi is not defined". Why are we getting that error? Review the code and fix it.
2. Once that error is fixed we will find that there is another syntax error: "Assignment to constant variable." Fix this one as well.
3. After that the code runs with no errors. But there is no indication of whether it worked correctly. Insert some `console.log()` statements to review what is happening.

<details>
<summary>Solution 1</summary>

```javascript
const PI = 3.14;
let radius = 3;
let area = 0;
area = radius * radius * PI;
console.log("Area1:", area);
radius = 4;
area = radius * radius * PI;
console.log("Area2:", area);
```

</details>

## Activity 2

You may have noticed that have repeated lines of code in our example. This is usually a sign that we need a function. Let's refactor our code (programmer speak for change) by adding a function that will calculate the area of a circle if given a radius value.

1. Create a function called `circleArea`. In Javascript a simple function takes the form:

```javascript
function circleArea(radius) {
  // code to complete our task here
}
```

2. Refactor (change) our code to make the function work. Use the code below:

  ```javascript
  const PI = 3.14;
  let area = 0;
  function circleArea(radius) {
    const area = radius * PI;
  }
  area = circleArea(3);
  console.log(area);
  ```

3. If you use the function above, you will notice that we get 'undefined' as our result. We have another error. but this one is not showing up in the Console. Put a breakpoint on the line where we use our function. Then refresh the page and this time instead of **Step Over** use the **Step Into** button (It will be an arrow pointing down right next to Step Over)
4. See if you can figure out what is wrong and Fix it.
5. Once you have solved that there is one more logic error. See if you can find it!

<details>
<summary>Solution 2</summary>

```javascript
const PI = 3.14;
// let radius = 3;
let area = 0;

function circleArea(radius) {
  const area = radius * radius * PI;
  return area;
}

area = circleArea(3);
console.log("Area1:", area);
// radius = 4;
area = circleArea(4);
console.log("Area2:", area);
```

</details>
