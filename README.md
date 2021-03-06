# html2jsx.js [![Build Status](https://travis-ci.org/SamyPesse/html2jsx.js.png?branch=master)](https://travis-ci.org/SamyPesse/html2jsx.js)

> Pure-JS HTML to Jsx parser that also works in webworker.

Since [html2jsx](https://github.com/reactjs/react-magic/blob/master/README-htmltojsx.md) from React is using the DOM (or jsdom in Node.js) to parse the HTML, it can't be used in webworkers. **html2jsx.js** is using a pure javascript html parser instead of the dom.

### Usage

Install it from NPM using:

```
$ npm install html2jsx.js
```

Then simply parse html into Jsx using:

```js
var html2jsx = require('html2jsx.js');

html2jsx('<h1>Hello World</h1>', function(err, jsx) {
    // jsx == 'React.createElement("h1", null, [ "Hello World" ])'
    console.log(jsx);
});
```

You can also provide your own components:

```js
html2jsx('<p>This is some math: <TeX>a = b + 1</TeX></p>', {
    components: ['TeX']
}, function(err, jsx) {
    // jsx == 'React.createElement("p", null, [ "This is some math: ", React.createElement(TeX, null, [ "a = b + 1" ]) ])'
    console.log(jsx);
});
```
