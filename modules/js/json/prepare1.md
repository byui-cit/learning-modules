---
title: JSON - Introduction
description: Getting started with JSON
date: 2021-10-15

layout: layouts/post.njk
---

## JSON: JavaScript Object Notation

With web development there is a common need to send information to and from servers. This often needs to happen after the web page has loaded, asynchronously. One of the problems is that the data needs to be sent in a way that is somewhat generic so that many different platforms and languages can use it. Plain text is about as generic as it gets.

A few years ago this would be with something like an XML (eXtensible Markup Language) string. XML is a format similar to HTML...in fact HTML could be considered a subset of XML. It is very flexible, but also very verbose and hard to convert to and from the format.

JSON was developed to be a lightweight format that would be easier to work with. An important thing to remember about JSON is that it is a simple string!  A string with specific rules about how it is formatted.

### JSON is:

- text-based,
- stored in with the extension .json,
- closely paired to a literal JavaScript object and is converted to a native JavaScript object.
- not dependent on a particular programming language,
- pure property formatted data, there are no methods,
- written using basic key/value pairs in this format: key:pair data types of strings, numbers, arrays, Booleans, and other object literals,
- requires double quotes to be used around string and property names and follows strict adherence to comma or colon placement,
- can be accessed using JavaScript object notation,
- can be checked with a linter like jsonlint.com to validate the structure, and
- does not allow comments.

The [JSON](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON) object has methods that allow you to convert or [parse](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/parse) the string to an native object and we can [stringify()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify) a native object to a string using that same, built-in JSON object.

A common task would be to take a Javascript object in code like the following:

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
```

And use `JSON.stringify(aCourse)` which will convert it into a string. It would look like this:

```json
{
  "code": "CSE121b",
  "name": "Javascript Language",
  "sections": [
    {
      "sectionNum": 1,
      "roomNum": "STC 353",
      "enrolled": 26,
      "days": "TTh",
      "instructor": "Bro T"
    },
    {
      "sectionNum": 2,
      "roomNum": "STC 347",
      "enrolled": 25,
      "days": "TTh",
      "instructor": "Sis A"
    }
  ]
}
```

Note how similar the JSON is to the object! The primary difference is that the keys must be quoted with double quotes. The computer would actually view that like this:

```json
{"code": "CSE121b","name": "Javascript Language","sections": [{"sectionNum": 1,"roomNum": "STC 353","enrolled": 26,"days": "TTh","instructor": "Bro T"},{"sectionNum": 2,"roomNum": "STC 347","enrolled": 25,"days": "TTh","instructor": "Sis A"}]}
```

This string could now be sent to a server using [fetch](https://developer.mozilla.org/en-US/docs/Web/API/Window/fetch), or stored in [localStorage](https://developer.mozilla.org/en-US/docs/Web/API/Window/localStorage).

Conversely when a server sends you data back in JSON, we need to convert the string back into an actual object that we can manipulate. `JSON.parse(dataFromServer)`

>Since we usually use `fetch` to get that data from the server, we commonly use it's built-in helper method to do our conversion. It would look something like this: `response.json()`
>
>`JSON.stringify(myData)` and `response.json()` do pretty much the same thing. You do not want to use both!

## Example

Here is an example JSON file. Directly open this file with your browser: [JSON "Hero" Data Example](https://mdn.github.io/learning-area/javascript/oojs/json/superheroes.json) - MDN

<details>
<summary>Can you identify the properties and the data types?</summary>

Here are some example property names and corresponding data types from this JSON file.

- **property**: "squadName", **data type**: string
- **property**: "formed", **data type**: number
- **property**: "active", **data type**: Boolean
- **property**: "members", **data type**: holds an array of objects (the object has four properties)

</details>
