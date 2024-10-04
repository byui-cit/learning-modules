---
title: URL Search Parameters - Introduction
description: What are URL search parameters and how can we use them?
date: 2024-10-04

layout: layouts/post.njk
---

## What are URL search parameters?

URL search parameters serve as a mechanism to pass additional information to a web server or another web page, typically for the purpose of dynamic content generation or data retrieval.

They are often used to:

- Perform searches: Specify search terms or criteria to filter results.
- Filter data: Apply conditions to narrow down the displayed information.
- Paginate results: Indicate the page number or offset for large datasets.
- Sort data: Determine the order in which results are presented.
- Submit forms: Transmit form data to the server for processing.
- State changes: Update the state of a web application, such as adding items to a cart or changing a user's preferences.

## Format

URL search parameters are appended to the end of a URL, starting with a `?` character, followed by a series of key-value pairs separated by `&` characters. Each key-value pair consists of a parameter name and its corresponding value.

### Example

```bash
https://example.com/search?q=hello+world&lang=en&sort=desc
```

In this example, the URL has three search parameters:

- `q`: The search query, set to "hello world".
- `lang`: The language, set to "en" (English).
- `sort`: The sort order, set to "desc"  (descending).

Notice as well that the space character in "hello world" has been replaced by a `+`. A space is not a valid character that can be used in a parameter value (it would break the URL in fact), and so it is encoded to something else that is ok. Any special characters you use must be encoded! A special character is anything but letters, numbers, and `-`, `.`, `_`, `~`

## Best Practices

When working with URL search parameters, it's essential to:

- Use meaningful and consistent parameter names.
- URL-encode special characters in parameter values to ensure they are properly transmitted. (See [encodURIComponent](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/encodeURIComponent))
- Keep parameter values concise and avoid using sensitive or confidential information.

## Using search parameters

Search parameters always have the same format: `?someKey=someValue&someotherKey=SomeOtherValue`.  Decodings these strings is a very common action with web development. Because of this the browser has built in functions to help.

Information about a web page location is found in `window.location`. Open up a webpage, then open up the developer tools and switch to the console tab. Enter `window.location` into the prompt. You should see something like this:

```javascript
{
    "ancestorOrigins": {},
    "href": "https://www.google.com/search?q=urlsearchparams&sourceid=chrome&ie=UTF-8",
    "origin": "https://www.google.com",
    "protocol": "https:",
    "host": "www.google.com",
    "hostname": "www.google.com",
    "port": "",
    "pathname": "/search",
    "search": "?q=urlsearchparams&sourceid=chrome&ie=UTF-8",
    "hash": ""
}
```

Notice that in the example there were some URL parameters. The browser helpfully has already parsed the URL to separate out the search string. We still need to take that string and break it up into the individual keys and values however. Luckily the browser is not done helping us.

We can use [URLSearchParams](https://developer.mozilla.org/en-US/docs/Web/API/URLSearchParams) to do this parsing for us. For example if we wanted to get the value sent for the query (q), we could do the following:

```javascript
const paramsString = window.location.search
const params = new UrlSearchParams(paramsString);
const query = params.get('q');
```

This will give us the value of the q parameter. If there were no q parameter, it will return `null`. If you want to get all the parameters, you can use the `getAll()` method.
