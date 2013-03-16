Module for input management with nodejs.

# Installation

To install the most recent release from npm, run:

    npm install stdio

# Usage

You can do many things with this module

## Read standard input at once

```javascript
var stdio = require('stdio');
stdio.read(function(data){
    console.log(data);
});
```

## Parse Unix-like command line options

```javascript
var stdio = require('stdio');
var ops = stdio.getopt({
    'check': {key: 'c', args: 2},
    'map': {key: 'm'},
    'kaka': {key: 'k', args: 2},
    'ooo': {key: 'o'}
});
console.log(ops);
```

If you run the previous example with the command

    node pruebas.js -c 23 45 88 --map -k 23 44 cosa

Program output will be:

    { check: { args: [ '23', '45' ] },
      args: [ '88', 'cosa' ],
      map: true,
      kaka: { args: [ '23', '44' ] } }

So you can check options:

```javascript
if(ops.map){
    // Your action
}
if(ops.kaka){
    // Your action, using ops.kaka[0] or ops.kaka[1] or...
}
```