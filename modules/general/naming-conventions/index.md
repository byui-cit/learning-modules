


---
title: File and Folder Naming Conventions
description: File and folder naming conventions in programming - This subject can be opinionated.
date: 2021-11-08
order: 1
tags:
  - general
layout: layouts/post.njk
---

## Description

When working on the web, there are many things that affect the operation of the files—the browser, the protocol(s), the client and server operating systems, the language(s), etc. While many of these are out of your control, there are steps you can take to help keep things consistent. We label these steps and 'best-practice' procedures as the web naming rules or naming conventions and should be applied to all files and folders in this class.

Each organization may have their own guides and 'best' practices as many of these items may be platform specific.

## Where is this topic utilized?

- CSE 121b
- WDD 130
- WDD 230
- WDD 330


## Prepare

### Rules for Naming Files and Folders

Each course may have specific naming conventions. Be sure to identify them in the course material.
Example [WDD 230]
► Use all lowercase. Platforms and systems handle case sensitivity differently.

► Do NOT use spaces in names. Spaces are interrupted obtusely by user agents, therefore, do not use them. The Hypertext Transfer Protocol (HTTP) ignores spaces, except in file names. In file names, it replaces a space with a symbol—"%20." This makes URL's look confusing and can also lend itself to confusion in the mind of site visitors. So avoid using spaces. Instead, if you have to create a visual space, use underscores _ or hyphens -.

► Do NOT use special characters (es.g., <,>, \, /, #, ?, ! ). Special characters often mean specific things to computers, so just avoid using them completely in the naming of files and folders.

► Use as short and as meaningful (semantic) of names as possible. Short, meaningful names save you, other developers, and site visitors from having to remember long complicated names for files and folders. When meaningful, they also help with the predictive nature of the file or folder contents when working with those files or folders.

► 🔑In this class, the standard folder names for our sites/sub-folders are:

css  (this folder will contain our CSS files
js (this folder will contain our JavaScript files
images (this folder will contain our images)
Reference: [Dealing With Files](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/Dealing_with_files) - moz://a MDN Web Docs

Be kind and helpful to yourself and site visitors by following these simple rules. Also, be aware that for the class, you will be held accountable for doing so as this is part of the overall assessment criteria with deliverables.

<div class="callout" style="background-color: #dbf3fa; padding: 10px; border: 1px solid #dddddd; font-size: 0.9rem; margin: 0px 15px 15px; color: #000000;"><strong><span style="font-size: 14pt;">🌮 Common Naming Conventions in Programming</span><br /></strong>&nbsp; <em>The following are common case and syntax naming practices found in programming:&nbsp;</em><br />&bull; &nbsp;<strong>Camel Case </strong>- each word within a compound word name is capitalized except for the first word.&nbsp; Examples: julySales, getNewReport()<br />&bull; &nbsp;<strong>Pascal Case</strong> - each word within a compound word name is capitalized. &nbsp; Examples:&nbsp; JulySales, GetNewReport()<br />&bull; &nbsp;<strong>Underscore</strong> or <strong>Snake Case</strong> - each word within a compound word name is separated by underscores. Often found in file names but not preferred due to the fact that underlining will happen with hypertext by default, leading to confusion. Examples: july_sales, get_new_report(), soda_springs.html<br />&bull;&nbsp; <strong>Kebab Case</strong> - all the letters are lower case and each word is separated by a hyphen or minus sign. Examples: july-sales, get-new-report(), soda-springs.html<br /><br /><strong>References</strong><br />- <a href="https://developer.mozilla.org/en-US/docs/MDN/Contribute/Guidelines/Code_guidelines/JavaScript#Variable_naming">MDN JavaScript Variable Naming</a><br />- <a href="https://dev.to/danialmalik/a-beginner-s-guide-to-clean-code-part1-naming-conventions-139l">Dev.to Clean Coding</a>&nbsp;</div>

## Ponder

Consider the following examples of file names and ponder the implications of the naming.
