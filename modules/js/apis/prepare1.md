---
title: APIs - Introduction
description: What are API's? And how can we use them?
date: 2021-10-15

layout: layouts/post.njk
---

## What are APIs

API stands for Application Programming Interface. It is a set of defined rules that enables different applications to communicate with each other. An API endpoint is accessed through a URL. You make a request to a specific URL, and data instead of HTML is returned.

Most APIs are designed according to certain rules to make them consistent and easy to use. One of the most common set of rules used is called REST (Representational State of Resource). REST APIs are stateless, cacheable, and use HTTP methods to perform actions.

Web servers are designed to accept different types of requests. For example if we wanted to view a webpage that a server had, we would make a `GET` request to the URL of that page. The browser handles the request for us, so we normally don't have to worry about the request type.  We could also make a `POST` request. This usually involves sending data to a URL. This is commonly used by HTML forms. Other common request types include `PUT`, and `DELETE`.

We accessing an API we might make a `GET` request to the following URL: `https://some.server.com/users`  This would most likely return a list (usually in JSON format) of users from the server. But we could also make a `POST` request to the same URL, and if we sent the data representing a new user along with the request then the server would insert that user into where ever it was storing users.

Likewise we might make a `put` request to this URL: `https://some.server.com/user/1`  This would indicate that we were sending some updated user information for the user with an ID of 1, and that the server should update that user accordingly.  Finally if we made a `delete` request to that same URL, the server would delete user 1.

Most public APIs do not allow `post`, `put`, or `delete` requests, but restrict users to `get`. A good API will also have detailed documentation to help users to know which URLs to use to get the data they are looking for.

## Using API documentation

Let's take a look at some API documentation. We will start with a simple API...the [PokeApi](https://pokeapi.co). On the first page of the site they give an example of using the API to request the data for the Pokemon Ditto. Notice that the first part of the URL is static...they don't let you change it: `https://pokeapi.co/api/v2/`  This part of the URL will always be the same for every request. It is commonly referred to as the **base URL**.  The end part will change with each request based off of the data we need.  In this case we use `pokemon/ditto`. Use the `pokemon` endpoint, and find the data for `ditto`. How would you pull data for `charmander`?

Open the [Documentation](https://pokeapi.co/docs/v2) page. What URL would you use to pull data for the available berries in the Pokemon games? What if you wanted detailed information  about the berry `Cheri`? How would you pull that data?

<details>
<summary>Answer</summary>

1. For all berries: `https://pokeapi.co/api/v2/berry/` Try entering that URL in a new browser tab.
2. For a specific berry: `https://pokeapi.co/api/v2/berry/cheri` or `https://pokeapi.co/api/v2/berry/1`

</details>

Poke around some more in the documentation to get a feel for what else you can request from this API.

## Parameters

Some API endpoints allow you to further customize your request through a query string parameter. These are added onto the end of the URL with a `?`. For example the PokeApi restricts it's responses to 20 records by default.  If you wanted to get more than 20  records, you could add a `limit` parameter to your request. For example: `https://pokeapi.co/api/v2/pokemon/?limit=100`  This would return the first 100 records.  You can also use the `offset` parameter to skip over records. For example: `https://pokeapi.co/api/v2/pokemon/?offset=20&limit=100`  This would return records 21-120.

## CORS

When we make a request to an API, the browser will automatically add a header to the request called `Origin`. This is used to identify the domain that the request is coming from. The server can then use this information to decide whether or not to allow the request to proceed. This is called CORS (Cross-Origin Resource Sharing). If the server does not allow the request, the browser will block it. This is a security feature to prevent malicious scripts from making requests on behalf of the user. If you are trying to make a request to an API from a browser, you will need to make sure that the server allows requests from your domain.

## Authentication

Some APIs are totally public and can be used by anyone, the PokeApi is one example of these. Other APIs are protected and you need to prove that you shuold be allowed to access it. This can happen in many forms, but often involves a unique API key that is issued to you that you must send with every request.

The [NPS API](https://www.nps.gov/subjects/developer/get-started.htm) is one such API. You can request a key that you should then use.  Other APIs are more restrictive, you might have to pay and use a login to request access.

You will need to look at the documentation for the API you want to use to see exactly how they wat you to send the key, but the NPS API uses a fairly common method, sending the key in the `header` information of the request. We will use the URL in the Getting started page as an example. It is requesting the alerts from two parks.

```javascript
const baseUrl = "https://developer.nps.gov/api/v1/";

async function getJson(endpoint) {
  // replace this with your actual key
  const apiKey = "YOUR_API_KEY";
  // construct the url: baseUrl + endpoint + parameters
  const url = baseUrl + endpoint;
  // set the options. The important one here is the X-Api-Key
  const options = {
    method: "GET",
    headers: {
      "Content-Type": "application/json",
      "X-Api-Key": apiKey
      }
  }
  // make the request
  const response = await fetch(url, options)
  const data = await response.json()
  console.log(data)
}

getJson('alerts?parkCode=acad,dena`);
```
