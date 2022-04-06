---
title: Fetch Basics - Ponder activities.
description: Practice using Fetch
date: 2021-10-15

layout: layouts/post.njk
---

## Preparation

Make sure you read through the Prepare section for this topic. You will also need your editor open with some html and the code from the Prepare activity:

### html

```html
<!-- fetch.html -->
<html>
  <head>
    <title>Fetch Activities</title>
    <script src="fetch.js"></script>
  </head>
  <body></body>
</html>
```

### Javascript

```javascript
// fetch.js
const url = "https://pokeapi.co/api/v2/pokemon/ditto";
let results = null;
async function getPokemon(url) {
  const response = await fetch(url);
  //check to see if the fetch was successful
  if (response.ok) {
    // the API will send us JSON...but we have to convert the response before we can use it
    // .json() also returns a promise...so we await it as well.
    const data = await response.json();
    doStuff(data);
  }
}
function doStuff(data) {
  results = data;
  console.log("first: ", results);
}
getPokemon(url);
console.log("second: ", results);
```

<div class="callout">

These activities will be most effective if you TRY them first before you look at the solution. And after you do look at the solution...DO NOT copy and paste the code. Read through it, try to understand what it is doing...then go fix your code.

</div>

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
3. Add a new url that will return a list of pokemon instead of just one
   `const urlList = "https://pokeapi.co/api/v2/pokemon";`
4. Create two functions: `function doStuffList(data) {}` and `function getPokemonList(url) {}`
5. Write the code for getPokemonList first. It should do the following:
   1. Make a fetch request to the url passed in.
   2. When the request finishes check to make sure it was ok.
   3. If it was ok then convert the response to json.
   4. Call the `doStuffList` function, passing in the data.
6. Move to the `doStuffList` function next. In the function start by console.logging **data**. Save everything and open your file in the browser. Take a look in the console at the structure of what got sent back. Notice that our list is inside of a property called **results**
7. Create a variable called `pokeList` in the doStuffList function and set it equal to `data.results`
8. for each of the pokemon in the list: create a line of html to output it
   `<li>${pokeList.name}</li>`
9. Add the new list to what was already in our output element.
10. Run the new `getPokemonList` function, passing in `urlList`.

<details>
<summary>Solution 2</summary>

```javascript
const url = "https://pokeapi.co/api/v2/pokemon/ditto";
const urlList = "https://pokeapi.co/api/v2/pokemon";
let results = null;

async function getPokemon(url) {
  const response = await fetch(url);
  //check to see if the fetch was successful
  if (response.ok) {
    // the API will send us JSON...but we have to convert the response before we can use it
    // .json() also returns a promise...so we await it as well.
    const data = await response.json();
    doStuff(data);
  }
}
async function getPokemonList(url) {
  const response = await fetch(url);
  if (response.ok) {
    const data = await response.json();
    doStuffList(data);
  }
}
function doStuff(data) {
  results = data;
  const outputElement = document.querySelector("#output");
  const html = `<h2>${data.name}</h2><img src="${data.sprites.front_default}" alt="${data.name}">`;
  outputElement.innerHTML = html;
  console.log("first: ", results);
}

function doStuffList(data) {
  console.log(data);
  const pokeListElement = document.querySelector("#outputList");
  const pokeList = data.results;
  pokeList.forEach((currentItem) => {
    const html = `<li>${currentItem.name}</li>`;
    // note the += here...
    pokeListElement.innerHTML += html;
  });
}
getPokemon(url);
console.log("second: ", results);

getPokemonList(urlList);
```

</details>

## NOTE

Did it bother any of you that our `getPokemon` function and `getPokemonList` function are almost identical? It should as it breaks the DRY principle...we are definately repeating ourselves! How can we fix this to remove the duplicated code? Think about it (hint: callbacks), then check out the alternate solution below.

<details>
<summary>Solution 2 - alternate</summary>

```javascript
const url = "https://pokeapi.co/api/v2/pokemon/ditto";
const urlList = "https://pokeapi.co/api/v2/pokemon";
let results = null;

async function getPokemon(url, doThis) {
  const response = await fetch(url);
  //check to see if the fetch was successful
  if (response.ok) {
    // the API will send us JSON...but we have to convert the response before we can use it
    // .json() also returns a promise...so we await it as well.
    const data = await response.json();
    // execute the callback
    doThis(data);
  }
}

function doStuff(data) {
  results = data;
  const outputElement = document.querySelector("#output");
  const html = `<h2>${data.name}</h2><img src="${data.sprites.front_default}" alt="${data.name}">`;
  outputElement.innerHTML = html;
  console.log("first: ", results);
}

function doStuffList(data) {
  console.log(data);
  const pokeListElement = document.querySelector("#outputList");
  const pokeList = data.results;
  pokeList.forEach((currentItem) => {
    const html = `<li data-url="${item.url}">${currentItem.name}</li>`;
    // note the += here...
    pokeListElement.innerHTML += html;
  });
}
getPokemon(url, doStuff);
console.log("second: ", results);
// Notice that by just passing a different callback function in
// we can totally change what happens when the data comes back.
// It's like we gave the getPokemon function superpowers!
getPokemon(urlList, doStuffList);
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
  let pokeList = data.results;
  // sort our list before output it
  pokeList = sortPokemon(pokeList);
  pokeList.forEach((currentItem) => {
    const html = `<li>${currentItem.name}</li>`;
    //note the += here
    pokeListElement.innerHTML += html;
  });
}
```

</details>
