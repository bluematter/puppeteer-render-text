# puppeteer-render-text

> Robust text renderer using headless chrome.

[![NPM](https://img.shields.io/npm/v/puppeteer-render-text.svg)](https://www.npmjs.com/package/puppeteer-render-text) [![Build Status](https://travis-ci.com/transitive-bullshit/puppeteer-render-text.svg?branch=master)](https://travis-ci.com/transitive-bullshit/puppeteer-render-text) [![JavaScript Style Guide](https://img.shields.io/badge/code_style-standard-brightgreen.svg)](https://standardjs.com)

<p align="center">
  <img width="502" alt="Logo" src="https://cdn.rawgit.com/transitive-bullshit/puppeteer-render-text/master/media/logo.png">
</p>

## Why?

ImageMagick is the traditional unix tool to programatically [render text](http://www.imagemagick.org/Usage/text/), and while it works very well for simple use cases, trying to use it to render rich text or html is very difficult. [Pango](https://www.pango.org/) is another option that's been around for ages, but both suffer from archaic syntax and minimal rich text support.

[Puppeteer](https://github.com/GoogleChrome/puppeteer), on the other hand, allows for robust, headless chrome screenshots with best-in-class support for all modern html / text / font features.

**This module makes it easy to use headless chrome to render text + html to images.**

## Features

-   built-in [fontfaceobserver](https://fontfaceobserver.com/)
-   easily load [google fonts](https://fonts.google.com/)
-   optional word-wrap
-   main context is just **html**
-   styling is done via [**css**](https://www.w3schools.com/jsref/dom_obj_style.asp)
-   thoroughly tested

## Install

```bash
npm install --save puppeteer-render-text
```

## Usage

```js
const renderText = require('puppeteer-render-text')

// render text with built-in font and no word-wrap
await renderText({
  text: 'hello world',
  output: 'out0.png',
  style: {
    fontFamily: 'segue ui',
    fontSize: 64
  }
})

// render text with custom google font and word-wrap at 400px
await renderText({
  text: 'headless chrome is awesome',
  output: 'out1.png',
  loadGoogleFont: true,
  width: 400,
  style: {
    fontFamily: 'Roboto',
    fontSize: 32,
    padding: 16
  }
})

// render html with custom google font and custom word-wrap at 100px
await renderText({
  text: 'headless <b>chrome</b> is <span style="color: red: font-style: italic;">awesome</span>',
  output: 'out1.png',
  loadGoogleFont: true,
  width: 100,
  style: {
    fontFamily: 'Roboto',
    overflowWrap: 'break-word'
  }
})
```

Note that all CSS styles are specified via the [JS CSS syntax](https://www.w3schools.com/jsref/dom_obj_style.asp), which uses camelCase instead of hyphens. This is, for instance, what [React](https://reactjs.org/docs/dom-elements.html#style) uses for its inline styles.

## API

<!-- Generated by documentation.js. Update this documentation by updating the source code. -->

### [renderText](https://github.com/transitive-bullshit/puppeteer-render-text/blob/78fc727089da2932a8364ac7ba6550fed891e215/index.js#L40-L164)

Renders the given text / html via puppeteer.

Asynchronously returns the generated html page as a string for debugging purposes.

Type: `function (opts): Promise`

-   `opts` **[object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** Configuration options
    -   `opts.text` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** HTML content to render
    -   `opts.output` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** Path of image file to output result
    -   `opts.width` **[number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number)?** Optional max width for word-wrap
    -   `opts.height` **[number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number)?** Optional max height to clip overflow
    -   `opts.loadFontFamily` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)?** Optional font family to load with fontfaceobserver
    -   `opts.loadGoogleFont` **[boolean](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Boolean)** Whether or not to load and wait for `opts.style.fontFamily` as one or more google fonts (optional, default `false`)
    -   `opts.style` **[object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** JS [CSS styles](https://www.w3schools.com/jsref/dom_obj_style.asp) to apply to the text's container div (optional, default `{}`)
    -   `opts.inject` **[object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** Optionally injects arbitrary string content into the head, style, or body elements. (optional, default `{}`)
        -   `opts.inject.head` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)?** Optionally injected into the document <head>
        -   `opts.inject.style` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)?** Optionally injected into a <style> tag within the document <head>
        -   `opts.inject.body` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)?** Optionally injected into the document <body>

## Related

-   [puppeteer](https://github.com/GoogleChrome/puppeteer) - Headless Chrome Node API.

## License

MIT © [Travis Fischer](https://github.com/transitive-bullshit)
