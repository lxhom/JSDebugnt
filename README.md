# JSDebugnt

JSDebugn't is a 1-line JS script that blocks the JS Debugging Console in browsers.

## Demo

See the [demo page](https://lxhom.github.io/JSDebugnt/demo.html) ([source code](/demo.html))

## JS Source

[JS Source file](/debugnt.js)

`setInterval(_=>console.log("%c"+("i".repeat(9999)+"\n").repeat(100),"font-size:1px;font-family:sans-serif;"),100)`

## Full explanation

[Full explanation file](/debugnt-explanation.js)

```js
// Script used to block the browser console. It uses CSS styled console
// messages to completly block the renderer of the console, making the 
// console unusable without freezing the devtools or the webpage.
// (The devtools might freeze entirely, but they usually still work
// even though the console itself is completly dead.)
// Note: Most modern browsers show a "Show more" button when a console
// message is larger than 10KB, I mention this in a comment below.

setInterval(                                             // Set interval
  _ =>                              // Arrow function w/ "_" as argument
    console.log(                                     // Write to console
    "%c" + (                             // Insert CSS from 2nd argument
      "i"                         // Shortest letter in sans-serif fonts
      .repeat(9999) +            // Repeat 9999x to get below 10KB limit
      "\n"               // Newline to ensure that all i's are on screen
      ).repeat(100),                                 // Repeat 100 times
      "font-size: 1px;" + // Set tiny font size to render a lot of chars
      "font-family: sans-serif;"   // Use sans-serif to get shortest i's
    ),                                              // Console write end
100)                                        // Set the interval to 100ms
```
