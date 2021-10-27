---
title: HTML Semantics - Resource name
description: Getting started with making asynchronous requests with Fetch
date: 2021-10-15

layout: layouts/post.njk
---

## AJAX: asynchronous requests

**AJAX** stands for Asynchronous Javascript And Xml. It is a collection of technologies that allow a webpage to make a request to a server after it has loaded for additional information. The requests are Asynchronous in that the program the made them does not wait around doing nothing until they come back...it will move on and do more stuff, the requests are made with Javascript, but they don't often return XML anymore. Most often now you will get the information back as JSON.

Originally the requests were made using [XmlHttpRequest](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest/Using_XMLHttpRequest), and you will still see that around, but more and more developers are turning to the newer [fetch](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch) command to make their requests.

## Promises

The asynchronous nature of these requests is a blessing and a curse. A blessing because the developer has no control over how quickly or slowly the server responds. So if the request was made synchronously nothing else could happen until the request finished. If the server you are waiting for is slow, it will make your application slow...not good. So asynchronous requests allow our code to interact with external sources while still being performant.

Asynchronous programming is a bit different to work with however. You have to deal with the fact that your code might not run in the order you wrote it. This is the curse. There are two main ways for dealing with this. One we have talked about before...callback functions. They have been used for a while now, but often lead to code that is really hard to follow...[callback hell](http://callbackhell.com/) is what it is often called.

The newer method for writing asynchronous code is **Promises**. Promises essentially give us another way to say "when you finish your thing...`then` do this next thing". The best way to understand them is by seeing them in practice. Luckily for us fetch uses promises.

<figure class="video-container">
<iframe width="560" height="315" src="https://www.youtube.com/embed/a3Srum6o5Oo" title="BYU-I Hackathon 2021" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</figure>
