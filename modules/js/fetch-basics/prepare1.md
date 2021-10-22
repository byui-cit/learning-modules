---
title: Fetch Basics - What is AJAX and Fetch?
description: Getting started with making asynchronous requests with Fetch
date: 2021-10-15

layout: layouts/post.njk
---

## AJAX: asynchronous requests

**AJAX** stands for Asynchronous Javascript And Xml. It is a collection of technologies that allow a webpage to make a request to a server after it has loaded for additional information. The requests are Asynchronous in that the program the made them does not wait around doing nothing until they come back...it will move on and do more stuff, the requests are made with Javascript, but they don't often return XML anymore. Most often now you will get the information back as JSON.

Originally the requests were made using [XmlHttpRequest](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest/Using_XMLHttpRequest), and you will still see that around, but more and more developers are turning to the newer [fetch](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch) api to make their requests.

## Promises

The asynchronous nature of these requests is a blessing and a curse. A blessing because the developer has no control over how quickly or slowly the server responds. So if the request was made synchronously nothing else could happen until the request finished. If the server you are waiting for is slow, it will make your application slow...not good. So asynchronous requests allow our code to interact with external sources while still being performant.

Asynchronous programming is a bit different to work with however. You have to deal with the fact that your code might not run in the order you wrote it. This is the curse. There are two main ways for dealing with this. One we have talked about before...callback functions. They have been used for a while now, but often lead to code that is really hard to follow...[callback hell](http://callbackhell.com/) is what it is often called.

The newer method for writing asynchronous code is **Promises**. Promises essentially give us another way to say "when you finish your thing...`then` do this next thing". The best way to understand them is by seeing them in practice. Luckily for us fetch uses promises.

## Example

We will use fetch to pull some data from a remote API (application programming interface). An API is essentially what happens when an organization decides to expose part of a program they own to the world. Why would they do this? Well let's take Calendly for example. It is an online scheduling application. A student can go sign up for an appointment with their instructor easily with it. The University uses Microsoft Exchange for calendaring. If something doesn't show up there...I will miss it. Luckily Exchange has an API. Through this API Calendly can log into my Exchange account and add things directly to my calendar if I give it permission to.

So as soon as a student signs up for an appointment in Calendly, the appointment automatically gets added to my calendar. This is one example of when an API is very useful.

We are going to use a fairly simple free API called [pokeapi](https://pokeapi.co/). If you visit that website you will find the documentation on how to request data, and examples. Let's use the example it has to pull information about the Pokemon Ditto.

```javascript
const url = 'https://pokeapi.co/api/v2/pokemon/ditto';
const results = fetch(url);
console.log(results);'
```

There is a lot going on in that simple line of code. With it we made a request for some specific information from a remote server. Check the console and you will find however that we did not get the information yet. Just as was mentioned above fetch returns a Promise. We have to tell it what we want it to do once the promise **fulfills** or finishes what it is doing. We do that with the [.then()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/then) method.

```javascript
promise.then(onFulfilled[, onRejected]);

  promise.then(value => {
    // fulfillment
  }, reason => {
    // rejection
  });
```

`.then()` takes two parameters...one required that contains what should happen if the request was successful, and one optional that contains what should happen if the request fails.

`fetch` does not return usable data initially. Instead we have to tell it what we were expecting...and ask it to convert the response into the right kind of data. The three types it understands are `json()`, `text()` (HTML and XML would be considered text), and `blob()` (blob is anything that isn't text or json). We are expecting JSON back from the api we made the request to. So we should convert it to that.

```javascript
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

Note that the second console.log ran first...then the first one. Remember that in async programming Javascript does not wait for everything to finish before moving on. If we had tried to use `results` immediately it would have failed. Instead we do whatever we need to do with `results` in the callback that gets called by `.then()`.

## Note

Note that this would often be done with anonymous functions...without the comments and condensed the code above could look like this:

```javascript
const url = "https://pokeapi.co/api/v2/pokemon/ditto";
let results = null;
fetch(url)
  .then((response) => {
    if (response.ok) {
      return response.json();
    } else {
      console.log("error:", response);
    }
  })
  .then((data) => {
    results = data;
    console.log("first: ", results);
  });
console.log("second: ", results);
```
