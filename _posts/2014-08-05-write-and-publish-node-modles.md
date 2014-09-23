---
layout: post
title: How to write (and publish) npm modules... in like four minutes
---

npm is pretty awesome, if you're reading this I'm sure you've used at least one at some point in time (`bower` is a pretty common one).

<!--more-->

I'm sure you've probably had some interest wanting to write one, or at least would like to know how one would (otherwise, why would you be reading this?).

For a while, I was pretty terrfied of writing them, but after a little research, I've been able to throw together a few. They don't do too much, but they work.

## Basics
You need to know a little `javascript` and need to have `node` installed as it's how you will be testing (and it comes with `npm` which is kind of the whole point here.

If you don't, install that (`brew install node` on a mac).

### 1. set up
In a new directory, ideally with the name of your soon to be module (you may want to check if the name is [available](http://npmjs.org)), `npm init` and set up your `package.json`. It's pretty much all you need to get published.

In this directory, I usually make two folders, `bin` and `lib`, where I put my code. The `package.json` is outside of those.

### 2. write code
Create a file, `<your script name>.js`, write some code.

If you're using my file structure, this file should be in `lib`.

This file is pretty much uselss, but a super basic example:
<pre>
'use strict'

var item;
var moduleName = function(){
  if (process.argv.length > 2){
    item = process.argv[2];
    console.log('you passed me this: ' + item);
  }else{
    console.log('pass me a file, so I can do something');
  }
}

module.exports.moduleName = moduleName;
</pre>

Make sure to export your code!

### 3. bin file
The closest thing to a 'hard part' here is understanding how to get everything to be called on command.

In `bin`, create a file with the name of the command you want to invoke at some point in time (it's likely going to be the same as your module). **do not use a suffix.**

It's not going to do much, but this is how it should roughly look:

<pre>
#!/usr/bin/env node

"use strict";
var path = require('path');
var fs = require('fs');
var lib = path.join(path.dirname(fs.realpathSync(__filename)), '../lib');

var moduleName = require(lib + '/moduleName.js').moduleName;

moduleName();
</pre>

Where moduleName is the name of your module.

### 4. Test!
Now you can test your file!

`node <path to bin> <arguments (if needed)>`

Make sure everything works as it should, you can include tests within this directory, but we'll skip that for now.

### 5. publish!
`npm adduser` to make sure you exist and are signed in.

`npm publish`

That's pretty much it.

### 6. install through npm
`npm install <moduleName>`


