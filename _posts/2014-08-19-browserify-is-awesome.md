---
layout: post
title: Browserify is awesome
---

If you pay attention to your surroundings and are often surrounded by javascript, chances are you've heard of some sorcery referred to as `browserify`.

<!--more-->

{<1>}![Browserify](https://pbs.twimg.com/profile_images/420347030263701504/9esmqty2_400x400.png)
## what is it?
`browserify` lets you bundle all of your front dependencies together using the commonJS `require` pattern (e.g. `var thing = require('./thing.js');`).

Basically, it's a perfect example of how `node` is making everything amazing.

It recursively traverses through all linked documents and bundles them together with a complex series of pipes and tubes and spilts out a magic script that only requires one to add a single script tag to their document.

It's awesome.

### so?

This may not seem too important. After all, you can compile all your srcipts together using `gulp` or `grunt` to accomplish something similar, but what's awesome about browserify is that it has an awesome transform system to alter files and have them work seamlessly together once compiled. These things often have siliarly awesome names (`watchify`, `es6ify`, `jadeify`, `reactify`, to name a few);

All of your files will only need to referece one or two files and they will be added into your applications ecosystem.

Also, `browserify` plays nice with `gulp` and `grunt` so you can deveope apps just as you have before.

### Another thing
Because `browserify` lets you use `npm` modules on the front end, many classic front-end tools are being ported to (or just published as) `npm`. I rarely use `bower` anymore. `npm` is all you will need soon.


#### Almost forgot!
One of my favorite transforms is `coffeeify`, as you might have expected it compiles your `coffeescript` files and integrates them into your app. Sounds normal, except it will allow you to pick and choose how you use `coffeescipt` in various parts of your app.

I'd highly recommend trying it out.

If you're interested, read more [here](http://browserify.org/)  and [here](https://github.com/substack/browserify-handbook).