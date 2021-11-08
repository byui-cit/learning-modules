---
title: DOM Events - Ponder
description: Practice using DOM Events
date: 2021-10-15

layout: layouts/post.njk
---

## Preparation

Make sure you read through the Prepare section for this topic. You will also need your editor open with some html and the code from the Prepare activity:

### html

```html
<!-- events.html -->
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Events practice: ToDos</title>
    <style>
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
    <h1>ToDos</h1>
    <section>
      <label for="todo">Enter Task</label>
      <input name="todo" id="todo" />
      <button id="submitTask">Enter</button>
    </section>
    <ul id="todoList" class="todos"></ul>
    <script src="events.js"></script>
  </body>
</html>
```

### Javascript

```javascript
// events.js
let tasks = [];

function renderTasks(tasks) {
  // get the list element from the DOM
  // make sure it is empty
  // loop through the tasks array. for each of them we need to add the HTML markup for a todo.
}

function newTask() {
  // get the value entered into the #todo input
  // add it to our arrays tasks
  // render out the list.
}

function removeTask(taskElement) {
  // note the use of Array.filter to remove the element from our task array
  tasks = tasks.filter(
    (task) => task.detail != taskElement.childNodes[0].innerText
  );
  // this line removes the HTML element from the DOM
  taskElement.remove();
}

function completeTask(taskElement) {
  // In this case we need to find the index of the task so we can modify it.
  const taskIndex = tasks.findIndex(
    (task) => task.detail === taskElement.childNodes[0].innerText
  );
  // once we have the index we can modify the complete field.
  // tasks[taskIndex].completed ? false : true is a ternary expression.
  // If the first part is true (left of the ?), then the value on the left of the : will get returned, otherwise the value on the right of the : will be returned.
  tasks[taskIndex].completed = tasks[taskIndex].completed ? false : true;
  // toggle adds a class if it is not there, removes it if it is.
  taskElement.classList.toggle("strike");
  console.log(tasks);
}

function manageTasks(event) {
  // did they click the delete or complete icon?
  console.log(event.target);
  console.log(event.currentTarget);
  // event.target will point to the actual icon clicked on. We need to get the parent li to work with however. HINT: Remember element.closest()? Look it up if you don't

  // because we added 'data-function="delete"' to each icon in a task we can access a dataset property on our target
  // use that in a couple of if statements to decide whether to run removeTask or completeTask
}

// we need to attach listeners to the submit button and the list. Listen for a click, call the 'newTask' function on submit and call the 'manageTasks' function if either of the icons are clicked in the list of tasks.
```

These activities will be most effective if you TRY them first before you look at the solution. And after you do look at the solution...DO NOT copy and paste the code. Read through it, try to understand what it is doing...then go fix your code.

## Activity 1

There are 3 functions to be written, and some events to listen for to complete this simple Todo list application. Begin by reviewing the code you were given. Pay attention to the comments!

1. Start with the `newTask` function. Get the value entered in the '#todo' input, then add it to the `tasks` array, and finally call the `renderTasks` function.
2. After completing that attach an event listener to the '#submitTask' button that will call the `newTask` function when it is clicked.
3. After making sure that it is working, complete the `renderTasks` function next. You can use the following for the markup for each task:
   ```javascript
   `<li ${task.completed ? 'class="strike"' : ""}>
      <p>${task.detail}</p>
      <div>
        <span data-function="delete">❎</span>
        <span data-function="complete">✅</span>
      </div>
    </li>`;
   ```
4. Finally we can write the `manageTasks()` function. When someone clicks the ❎ it should call the `removeTask()` function. If they click the ✅ then the `completeTask()` should be called.

<div class="callout">

One way to approach this would be to attach a listener to each button for each task. But if we up with many tasks that is a lot of listeners to keep track of. Instead we can take advantage of [Event Delegation](https://davidwalsh.name/event-delegate).

If we click on one of the icons the event will 'bubble' up to the list item and look for an event listener there. It will then bubble up to the UL and look for a listener there...so we could simply attach one listener to the parent UL ('#todoList') to catch any click in our list!

One problem though...how do we know which button on which task was clicked? `event.currentTarget` always contains a reference to the element the listener is attached to. `event.target` always references the element that triggered the event! (the element clicked on in this case)

If you look at the HTML you were provided for a task you will see `data-function="delete"` on the delete icon. This is a custom HTML attribute. The 'data-' is significant. Because we used that preface the browser will package that up for us making it easy to access. If we inspect `event.target.dataset.function` should see either 'delete' or 'complete' depending on which icon was clicked. Those we can use in if statements to decide which function to call: `removeTask()` or `completeTask()`

 </div>

<details>
<summary>Solution 1</summary>

```javascript
let tasks = [];

function renderTasks(tasks) {
  const listElement = document.querySelector("#todoList");
  listElement.innerHTML = "";
  tasks.forEach((task) => {
    listElement.innerHTML += `
    <li ${task.completed ? 'class="strike"' : ""}>
      <p>${task.detail}</p>
      <div>
        <span data-function="delete">❎</span>
        <span data-function="complete">✅</span>
      </div>
    </li>`;
  });
}

function newTask() {
  const task = document.querySelector("#todo").value;
  tasks.push({ detail: task, completed: false });
  renderTasks(tasks);
}

function removeTask(taskElement) {
  tasks = tasks.filter(
    (task) => task.detail != taskElement.childNodes[0].innerText
  );
  taskElement.remove();
}

function completeTask(taskElement) {
  const taskIndex = tasks.findIndex(
    (task) => task.detail === taskElement.childNodes[0].innerText
  );
  tasks[taskIndex].completed = tasks[taskIndex].completed ? false : true;
  taskElement.classList.toggle("strike");
  console.log(tasks);
}

function manageTasks(e) {
  // did they click the delete or complete icon?
  console.log(e.target);
  const parent = e.target.closest("li");
  if (e.target.dataset.function === "delete") {
    removeTask(parent);
  }
  if (e.target.dataset.function === "complete") {
    completeTask(parent);
  }
}

document.querySelector("#submitTask").addEventListener("click", newTask);
document.querySelector("#todoList").addEventListener("click", manageTasks);

renderTasks(tasks);
```

</details>
