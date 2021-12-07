---
title: JS Loops - Ponder activities.
description: Practice using loops
date: 2021-10-15

layout: layouts/post.njk
---

## Review

### for-of

Replacement for the for loop. Array.forEach or Array.map are usually better options if you are looping over an array (which you often are).

### for-in

This allows you to iterate over objects. It returns the key of the item instead of the value like for of. If you find yourself reaching for this often you should probably take a look at how you are storing your data...

### while

while is great for when you need to do something until a certain state occurs in your program. You know when you want the loop to end...but aren't sure how many loops it will require to get there.

## Preparation

Make sure you read through the Prepare section for this topic. You will also need your editor open with some html and JavaScript code:

### html

```html
<!-- loops.html -->
<html>
  <head>
    <title>Loop Activities</title>
    <script src="loops.js" defer></script>
  </head>
  <body>
    <ul id="favorite-foods"></ul>
    <dl id="places-lived"></dl>
  </body>
</html>
```

### Javascript

```javascript
// loops.js
myInfo = {
  name: "Brother T",
  photo: "images/photo.jpg",
  favoriteFoods: ["Fettucini", "Steak", "Chicken", "Shrimp", "Baked Potato"],
  hobbies: ["Reading", "Fishing", "Camping"],
  placesLived: [
    {
      place: "Rexburg, ID",
      length: "5 years",
    },
    {
      place: "Ammon, ID",
      length: "3 years",
    },
    {
      place: "Sandy, UT",
      length: "1 year",
    },
  ],
};
// Step 4: For each favorite food in the favoriteFoods property, create an HTML <li> element and place its value in the <li> element
let favoriteFood1 = document.createElement("li");
favoriteFood1.textContent = myInfo.favoriteFoods[0];

let favoriteFood2 = document.createElement("li");
favoriteFood2.textContent = myInfo.favoriteFoods[1];

let favoriteFood3 = document.createElement("li");
favoriteFood3.textContent = myInfo.favoriteFoods[2];

let favoriteFood4 = document.createElement("li");
favoriteFood4.textContent = myInfo.favoriteFoods[3];

// Step 5: Append the <li> elements created above as children of the HTML <ul> element with an ID of favorite-foods
document.querySelector("#favorite-foods").appendChild(favoriteFood1);
document.querySelector("#favorite-foods").appendChild(favoriteFood2);
document.querySelector("#favorite-foods").appendChild(favoriteFood3);
document.querySelector("#favorite-foods").appendChild(favoriteFood4);
```

These activities will be most effective if you TRY them first before you look at the solution. And after you do look at the solution...DO NOT copy and paste the code. Read through it, try to understand what it is doing...then go fix your code.

## Activity 1

The code above will output the elements in an Array to the DOM. The provided solution above showed doing that one list element at a time, but this produces a lot of duplicated code and is tedious even for short lists. Loops would be a much better way to approach that problem. How can we use loops to make this more DRY?

1. Decide which type of loop would be best for this task.

   <div class="callout">

   What would be an appropriate loop to use? A basic `while` loop is useful for when we don't know how many times we need to loop. In this case we do: as many times as we have elements in the array. So a basic `for` loop is good for when we know how many loops we need to make. But if you remember back to the reading it mentioned that anytime we are looping over an array we should look at `.forEach()` or `.map()`

   It is worthwhile to take a look at both options.

   </div>

2. Write a function using a `.forEach` method to loop over an array and output it's contents in a `<ul>`
3. Write a function using a `.map` method to loop over an array and output it's contents in a `<ul>`
4. Test your functions.

<details>
<summary>Solution 1</summary>

```javascript
// with .forEach
const foodsElement = document.querySelector('#favorite-foods');
function createandAppendFoodItem(food) {
  let favoriteFood = document.createElement('li');
  favoriteFood.textContent = food;
  foodsElement.appendChild(favoriteFood);
}
myInfo.favoriteFoods.forEach(createAndAppendFoodItem);
}

// with .map
  const foodsElement = document.querySelector('#favorite-foods');
  function mapFoodItem(food) {
    let favoriteFood = document.createElement('li');
    favoriteFood.textContent = food;
    return favoriteFood;
  }
  // this function could also be written this way using a template literal:
  function mapFoodItemSmall(food) {
    return `<li>${food}</li>`;
  }
  const foodListElements = myInfo.favoriteFoods.map(mapFoodItem);
  // we need to flatten the array of strings into one big string. .join does this.
  foodsElement.innerHTML = foodListElements.join('');
```

</details>

## Activity 2

Another way that we could implement the `map` version of our code above would be with an arrow function. Our code could be written like this:

```javascript
// The map example could be simplified as below:
const foodsElement = document.querySelector("#favorite-foods");
const foodListElements = myInfo.favoriteFoods.map((food) => `<li>${food}</li>`);
// we need to flatten the array of strings into one big string. .join does this.
foodsElement.innerHTML = foodListElements.join("");
```

In fact that example could be simplified even further:

```javascript
// OR we could in fact simplify this down to one line!
document.querySelector("#favorite-foods").innerHTML = myInfo.favoriteFoods
  .map((food) => `<li>${food}</li>`)
  .join("");
```

As you look at the third one line version of this what do you think? Which do you prefer? How easy is it to figure out what is going on looking at that compared to one of the more verbose examples above? Discuss with a classmate how you feel about the example above.

Simplification is a good thing, but it can be taken too far and make code harder to read and understand. Sometimes it's worth typing a few more characters to have readable code. **Readable code = maintainable code**

## Activity 3

What if we needed to output the contents of multiple different Arrays? Can you make what we did above more re-usable?

1. Create a function that will take a food string and return that string embedded in some html. (`<li>food</li>`)
2. Create a function that will take a place string and return that string embedded in some html. The place is a bit more complex. We have the location and the length. You can use the following for the template: `<dt>${place.place}</dt><dd>${place.length}</dd>`)
3. Create a function that will take a list, and a callback function to produce an HTML template. The function should transform our list by looping over it calling the template function once for each item in the list. The function should return all of the HTML strings flattened into one long string.
4. Call the function above once for the `placesLived` list and again for the `favoriteFoods` list. Set the innerHTML of the appropriate HTML element to the results of the function call.

<details>
<summary>Solution 3</summary>

```javascript
// reusable!
myInfo = {
  name: "Brother T",
  photo: "images/photo.jpg",
  favoriteFoods: ["Fettucini", "Steak", "Chicken", "Shrimp", "Baked Potato"],
  hobbies: ["Reading", "Fishing", "Camping"],
  placesLived: [
    {
      place: "Rexburg, ID",
      length: "5 years",
    },
    {
      place: "Ammon, ID",
      length: "3 years",
    },
    {
      place: "Sandy, UT",
      length: "1 year",
    },
  ],
};
const foodsElement = document.querySelector("#favorite-foods");
const placesElement = document.querySelector("#places-lived");
// requires a list, and a callback that will produce an html string for each item in the list
// returns a string of html
function generateListMarkup(list, templateCallback) {
  const htmlList = list.map(templateCallback);
  return htmlList.join("");
}
// requires an food string
// returns that string embedded in HTML markup
function foodsTemplate(food) {
  return `<li>${food}</li>`;
}

// requires an place string
// returns that string embedded in HTML markup
function placesTemplate(place) {
  return `<dt>${place.place}</dt><dd>${place.length}</dd>`;
}

foodsElement.innerHTML = generateListMarkup(
  myInfo.favoriteFoods,
  foodsTemplate
);
placesElement.innerHTML = generateListMarkup(
  myInfo.placesLived,
  placesTemplate
);
```

</details>
