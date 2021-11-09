---
title: JS Objects - Ponder activities.
description: Practice using Objects
date: 2021-10-15

layout: layouts/post.njk
---

## Preparation

Make sure you read through the Prepare section for this topic. You will also need your editor open with some html :

### html

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

These activities will be most effective if you TRY them first before you look at the solution. And after you do look at the solution...DO NOT copy and paste the code. Read through it, try to understand what it is doing...then go fix your code.

## Activity 1

Use objects and encapsulation to create a representation of a school schedule

1. Create an object literal to represent a course. It should include the course name and course number.

   ```javascript
   const aCourse = {
     code: "CSE121b",
     name: "Javascript Language",
   };
   ```

    <div class="callout">

   Notice a couple of things.

   - The keys are strings and do not always need to be quoted (it's never an error to quote them, but becomes necessary if the key has a space in it).
   - After the key is a colon, then the value.
   - The values can be anything that can be assigned to a variable in Javascript: primitives, arrays, other objects, functions...
   - keys that store data are called properties, keys that store functions are called methods

    </div>

2. In order to assign students to a course so it can be taught one or more sections must be created. Add a `sections` property to the object. Since a course can have more than one section make this an array. A section will look like this:

```javascript
{ sectionNum: 1, roomNum: 'STC 353', enrolled: 26, days: 'TTh', instructor: 'Bro T'},
{ sectionNum: 2, roomNum: 'STC 347', enrolled: 28, days: 'TTh', instructor: 'Sis A'}
```

3. Create a function to set the name and number of the course in the HTML. Pass the course object into your function (remember that you can use the dot notation to access the parts of an object.)
4. Create another function that will output the sections into the table idenetified by `#sections`. You should pass the sections you want rendered into the function.

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

setCourseInfo(aCourse);
renderSections(aCourse.sections);
```

</details>

## Activity 2

The next part will see us add a method to our object that can be used to modify the object itself. In order to do this we need to understand `this`.

<div class="callout">

One important concept when using Object Literals like this is `this`. When you create an object it creates a reference to itself. That reference is called `this`. We will need to use that reference in our methods for them to work

For example inside our `enrollStudent` method we will need to access the `sections` portion of our object. We have to tell the code where to look for `sections`. In english it would sound like this: 'Look inside of the current object for a property called `sections`'. In code it looks thus:

```javascript
this.sections;
```

</div>

1. Add a method to the object that will allow us to add a student to a section. The method should take as argument the section number we are enrolling the student in. Call it `enrollstudent(sectionNum)`

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
