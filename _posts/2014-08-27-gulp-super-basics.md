---
layout: post
title: Gulp.js Super Basics
---

## why?
By now, I'm sure you've heard of `grunt` and `gulp`. Personally, I prefer `gulp`, it's more like standard `javascript` and doesn't make me feel like I need to learn a new language to use it. `grunt`, while having more support at the time of writing this, has more support than `gulp`, but it feels like handwriting `json` objects, not the `javascript` I know and love.
Anyway, `gulp` and `grunt` are awesome. They allow you to automate a whole lot of often things and keep everything DRY, not just your code, but your whole process.

<!--more-->

## how?
I'm about to write something that is not necessarily the most useful piece of code, but it can illusrate how `gulp` can save a ton of time.

`gulp`, and `grunt`, require a `gulpfile.js` (or `gruntfile.js`, but this uses a different syntax) to run and configure tasks.

### First steps
For `gulp`, before you can use anything, make sure you `gulp` globally. 

`npm i -g gulp`

Then, in the project you want to use `gulp` in, add `gulp` to your local dependencies.

`npm i --save-dev gulp`

This allows your to make and use your `gulpfile.js`.
<pre>
//require 'gulp', if you know 'node', you know this.
var gulp = require('gulp');

//gulp has a special 'default' used when calling 'gulp'
// form the terminal. You can set it like this:

gulp.task('default', function(){
  console.log('testing gulp...');
});
</pre>

When you call `gulp` from the command line, it will log 'testing gulp...', this is arguably the most boring thing you can do with `gulp`.

The `gulp` method, `task` allows you to name tasks to be called from the command line.

The first parameter is a string, the name you will call later. `gulp <task name>`

Specifying the task name as 'default' will set the behavior of simply calling `gulp`.

The second parameter (if provided) is an array of task names (as strings) to be completed before this task. This allows you to string various tasks together and part out more specialized tasks.

A final gulpfile shoule look something like this:
<pre>
'use strict';

var gulp = require( 'gulp' );
var browserify = require( 'browserify' );
var watchify = require( 'watchify' );

var source = require( 'vinyl-source-stream' );
var paths = require( '../paths.js' );

gulp.task('browserify', function(){

  var bundler =
    browserify({
      entries: [paths.src + 'scripts/app.coffee'],
      extensions: ['.coffee', '.jade'],
      debug: true,
      cache: {},
      packageCache: {},
      fullPaths: true
    });

  var watchedBundle = global.isWatching ? watchify(bundler) : bundler;

  watchedBundle
    .transform('coffeeify')
    .transform('jadeify');

  var bundle = function(){
    bundleLogger.start();

    return bundler
            .bundle()
            .pipe(source('app.js'))
            .pipe(gulp.dest(paths.dest + '/js'))
  };

  if (global.isWatching){
    watchedBundle.on('update', bundle);
  }

  return bundle();
});

gulp.task( 'setWatch', function () {
  global.isWatching = true;
};

gulp.task( 'default', ['setWatch', 'browserify']);
</pre>
With this, call `gulp` will bundle everything up with `browserify` and watch for any changes during develpment.

You can still call `gulp browserify` and `gulp setWatch` independently or in other `gulp` tasks.


I will go into more detail on this specific task (`browserify` bundling) in the very near future.