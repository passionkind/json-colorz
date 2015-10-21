# json-colorz
[![NPM version][npm-image]][npm-url]
[![js-standard-style][standard-image]][standard-url]
[![experimental][stability-image]][stability-url]
[![Downloads][downloads-image]][downloads-url]

This package allows you to display your json object on the console in a pretty format with colors.
[WIP]

## Why?
[Jsome](https://www.npmjs.com/package/jsome) uses [chalk](https://www.npmjs.com/package/chalk) and I want to use [colorz](https://www.npmjs.com/package/colorz). 
jsome has a cli and can be used in the browser, json-colorz respectfully, does not and cannot. json-colorz was built for node development use only. 

So I advocate to you, the user, USE [JSOME](https://github.com/Javascipt/Jsome). If you like this version, then star [JSOME](https://github.com/Javascipt/Jsome). All credit for this code goes to Jsome author, [Khalid REHIOUI](https://www.npmjs.com/~javascript). 

## Installation
```bash
$ npm install json-colorz
```

## Usage
```js
var jclrz = require('json-colorz');

var obj = {
  install: false,
  devpackages: ["colorz", "json-colorz"],
  packages: [1, 2, 3],
  git: false,
  verbose: /(app)/,
  dryrun: true,
  files: {
    gitignore: false,
    eslintrc: true,
    index: true,
    license: false,
    package: true,
    readme: true,
    test: false,
    travis: false
  },
  meta: {
    date: "Mon Oct 19 2015 16:48:33 GMT-0400 (EDT)",
    year: "2015",
    packageName: "testproj607",
    type: "private",
    repo: "none",
    remote: false,
    push: false,
    author: "Your Name",
    email: "git@your.email",
    name: "yourHandle",
    url: "https://github.com/yourHandle/testproj607",
    version: "0.1.0",
    license: "ISC",
    description: "An awesome module being created"
  }
}

jclrz(obj)
// see image below
```

![jclrz](http://i.imgur.com/0A3rHRc.png)

The following is a duplication of jsome's readme file with appropriate references changed as necessary. code functions exactly the same.

The `jclrz` function returns the object passed as argument so that when debugging, you can print the value of an object without having to change a lot on your code

```javascript

    // instead of 
    
    var foo = {
      bar : obj
    }
    jclrz (obj);
    
    // you can do this :
    
    var foo = {
      bar : jclrz(obj)
    }
    
```

You can add some points to show levels of elements... very helpful when you are dealing with complex json objects

```javascript
    jclrz.level.show = true;
```

![jclrz](https://raw.githubusercontent.com/Javascipt/Jsome/master/examples/example2.png)

The object `jclrz.level` has as default value the following json :

```javascript
  jclrz.level = {
      'show'    : false
    , 'char'    : '.'
    , 'color'   : 'red'
    , 'spaces'  : 2
    , 'start'   : 0
  }
```

You can change the level char, its color ( [see colorz package](http://npmjs.org/package/colorz) ) and the number of spaces for each level.

You can also display your json starting from a specific level to avoid displaying your json starting from the extreme left. You can do that by changing the value `jclrz.level.start`.

You can configure the colors of the displayed json by changing the values of the `jclrz.colors` object which has as default these values.

```javascript
  jclrz.colors = {
      'num'   : 'cyan'    // stands for numbers
    , 'str'   : 'magenta' // stands for strings
    , 'bool'  : 'red'     // stands for booleans
    , 'regex' : 'blue'    // stands for regular expressions
    , 'undef' : 'grey'    // stands for undefined
    , 'null'  : 'grey'    // stands for null
    , 'attr'  : 'green'   // objects attributes -> { attr : value }
    , 'quot'  : 'yellow'  // strings quotes -> "..."
    , 'punc'  : 'yellow'  // commas seperating arrays and objects values -> [ , , , ]
    , 'brack' : 'yellow'  // for both {} and []
  }
```

You can not only use the color value as string but also you can use an array to specify the background color or you can make things look bold  ( [see colorz package for more details](http://npmjs.org/package/colorz) )


```javascript
  jclrz.colors.bool  = ['green' , 'bgRed']
  jclrz.colors.attr  = ['green' , 'bold']
  jclrz.colors.quot  = ['yellow', 'bold']
  jclrz.colors.punc  = ['yellow', 'bold']
  jclrz.colors.brack = ['yellow', 'bold']
```
![jclrz](https://raw.githubusercontent.com/Javascipt/Jsome/master/examples/example3.png)


When you have a json as a string, instead of passing by `JSON.parse` function, you can just call the parse function of jclrz

```javascript
  jclrz(JSON.parse('[1,2,3]'));
```

becomes:

```javascript
  jclrz.parse('[1,2,3]');
```

If you need to disable the colors:

```javascript
  jclrz.params.colored = false;
```

When you have a very long json to display, don't make your code blocking... you can enable the asynchronous mode.

```javascript
  jclrz.params.async = true;

  jclrz(longJson, function () {
      /* Your code here */
  });
```

The default value of `params` is:

```javascript
  jclrz.params = {
      'colored' : true
    , 'async'   : false
  }
```

## See Also
- [jsome](https://www.npmjs.com/package/jsome): the awesome package json-colorz shamelessly duplicated

## License
[ISC](https://github.com/akileez/json-colorz/blob/master/LICENSE)

[npm-image]: https://img.shields.io/npm/v/json-colorz.svg?style=flat-square
[npm-url]: https://npmjs.org/package/json-colorz
[standard-image]: https://img.shields.io/badge/code%20style-standard-brightgreen.svg?style=flat-square
[standard-url]: https://github.com/feross/standard
[stability-image]: https://img.shields.io/badge/stability-experimental-orange.svg?style=flat-square
[stability-url]: https://github.com/akileez/json-colorz
[downloads-image]: http://img.shields.io/npm/dm/json-colorz.svg?style=flat-square
[downloads-url]: https://npmjs.org/package/json-colorz
