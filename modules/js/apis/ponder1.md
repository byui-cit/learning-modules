---
title: APIs - Ponder activities.
description: Practice using APIs
date: 2024-07-31

layout: layouts/post.njk
---

## Preparation

It is recommended to review [APIs - Introduction](../prepare1) before you start. You will also need your editor open with some html and the code from the Prepare activity:

### html

```html
<!-- api.html -->
<html>
  <head>
    <title>API Activities</title>
    <script src="api.js" defer></script>
  </head>
  <body></body>
</html>
```

### Javascript

```javascript
// api.js
const baseUrl = "https://developer.nps.gov/api/v1/";

async function getJson(endpoint) {
  // replace this with your actual key
  const apiKey = "YOUR_API_KEY";
  // construct the url: baseUrl + endpoint + parameters
  const url = baseUrl + endpoint;
  // set the options. The important one here is the X-Api-Key
  const options = {
    method: "GET",
    headers: {
      "Content-Type": "application/json",
      "X-Api-Key": apiKey
      }
  }
  // make the request
  const response = await fetch(url, options)
  const data = await response.json()
  console.log(data)
  return data;
}

getJson('alerts?parkCode=acad,dena');
```

These activities will be most effective if you TRY them first before you look at the solution. And after you do look at the solution...DO NOT copy and paste the code. Read through it, try to understand what it is doing...then go fix your code.

## Activity 1

The key to being able to successfully use an API is spending time with it's documentation to that you understand what data it makes available, and how to get it. We will use the [NPS API](https://www.nps.gov/subjects/developer/get-started.htm) for this activity.  If you have not done so you will need to follow that link and request an API key to complete this activity.

1. On the [documentation page](https://www.nps.gov/subjects/developer/api-documentation.htm) you should enter your api key in to be able to use their tools to more quickly test things. Click on the "Authorize" button at the top of the page and enter your key.
2. What URL would you use to get a list of parks involving Idaho?  You can use the "Try it out" tool to test your answer.
3. What URL would you use to find information about campgrounds available at City of Rocks?
4. How could you find out which parks offer the activity: Climbing
5. What URL would you use to pull up any photos available involving bears?

<details>
<summary>Solution 1</summary>

2. https://developer.nps.gov/api/v1/parks?stateCode=id
3. https://developer.nps.gov/api/v1/campgrounds?parkCode=ciro
4. https://developer.nps.gov/api/v1/activities/parks?q=climbing
5. https://developer.nps.gov/api/v1/multimedia/galleries?q=bears

</details>

## Activity 2

Now that we have identified some URLs with information of interest, let's use Javascript to pull and display some of the details. We will display a list of parks that offer Climbing as an activity.

1. Add a ul element to our html to hold a list. (`<ul id="outputList"></ul>`)
2. Get that element with Javascript
3. Change the url that we are using to make the request to `activities/parks?q=climbing`. Check out the data that was returned to make sure you understand what is available. Note that the results we need are in a property called `data` which is an array of objects. Then inside of that we have a property called `parks` which is also an array of objects. This is the array we will need to loop over to output the results.
4. Create two functions: `async function renderClimbingList() {}` and `function listTemplate(item) {}`
5. Write the template function first. We should include the Name of the park, the state it is in, and make the name a link which links to the official URL for the park
6. In the `renderClimbingList` function we need to use the `getJson` function provided earlier to get the data we need. Then `map` over the list of parks using the template function. Then output the resulting HTML to the list created in step 1
7. Call the `renderClimbingList` function at the end of the script.

<details>
<summary>Solution 2</summary>

```javascript
const baseUrl = "https://developer.nps.gov/api/v1/";

async function getJson(endpoint) {
  // replace this with your actual key
  const apiKey = "YOUR_API_KEY";
  // construct the url: baseUrl + endpoint + parameters
  const url = baseUrl + endpoint;
  // set the options. The important one here is the X-Api-Key
  const options = {
    method: "GET",
    headers: {
      "Content-Type": "application/json",
      "X-Api-Key": apiKey
      }
  }
  // make the request
  const response = await fetch(url, options)
  const data = await response.json()
  console.log(data)
  return data;
}

function listTemplate(item) {
  return `<li><a href="${item.url}">${item.fullName}</a> ${item.states}</li>`
}

async function renderClimbingList() {
  const endpoint = "activities/parks?q=climbing"
  const listElement = document.getElementById("outputList")
  const data = await getJson(endpoint)
  const parks = data.data
  const listHtml = parks.map(listTemplate).join("")
  listElement.innerHTML = listHtml;
}
renderClimbingList()

```

</details>
