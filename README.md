# async-css-tests
A bunch of web pages for testing various "async" CSS methods in various browsers

We have a large, ~100kB `.html` file and an equally large `.css` to be downloaded on each.

## Disclaimer

All of these tests are very basic and *do not* accurately reflect real sites. **There is no substitute for running your own tests on your own site with your own browser support requirements.**

## Methods

Here's the full list of various combinations I've tried to measure. If you can think of a new one, let me know.

### Only `<link>`

* Control: regular ol' blocking `<link rel="stylesheet">` in the `<head>`
* `<link>` at the top of the `<body>`
* `<link>` at the bottom of the `<body>`
* Non-matching `media` attribute on `<link>` in the `<head>`, `<link>` at the top of the `<body>`
* Non-matching `media` attribute on `<link>` in the `<head>`, `<link>` at the bottom of the `<body>`
* Non-matching `type` attribute on `<link>` in the `<head>`, `<link>` at the top of the `<body>`
* Non-matching `type` attribute on `<link>` in the `<head>`, `<link>` at the bottom of the `<body>`

### Only `@import`

* `@import` in the `<head>`
* `@import` at the top of the `<body>`
* `@import` at the bottom of the `<body>`
* Non-matching media query on `@import` rule in the `<head>`, `@import` at the top of the `<body>`
* Non-matching media query on `@import` rule in the `<head>`, `@import` at the bottom of the `<body>`

### Mixing `<link>` and `@import`

This is a combinatorial explosion, and I really need to figure out how to auto-generate and run these tests before I want to attempt this. `@import` isn't looking like it's worth pursuing in any case, though.

### HTTP `Link:` header

* Lone `Link: <style.css>; rel=stylesheet
* Header with non-matching `media`, `<link>` at the top of the `<body>`
* Header with non-matching `media`, `<link>` at the bottom of the `<body>`
* Header with non-matching `type`, `<link>` at the top of the `<body>`
* Header with non-matching `type`, `<link>` at the bottom of the `<body>`

### JavaScript-powered CSS loading

* The Filament Group's loadCSS
* [Keith Clark's `media`-swapping method](http://keithclark.co.uk/articles/loading-css-without-blocking-render/)

### Miscellaneous methods

* `<link rel="subresource">`
* `<link rel="preload">`
* `<link>` with the `lazyload` attribute
* HTML Imports
* `<object type="text/css">` in the `<head>`