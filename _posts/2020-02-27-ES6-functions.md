---
layout: post
title: "ES6 function syntax"
author: Zach
---

Taken from Dave Ceddia's email course [React Basics](https://daveceddia.com/pure-react-email-course/).

```javascript
// Plain function with destructed argument object
function Hi({ name }) {
    return <div>Hello {name}!</div>
}

// A constant holding an anonymous function
const Hi = function({ name }) {
    return <div>Hello {name}!</div>
}

// Removing the "function" keyword and adding the arrow after the
// parameter list
const Hi = ({ name }) => {
    return <div>Hello {name}!</div>
}

// Removing the braces, which makes the "return" implicit so we can remove
// that too.  Replacing them with parentheses for readability
const Hi = ({ name }) => (
    <div>Hello {name}!</div>
)

// Make it a one-liner
const Hi = ({ name }) => <div>Hello {name}!</div>
```
