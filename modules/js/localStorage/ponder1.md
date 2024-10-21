---
title: localStorage - Ponder
description: Practice using localStorage
date: 2024-10-21

layout: layouts/post.njk
---

## Preparation

For this activity you are given the code for a simple To-do application that will allow you to add a task, mark a task as completed, and remove a task. The problem is that if you refresh the browser all your tasks will disappear. Not ideal. We will modify the code to use localStorage to store the tasks for us. It is recommended to review [Introduction to localStorage](../prepare1) before you start.

You will need your editor open to create a couple of new files for the following code:

### html

```html
<!-- storage.html -->
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>localStorage practice: ToDos</title>
    <script src="storage.js" defer></script>
    <style>
      header {
        display: flex;
        justify-content: space-between;
      }
      .todos {
        width: 300px;
      }
      .todos > li {
        display: flex;
        justify-content: space-between;
        align-items: center;
        border: 1px solid;
        padding: 0.5em;
      }
      .todos p {
        margin: 0;
      }
      .todos span {
        cursor: pointer;
      }
      .strike {
        text-decoration: line-through;
        color: gray;
      }
    </style>
  </head>
  <body>
    <header>
        <h1>ToDos</h1>
        <p class="user">[user name here]</p>
    </header>
    <main>
    <section>
      <label for="todo">Enter Task</label>
      <input name="todo" id="todo" />
      <button id="submitTask">Enter</button>
    </section>
    <ul id="todoList" class="todos"></ul>
    </main>
  </body>
</html>
```

### Javascript

```javascript
// storage.js
let tasks = [];

function taskTemplate(task) {
  return `
    <li ${task.completed ? 'class="strike"' : ""}>
      <p>${task.detail}</p>
      <div>
        <span data-action="delete">❎</span>
        <span data-action="complete">✅</span>
      </div>
    </li>`
}

function renderTasks(tasks) {
  // get the list element from the DOM
  const listElement = document.querySelector("#todoList");
  listElement.innerHTML = "";
  // loop through the tasks array. transform (map) each task object into the appropriate HTML to represent a to-do.
  const html = tasks.map(taskTemplate).join("");
  listElement.innerHTML = html;
}

function newTask() {
  // get the value entered into the #todo input
  const task = document.querySelector("#todo").value;
  // add it to our arrays tasks
  tasks.push({ detail: task, completed: false });
  // render out the list
  renderTasks(tasks);
}

function removeTask(taskElement) {
  // Notice how we are using taskElement instead of document as our starting point?
  // This will restrict our search to the element instead of searching the whole document.
  tasks = tasks.filter(
    (task) => task.detail != taskElement.querySelector('p').innerText
  );
  taskElement.remove();
}

function completeTask(taskElement) {
  const taskIndex = tasks.findIndex(
    (task) => task.detail === taskElement.querySelector('p').innerText
  );
  tasks[taskIndex].completed = tasks[taskIndex].completed ? false : true;
  taskElement.classList.toggle("strike");
  console.log(tasks);
}

function manageTasks(e) {
  // did they click the delete or complete icon?
  console.log(e.target);
  const parent = e.target.closest("li");
  if (e.target.dataset.action === "delete") {
    removeTask(parent);
  }
  if (e.target.dataset.action === "complete") {
    completeTask(parent);
  }
}

// Add your event listeners here
document.querySelector("#submitTask").addEventListener("click", newTask);
document.querySelector("#todoList").addEventListener("click", manageTasks);

// render  the initial list of tasks (if any) when the page loads
renderTasks(tasks);
```

These activities will be most effective if you TRY them first before you look at the solution. And after you do look at the solution...DO NOT copy and paste the code. Read through it, try to understand what it is doing...then go fix your code.

## Activity 1

Begin by reviewing the code you were given. You should take the time to set a few breakpoints and step through the code until you feel you understand how it works.  You will probably want to pay special attention to the `manageTasks` function. If you are having a hard time understanding any part of it you could even paste the code into a generative AI for an explanation.

Once you have an idea of how the code works we can do a simple implementation of localStorage to get started.

1. Add an input and button to the page requesting the user to enter their name.
2. When the button is clicked we should get the name entered and store it into localStorage with the key "todo-user", then render the name onto the page.
3. Add a new function to our javascript file called `setUser`. This function should be called when the page loads, and should check to see if a user name has already been set in localStorage. If it finds one it should get it and render it to the page.

>### Notes
>In this case we are storing and retrieving a simple string. We can simply use `localStorage.set(key, data)` and `localStorage.get(key)` to accomplish it.
>
>To check to see if the name was successfully set in localStorage you can open the developer tools and look under the "Application" tab in Chrome or the "Storage" tab in Firefox and Safari. You could also clear out (delete) any localStorage key from here.
>
>Refresh the browser page to see if the name is getting set correctly in the header.

<details>
<summary>Solution 1</summary>

```html
<section>
  <label for="user">Name</label>
  <input type="text" id="user" value="[user name here]" />
  <button id="userNameButton">Enter</button>
</section>
<hr />
```


```javascript
function setUserName() {
  const name = localStorage.getItem("todo-user");
  if (name) {
    document.querySelector(".user").innerText = name;
  }
}
function userNameHandler() {
  const name = document.querySelector("#user").value;
  localStorage.setItem("todo-user", name);
  setUserName();
}

document
  .querySelector("#userNameButton")
  .addEventListener("click", userNameHandler);

  // check to see if a user name has been set...if yes then set it in the header
setUserName();
```

</details>

## Activity 2

Now that we have seen a simple use of localStorage we are ready to move onto something a little more interesting. Storing the list of tasks.

Since we can only store strings in the value of a localStorage key, we have to convert any complex data structure like a list or object into a simple string. Luckily this is something that happens all the time in Javascript. We call this simplified string based form of a variable JSON: Javascript Object Notation. JSON is simply the string representation of a Javascript object.

Since we will be converting back and forth from a JSON string to a JS Object every time we get or set something to local storage we should start by making some functions that will simplify that for us.

1. Create a function called `setLocalStorage(key, data)`. In this function take the data that was passed in and convert it to a string. (`JSON.stringify()`), then set that string in localStorage using the key provided.
2. Create a function called `getLocalStorage(key)`. In this function take the key provided and if the key exists in localStorage, convert the string back to a JS object using `JSON.parse()`, and return that object.
3. Use these two new functions to set the list of tasks to localStorage everytime a new task is added to the list, and when a task is updated or deleted.
4. When the page initially loads we should check to see if there are any tasks in localStorage, if there are we should update the `tasks` variable, and display them.
5. Because we now have several things that must be done when the page loads to get it ready, create a function called `init` that will take care of all the setup tasks.

<details>
<summary>Solution 2</summary>

```javascript
let tasks = [];

function setLocalStorage(key, data) {
  localStorage.setItem(key, JSON.stringify(data));
}

function getLocalStorage(key) {
  const storedValue = localStorage.getItem(key);
  // check to see if something was found
  if (storedValue) {
    return JSON.parse(storedValue);
  }
  // if not return an empty array
  return [];
}

function taskTemplate(task) {
  return `
    <li ${task.completed ? 'class="strike"' : ""}>
      <p>${task.detail}</p>
      <div>
        <span data-action="delete">❎</span>
        <span data-action="complete">✅</span>
      </div>
    </li>`;
}

function renderTasks(tasks) {
  // get the list element from the DOM
  const listElement = document.querySelector("#todoList");
  listElement.innerHTML = "";
  // loop through the tasks array. transform (map) each task object into the appropriate HTML to represent a to-do.
  const html = tasks.map(taskTemplate).join("");
  listElement.innerHTML = html;
}

function newTask() {
  // get the value entered into the #todo input
  const task = document.querySelector("#todo").value;
  // add it to our arrays tasks
  tasks.push({ detail: task, completed: false });
  // SAVE the tasks array to local storage
  setLocalStorage("todos", tasks);
  // render out the list
  renderTasks(tasks);
}

function removeTask(taskElement) {
  // Notice how we are using taskElement instead of document as our starting point?
  // This will restrict our search to the element instead of searching the whole document.
  tasks = tasks.filter(
    (task) => task.detail != taskElement.querySelector("p").innerText
  );
  taskElement.remove();
  // UPDATE localStorage with the changes
  setLocalStorage("todos", tasks);
}

function completeTask(taskElement) {
  const taskIndex = tasks.findIndex(
    (task) => task.detail === taskElement.querySelector("p").innerText
  );
  tasks[taskIndex].completed = tasks[taskIndex].completed ? false : true;
  taskElement.classList.toggle("strike");
  console.log(tasks);
  // UPDATE localStorage with the changes
  setLocalStorage("todos", tasks);
}

function manageTasks(e) {
  // did they click the delete or complete icon?
  console.log(e.target);
  const parent = e.target.closest("li");
  if (e.target.dataset.action === "delete") {
    removeTask(parent);
  }
  if (e.target.dataset.action === "complete") {
    completeTask(parent);
  }
}
function setUserName() {
  const name = localStorage.getItem("todo-user");
  if (name) {
    document.querySelector(".user").innerText = name;
  }
}
function userNameHandler() {
  const name = document.querySelector("#user").value;
  localStorage.setItem("todo-user", name);
  setUserName();
}

function init() {
  // see if there are any tasks in localStorage
  tasks = getLocalStorage("todos");
  // render  the initial list of tasks (if any) when the page loads
  renderTasks(tasks);
  // check to see if a user name has been set...if yes then set it in the header
  setUserName();
}

// Add your event listeners here
document.querySelector("#submitTask").addEventListener("click", newTask);
document.querySelector("#todoList").addEventListener("click", manageTasks);
document
  .querySelector("#userNameButton")
  .addEventListener("click", userNameHandler);

init();


```

</details>
