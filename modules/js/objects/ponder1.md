---
title: JS Objects - Ponder activities.
description: Practice using Objects
date: 2021-10-15

layout: layouts/post.njk
---

## Preparation

It is recommended to review [Objects - Representing data](../prepare1) before you start. You will also need your editor open with some HTML:

### HTML

```html
<!-- courses.html -->
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Courses and sections</title>
    <script src="courses.js" defer></script>
  </head>
  <body>
    <h1 id="courseName"></h1>
    <h2 id="courseCode"></h2>
    <label for="sectionNumber">Section Number</label>
    <input id="sectionNumber" />
    <button id="enrollStudent">Enroll Student</button>
    <button id="dropStudent">Drop Student</button>

    <table>
      <thead>
        <tr>
          <th>Section#</th>
          <th>Room#</th>
          <th>#Enrolled</th>
          <th>Days</th>
          <th>Instructor</th>
        </tr>
      </thead>
      <tbody id="sections"></tbody>
    </table>
  </body>
</html>
```

### Javascript

```javascript
// courses.js
const aCourse = {
  code: "CSE121b",
  name: "Javascript Language",
};
```

These activities will be most effective if you **try** them first before you look at the solution. And after you do look at the solution...**do not** copy and paste the code. Read through it, try to understand what it is doing...then go fix your code.

## Activity 1

Use objects and encapsulation to create a representation of a school schedule

1. Review the object literal you were given represent a course. It includes the course name and course number.

   ```javascript
   const aCourse = {
     code: "CSE121b",
     name: "Javascript Language",
   };
   ```

    <div class="callout">

   Notice a couple of things.

   - This is similar to a Dictionary in Python. Objects in Javascript are collections of `key:value` pairs.
   - The keys are strings but do not always need to be quoted. It's never an error to quote them, but becomes necessary if the key has a space in it. For example if instead of `code` we wanted to make the key more specific and call it `course code` we would need to do this: `"course code": "CSE121b"`. But in most cases you would be better off to use `courseCode` instead.
   - The `key` is on the left side of the colon and the value is on the right.
   - The values can be anything that can be assigned to a variable in Javascript: primitives, arrays, other objects, functions...
   - Keys that store data are called properties, keys that store functions are called methods

    </div>

2. In order to assign students to a course so it can be taught one or more sections must be created. Add a `sections` property to the object (a new `key:value` pair). Since a course can have more than one section, make this an array. A section will look like this:

  ```javascript
  { sectionNum: 1, roomNum: 'STC 353', enrolled: 26, days: 'TTh', instructor: 'Bro T'},
  { sectionNum: 2, roomNum: 'STC 347', enrolled: 28, days: 'TTh', instructor: 'Sis A'}
  ```

3. Create a function to set the name and number of the course in the HTML. Pass the course object into your function (remember that you can use the dot notation to access the parts of an object.)
4. Create another function that will output the sections into the table identified by `#sections`. You should pass the sections you want rendered into the function.

<details>
<summary>Solution 1</summary>

```javascript
const aCourse = {
  code: "CSE121b",
  name: "Javascript Language",
  sections: [
    {
      sectionNum: 1,
      roomNum: "STC 353",
      enrolled: 26,
      days: "TTh",
      instructor: "Bro T",
    },
    {
      sectionNum: 2,
      roomNum: "STC 347",
      enrolled: 25,
      days: "TTh",
      instructor: "Sis A",
    },
  ],
};

function setCourseInfo(course) {
  const courseName = document.querySelector("#courseName");
  const courseCode = document.querySelector("#courseCode");
  courseName.textContent = course.name;
  courseCode.textContent = course.code;
}

function sectionTemplate(section) {
  return `<tr>
    <td>${section.sectionNum}</td>
    <td>${section.roomNum}</td>
    <td>${section.enrolled}</td>
    <td>${section.days}</td>
    <td>${section.instructor}</td></tr>`
}

function renderSections(sections) {
  const html = sections.map(sectionTemplate);
  document.querySelector("#sections").innerHTML = html.join("");
}

setCourseInfo(aCourse);
renderSections(aCourse.sections);
```

</details>

## Activity 2

The next part will see us add a method to our object that can be used to modify the object itself. In order to do this we need to understand `this`.

<div class="callout">

One important concept when using Object Literals is `this`. "`this`" is a keyword in Javascript. When you create an object it creates a reference to itself. That reference is called `this`. We will need to use that reference in our methods for them to work.

For example inside our `enrollStudent` method we will need to access the `sections` portion of our object. We have to tell the code where to look for `sections`. In english it would sound like this: 'Look inside of the current object for a property called `sections`'. In code it looks thus:

```javascript
this.sections;
```

</div>

1. Add a a new key to your object called `enrollStudent`. The value of this key should be an anonymous function that takes one argument: `sectionNum`. Functions added to objects like this are commonly referred to as methods. This method will allow us to add a student to a section.

<div class="callout">

`this` gets set normally when we call a method with the dot operator. So for example if we did this:

```javascript
aCourse.enrollStudent(1);
```

Then `this` would be equal to `aCourse`.
`this` will be equal to whatever is on the left side of the dot.

</div>

2. Complete the `enrollStudent` method. It should find the section that was given in `this.sections`. Check out [Array.findIndex()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/findIndex) if you are not sure how to find the right section.
3. If the section exists, then add 1 to `enrolled`, and then call the renderSections function to show our change
4. Create another method called `dropStudent(section)`. Subtract 1 from `enrolled` if the section passed in is found.
5. Add two event listeners to your code. One for the `#enrollStudent` button that will call out enrollStudent method, and another for the `#dropStudent` button. The event handler function in each case should grab the contents of the `#sectionNumber` input and pass it into the appropriate function.
   <div class="callout">

   Think about `this` and an event listener. We could setup the listener like this:

   ```javascript
   document.querySelector('#enrollStudent`)
    .addEventListener('click', function(e) {
     //what would the value of 'this' be inside this function?
   })
   ```

   Remember that `this` gets assigned to the object on the left side of a '.' In this case it would be equal to the `#enrollStudent` element. This can sometimes cause problems if the event listener is set inside of another object and we expected `this` to be the parent object!

   Javascript developers run into this situation often. There are two common solutions:

   1. Arrow functions have one special feature. They do not rebind `this`. So sometimes you can solve the issue by changing your `function(e) {}` to `(e) => {}`

   2. If that doesn't work then the other option is to [bind](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/bind) the value that you want `this` to be to a method.

   ```javascript
   anObject.aMethod.bind(thisArg);
   ```

<details>
  <summary>Solution 2</summary>

```javascript
const aCourse = {
  code: "CSE121b",
  name: "Javascript Language",
  sections: [
    {
      sectionNum: 1,
      roomNum: "STC 353",
      enrolled: 26,
      days: "TTh",
      instructor: "Bro T",
    },
    {
      sectionNum: 2,
      roomNum: "STC 347",
      enrolled: 25,
      days: "TTh",
      instructor: "Sis A",
    },
  ],
  enrollStudent: function (sectionNum) {
    // find the right section...Array.findIndex will work here
    const sectionIndex = this.sections.findIndex(
      (section) => section.sectionNum == sectionNum
    );
    if (sectionIndex >= 0) {
      this.sections[sectionIndex].enrolled++;
      renderSections(this.sections);
    }
  },
  dropStudent: function (sectionNum) {
    // find the right section...Array.findIndex will work here
    const sectionIndex = this.sections.findIndex(
      (section) => section.sectionNum == sectionNum
    );
    if (sectionIndex >= 0) {
      this.sections[sectionIndex].enrolled--;
      renderSections(this.sections);
    }
  },
};

function setCourseInfo(course) {
  const courseName = document.querySelector("#courseName");
  const coursecode = document.querySelector("#courseCode");
  courseName.textContent = course.name;
  coursecode.textContent = course.code;
}

function renderSections(sections) {
  const html = sections.map(
    (section) => `<tr>
    <td>${section.sectionNum}</td>
    <td>${section.roomNum}</td>
    <td>${section.enrolled}</td>
    <td>${section.days}</td>
    <td>${section.instructor}</td></tr>`
  );
  document.querySelector("#sections").innerHTML = html.join("");
}

document.querySelector("#enrollStudent").addEventListener("click", function () {
  const sectionNum = document.querySelector("#sectionNumber").value;
  aCourse.enrollStudent(sectionNum);
});
document.querySelector("#dropStudent").addEventListener("click", function () {
  const sectionNum = document.querySelector("#sectionNumber").value;
  aCourse.dropStudent(sectionNum);
});

setCourseInfo(aCourse);
renderSections(aCourse.sections);
```

</details>

## Activity 3 - Stretch!

Take a look at the `enrollStudent` and `dropStudent` methods. Notice how much of the code is the same!

How could you refactor (change) these methods to have less duplication? How could they be combined into one function? Make that change.

<details>
<summary>Solution 3</summary>

```javascript
changeEnrollment: function (sectionNum, add = true) {
    // find the right section...Array.findIndex will work here
    const sectionIndex = this.sections.findIndex(
      (section) => section.sectionNum == sectionNum
    );
    if (sectionIndex >= 0) {
      if (add) {
        this.sections[sectionIndex].enrolled++;
      } else {
        this.sections[sectionIndex].enrolled--;
      }
      renderSections(this.sections);
    }
  }
```

</details>
