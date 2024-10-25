---
title: Regex - Introduction
description: Getting started with Regular Expressions
date: 2024-10-25

layout: layouts/post.njk
---

## Definition

Regular expressions are a sequence of characters that defines a search pattern. They are used to match, find, replace, or split text based on the pattern.

They are be very simple:

`^cat`: find the first thing that starts with the characters "cat",

 or very complex:

 `^(19|20)\d\d[- /.](0[1-9]|1[012])[- /.](0[1-9]|[12][0-9]|3[01])$`: find valid formatting for dates.

 They use a series of metacharacters to build strings that when interpreted can match just about any sort of pattern. For example in the first example `^cat`, the `^` symbol means "starts with", and in the second example you can see `\d` which indicates we are looking for a digit (0-9). Here is a [Regex cheat sheet](https://www.rexegg.com/regex-quickstart.php) if you want to see them all.

The best way to learn how to write and understand regular expressions is to actually use them. Go visit [RegexOne](https://regexone.com), complete the tutorial, then come back.

## Use cases

1. Input Validation:
    - Email validation: Ensure that email addresses follow a valid format.
    - Password validation: Check if passwords meet specific criteria (e.g., length, complexity).
    - Phone number validation: Verify that phone numbers are in a correct format.
    - Data format validation: Validate dates, times, and other data types.
2. Text Processing:
    - Search and replace: Find and replace specific patterns within text.
    - Data extraction: Extract relevant information from text (e.g., URLs, phone numbers).
    - Text formatting: Apply formatting rules to text (e.g., capitalization, hyphenation).
    - Text sanitization: Remove unwanted characters or HTML tags.
3. URL Parsing:
    - Extract components: Extract parts of a URL like protocol, hostname, path, and query parameters.
    - Validate URLs: Check if a URL is valid and well-formed.
4. Code Generation:
    - Template engines: Generate dynamic content based on templates and data.
    - Code formatting: Apply consistent formatting rules to code.
5. Text Analysis:
    - Natural language processing: Analyze text for sentiment, keywords, or other linguistic features.
    - Data mining: Extract patterns or insights from large datasets.
6. Security:
    - Input sanitization: Prevent injection attacks by filtering user input. (For example you could check some user input with `.*[<].*` to see if it contains any HTML)

## Using regular expressions in coding

The tutorial makes it easy to try writing regular expressions, but how do we actually use them on real tasks?  We will show three different use cases. First in a modern code editor (VSCode), and second with HTML, and finally with a programming language...in this case Javascript.

### Regex in editors.

Most modern code editors support regular expressions in their search and replace features. To see how this can work open up an HTML file in VSCode. Open the find dialog (cmd/ctrl-f). Notice that there are three icons in the box. The first if you press it will cause the search to match case, the second enables word matching instead of substring, and the last one that looks like `.*` enables regular expressions. Thats it...just click that button to toggle it on.

Try entering `<([A-Z][A-Z0-9]*)\b[^>]*>(.*?)</\1>` This will identify any valid sets of opening and closing tags. Or `[ \t]+$` will find any lines that have trailing whitespace.

### Regex in HTML

In HTML we can use regular expressions to check user input in forms.  HTML input elements have a `pattern` attribute we can add to specify the regex we want to apply to the input. For example we might want to make sure that the user enters a date in a specific format: "yyyy/mm/dd": `^(19|20)\d\d[- \/.](0[1-9]|1[012])[- \/.](0[1-9]|[12][0-9]|3[01])$`

>Try to break down that regex to understand how it works. If you need a little help try using [Regex101](https://regex101.com)

### Regex in code

Each programming language will have certain places where regular expressions can be used. In Javascript for example you can use them in the following built in methods:

- `String.prototype.match()`: returns an array of matches
- `String.prototype.replace()`: replaces matches with a string
- `String.prototype.search()`: returns the index of the first match
- `String.prototype.split()`: splits a string into an array of substrings
- `RegExp.prototype.test()`: returns true if the string matches the regex
- `RegExp.prototype.exec()`: returns an array of matches

Here are some examples of how these can be used:

```javascript
const regex = /hello/g; // g flag for global matching
const str = "hello world, hello again";

// Using test()
console.log(regex.test(str)); // Output: true

// Using exec()
console.log(regex.exec(str)); // Output: ["hello", "index": 0, "input": "hello world, hello again"]

// Using match()
console.log(str.match(regex)); // Output: ["hello", "hello"]

// Using replace()
console.log(str.replace(regex, "hi")); // Output: "hi world, hi again"

// Using search()
console.log(str.search(regex)); // Output: 0

// Using split()
console.log(str.split(regex)); // Output: ["", " world, ", " again"]
```

>Notice on the first line of the example the expression is not quoted!  Quotes are string literals. We use them to define strings. In Javascript Regular expressions are not strings, but are a special type of object. Just like we use the Array literals `[]` to initialize an Array, or the Object literals `{}` to create an Object, we use `/` to create a regular expression.
