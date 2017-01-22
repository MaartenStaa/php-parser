<h1 align="center">php-parser</h1>
<p align="center">
<a href="https://travis-ci.org/glayzzle/php-parser"><img src="https://travis-ci.org/glayzzle/php-parser.svg"></a>
<a href="https://coveralls.io/github/glayzzle/php-parser?branch=master"><img src="https://coveralls.io/repos/github/glayzzle/php-parser/badge.svg?branch=master&v=20170115" alt="Coverage Status" /></a>
<a title="npm version" href="https://www.npmjs.com/package/php-parser"><img src="https://badge.fury.io/js/php-parser.svg"></a>
<a title="npm downloads" href="https://www.npmjs.com/package/php-parser"><img src="https://img.shields.io/npm/dm/php-parser.svg?style=flat"></a>
<a title="Gitter" href="https://gitter.im/glayzzle/Lobby"><img src="https://img.shields.io/badge/GITTER-join%20chat-green.svg"></a>
</p>
<p align="center">This javascript library parses PHP code and convert it to AST.</p>

Installation
------------

This library is distributed with [npm](https://www.npmjs.com/package/php-parser) :

```sh
npm install php-parser --save
```

Usage
-----

```js
// initialize the php parser factory class
var engine = require('php-parser');
// initialize a new parser instance
var parser = new engine({
  // some options :
  parser: {
    extractDoc: true
  },
  ast: {
    withPositions: true
  }
});

// Retrieve the AST from the specified source
var AST = parser.parseEval('echo "Hello World";');
// AST.kind === 'program';
// AST.children[0].kind === 'echo';

// Retrieve an array of tokens (same as php function token_get_all)
var tokens = parser.tokenGetAll('<?php echo "Hello World";');
```

Sample AST output
-----------------

```js
{
  'kind': 'program',
  'children': [
    {
      'kind': 'echo',
      'arguments': [
        {
          'kind': 'string',
          'isDoubleQuote': true,
          'value': 'Hello World'
        }
      ]
    }
  ]
}
```

Try it online (demo) :
http://glayzzle.com/php-parser/#demo

API Overview
------------

The main API exposes a class with the following methods :

- **parseEval**(String buffer) : parse a PHP code in eval style mode (without php open tags)
- **parseCode**(String buffer, String filename) : parse a PHP code by using php open tags.
- **tokenGetAll**(String buffer) : retrieves a list of all tokens from the specified input.

You can also [pass options](https://github.com/glayzzle/php-parser/wiki/Options) that change the behavior of the parser/lexer.

Documentation
-------------

- [AST nodes definition](https://github.com/glayzzle/php-parser/blob/master/docs/AST.md)
- [List of options](https://github.com/glayzzle/php-parser/wiki/Options)
- [Main API](https://github.com/glayzzle/php-parser/tree/master/docs)
- [Lexer API](https://github.com/glayzzle/php-parser/blob/master/docs/lexer.md)
- [Parser API](https://github.com/glayzzle/php-parser/blob/master/docs/parser.md)

Related projects
----------------

- [php-unparser](https://github.com/chris-l/php-unparser) : Produce code that uses the style format recommended by PSR-1 and PSR-2.
- [php-writer](https://github.com/glayzzle/php-writer) : Update PHP scripts from their AST
- [ts-php-inspections](https://github.com/DaGhostman/ts-php-inspections) : Provide PHP code inspections written in typescript
- [php-reflection](https://github.com/glayzzle/php-reflection) : Reflection API for PHP files
- [wp-pot](https://github.com/rasmusbe/wp-pot) : Generate pot file for WordPress plugins and themes
- [crane](https://github.com/HvyIndustries/crane) : PHP Intellisense/code-completion for VS Code

> You can add here your own project by opening an issue request.

# Misc

This library is released under BSD-3 license clause.

If you want to contribute please visit this repository https://github.com/glayzzle/php-parser-dev.
