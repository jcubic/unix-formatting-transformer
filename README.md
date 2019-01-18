```
   ▄████████ ███▄▄▄▄      ▄████████  ▄█  ████████▄     ▄████████  ▄████████
  ███    ███ ███▀▀▀██▄   ███    ███ ███  ███   ▀███   ███    ███ ███    ███
  ███    ███ ███   ███   ███    █▀  ███▌ ███    ███   ███    █▀  ███    █▀
  ███    ███ ███   ███   ███        ███▌ ███    ███  ▄███▄▄▄     ███
▀███████████ ███   ███ ▀███████████ ███▌ ███    ███ ▀▀███▀▀▀     ███
  ███    ███ ███   ███          ███ ███  ███    ███   ███    █▄  ███    █▄
  ███    ███ ███   ███    ▄█    ███ ███  ███   ▄███   ███    ███ ███    ███
  ███    █▀   ▀█   █▀   ▄████████▀  █▀   ████████▀    ██████████ ████████▀
```

[![npm](https://img.shields.io/badge/npm-0.2.1-blue.svg)](https://www.npmjs.com/package/ansidec)
[![travis](https://travis-ci.org/jcubic/ansidec.svg?branch=master)](https://travis-ci.org/jcubic/ansidec)
[![Coverage Status](https://coveralls.io/repos/github/jcubic/ansidec/badge.svg?branch=master)](https://coveralls.io/github/jcubic/ansidec?branch=master)
[![MIT badge](https://img.shields.io/badge/license-MIT-blue.svg)](https://github.com/jcubic/jquery.terminal/blob/master/LICENSE)

ANSIDec is a library for handling limited number of ANSI escape sequences for use
in Browsers. The primary goal of the library is to allow of displaying ANSI and ASCII
art in Browsers by transforming Unix encoding to html.
But it can also be used from Node.js.

## Demo

https://jcubic.github.io/ansidec/

## Installation

Npm installation for use with webpack:

```
npm install ansidec
```

Besides npm you can also download that file locally or use
[unpkg.com](https://unpkg.com/ansidec):

```html
<script src="https://unpkg.com/ansidec"></script>

```

## Usage

```javascript
// if you're using webpack or node.js you can use npm
var ansi = require('ansidec');

var format = ansi.format(function(styles, color, background, text) {
  var style = [];
  if (color) {
    style.push('color:' + color);
  }
  if (background) {
    style.push('background:' + background);
  }
  if (styles.bold) {
    style.push('font-weight:bold');
  }
  if (styles.italic) {
    style.push('font-style:italic');
  }
  if (styles.underline) {
    styles.push('text-decoration:underline');
  }
  return '<span style="' + style.join(';') + '">' + text + '</span>';
});

document.querySelector('pre').innerHTML = format(text);
```

format function can be executed with text as second argument, then it will
return string. If it don't get string as second argument it will return
function. So it's like it was curried.

If you want just to output html you can use helper:

```javascript
var ansi = require('ansidec');

document.querySelector('pre').innerHTML = ansi.html(text)

```

and use format only if you need different html or any different output text.

## ANSI art

If you want to render ANSI art with this library you will need to covert the text from
ANSI art file to UTF-8 to do that you can use iconv-lite library or iconv on a Back-End
see how to do that in
[examples directory](https://github.com/jcubic/ansidec/tree/master/example).


### License

Released under [MIT](http://opensource.org/licenses/MIT) license

Copyright (c) 2018-2019 [Jakub T. Jankiewicz](https://jcubic.pl/)
