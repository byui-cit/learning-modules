---
title: localStorage - Introduction
description: Sometimes it's nice for a web page to remember things about a user. LocalStorage is a simple way to get started with persisting data on a web page.
date: 2024-10-21

layout: layouts/post.njk
---

## What is localStorage?

`localStorage` is a key-value storage system that allows you to store data locally in a user's browser. It is a part of the Web Storage API, which also includes `sessionStorage`. Data that is stored with the Web Storage API is unique per site. By design the data stored by one website cannot be accessed by another website. The data in fact can only be accessed in the same browser on the same computer.  Data set in localStorage for a site in Chrome cannot be seen in Firefox for example.

### Differences with sessionStorage

There is another browser API called `sessionStorage` that is very similar to `localStorage`. The main difference between the two is that `sessionStorage` data is deleted when the user closes the browser (or browser tab), while `localStorage` data is preserved even after the browser is closed. This means that `localStorage` is useful for storing data that you want to persist across multiple sessions, while `sessionStorage` is better suited for storing data that is only relevant for a single session.

One other difference is that `sessionStorage` can only store 5kb of information per key, while `localStorage` can store 5Mb.

### What is localStorage used for?

localStorage is used to store data that should be persisted across page reloads and browser restarts. It is commonly used for:

- Storing user preferences, such as font size or color scheme
- Caching frequently-used data, such as API responses
- Storing small amounts of data that don't need to be sent to the server (such as items in a shopping cart)
- Implementing simple authentication mechanisms
- Creating offline-enabled web applications

## How does localStorage work?

localStorage stores data as key-value pairs, where each key is a string and each value is a string, number, or boolean. You can store, retrieve, and remove data using the following methods:

- `localStorage.setItem(key, value)`: stores a value under a given key
- `localStorage.getItem(key)`: retrieves a value by its key
- `localStorage.removeItem(key)`: removes a value by its key
- `localStorage.clear()`: removes all stored values

## Example Use Case

Here is an example of how to use localStorage to store a user's name:

```javascript
// Set the user's name
localStorage.setItem('username', 'John Doe');

// Retrieve the user's name
const username = localStorage.getItem('username');
console.log(username); // Output: "John Doe"

```

You can see what is currently stored in your browser's localStorage by opening up the developer tools in your browser and choosing "Application" if you are in Chrome, or "Storage" in most other browsers.

Often we would like to store more complex data in `localStorage`, such as data stored in Arrays or Objects. `localStorage` has a limitation that only strings may be stored in a key. So to store more complex data it would have to first be converted to a simple string representation. Luckily in Javascript this is easy as it happens all the time. Data that has been converted to a simple string representation is called JSON and the tools to convert back and forth are built into the language.

See an example of how this works below.

```javascript
// Set the user's name and age
const user = { name: 'John Doe', age: 30 };
// make sure to convert the data to a string
localStorage.setItem('user', JSON.stringify(user));

// get the name and age back from localStorage parsing it back into objects and Arrays.
const getUser = JSON.parse(localStorage.getItem('user'))
console.log(getUser.name); // Output: "John Doe"
```

### Security Considerations

`localStorage` is not suitable for storing sensitive data, such as passwords or credit card numbers, as it is accessible to any script running on the same origin (server URL). You should always validate and sanitize data stored in localStorage to prevent security vulnerabilities.
