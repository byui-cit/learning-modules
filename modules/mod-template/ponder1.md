---
title: Module Name - Ponder activities.
description: Practice using Fetch
date: 2021-10-15

layout: layouts/post.njk
---

## Preparation

It is recommended to review [APIs - Introduction](../prepare1) before you start. You will also need your editor open with some html and the code from the Prepare activity:

### html

```html
<!-- fetch.html -->
<html>
  <head>
    <title>Fetch Activities</title>
    <script src="main.js"></script>
  </head>
  <body></body>
</html>
```

### Javascript

```javascript
// main.js
const url = "https://pokeapi.co/api/v2/pokemon/ditto";
let results = null;
// takes a fetch response and checks to make sure it was OK.
// then returns the body of the response as a PROMISE to some JSON.
function convertToJson(response) {
  if (response.ok) {
    return response.json();
  } else {
    console.log("error:", response);
  }
}
// this is where we would do whatever we needed to do with the resulting data.
function doStuff(data) {
  results = data;
  console.log("first: ", results);
}
// read this as: make a request to URL, WHEN it finishes THEN run convertToJson
// WHEN it finishes THEN run doStuff
fetch(url).then(convertToJson).then(doStuff);
// meanwhile...continue with the rest of the program...
console.log("second: ", results);
```

These activities will be most effective if you TRY them first before you look at the solution. And after you do look at the solution...DO NOT copy and paste the code. Read through it, try to understand what it is doing...then go fix your code.

## Activity 1

Our doStuff function in the example above is a bit underwhelming...lets make it do more than just console log out. It should really display the data that we retrieved to the user in the browser. We need a list!

1. Add an element to our HTML to hold the pokemon data...something like `<section id="output"></section>`
2. Get that element with javascript. (`document.querySelector`)
3. In the `doStuff` function create a variable and build out the html that we want to display the information. (I recommend a template literal string)
4. Insert our HTML into the output element (innerHTML)

<details>
<summary>Solution 1</summary>

```javascript
function doStuff(data) {
  const outputElement = document.querySelector("#output");
  results = data;
  const html = `<h2>${results.name}</h2>
                <img src="${results.sprites.front_default}" alt="Image of ${results.name}">`;
  outputElement.innerHTML = html;
  console.log("first: ", results);
}
```

</details>

## Activity 2

As interesting as Ditto is...it would be more fun to get information on lots of pokemon...if we make a slight change to the URL we are making the request to, we can get a list of pokemon instead of just one. Let's do that and then make a new function called `doStuffList` that will output the list.

1. Add a ul element to our html to hold the list. (`<ul id="outputList"></ul>`)
2. Get that element with Javascript
3. Change the url that we are using to make the request to `const url = "https://pokeapi.co/api/v2/pokemon";`
4. Create a function: `function doStuffList(data) {}`
5. In the function start by console.logging **data**. Take a look at the structure of what got sent back. Notice that our list is inside of a property called results
6. Create a variable called `pokeList` and set it equal to `data.results`
7. for each of the pokemon in the list: create a line of html to output it (`<li>${pokeList.name}</li>`
8. Add the new list to what was already in our output element.
9. Change your fetch call to use the `doStuffList` function instead of `doStuff`

<details>
<summary>Solution 2</summary>

```javascript
function doStuffList(data) {
  console.log(data);
  const pokeListElement = document.querySelector("#pokeList");
  const pokeList = data.results;
  pokeList.forEach((currentItem) => {
    const html = `<li>${currentItem.name}</li>`;
    // note the += here...
    pokeListElement.innerHTML += html;
  });
}
```

</details>

## Activity 3 - Stretch!

Our pokemon list is not alphabetized...we should fix that.

Create a function: `function sortPokemon(list) {}`
Check out some documentation on `Array.sort`. [MDN: Sort](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort). Notice that it provides an example compare function at the bottom...we can use that as a model.

```javascript
function compare(a, b) {
  if (a is less than b by some ordering criterion) {
    return -1;
  }
  if (a is greater than b by the ordering criterion) {
    return 1;
  }
  // a must be equal to b
  return 0;
}
```

<details>
<summary>Solution 3</summary>

```javascript
function compare(a, b) {
  if (a.name > b.name) {
    // sort b before a
    return 1;
  } else if (a.name < b.name) {
    // a and b different but unchanged (already in the correct order)
    return -1;
  } else return 0; // a and b are equal
}

function sortPokemon(list) {
  let sortedList = list.sort(compare);
  return sortedList;
}
function doStuffList(data) {
  console.log(data);
  const pokeListElement = document.querySelector("#outputList");
  const pokeList = data.results;
  // sort our list before output it
  pokeList = sortPokemon(pokeList);
  pokeList.forEach((currentItem) => {
    const html = `<li>${currentItem.name}</li>`;
    //note the += here
    pokeListElement.innerHTML += html;
  });
}
fetch(url).then(convertToJson).then(doStuffList);
```

</details>
