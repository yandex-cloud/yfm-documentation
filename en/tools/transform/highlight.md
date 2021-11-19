# Syntax highlighting

The [highlight.js](https://www.npmjs.com/package/highlight.js) package is used to highlight code. For the list of available languages, see [Github](https://github.com/highlightjs/highlight.js/tree/master/src/languages).

To install the package, run this command:

```shell
npm i highlight.js
```

## Adding other languages {#add}

You can pass an additional set of languages that will be registered for use.

A set of languages is passed as an object, with:

* The name of the language as the key.
* A function that defines the language as the value.

```javascript
const transform = require('@doc-tools/transform');
const customLang = require('./custom-lang');

const highlightLangs = { 'custom-lang': customLang };

const {result: {html, meta}, logs} = transform(content, {highlightLangs});
```

