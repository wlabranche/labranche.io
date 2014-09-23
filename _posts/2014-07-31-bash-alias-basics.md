---
layout: post
title: Bash Alias Basics
---

## Bash is awesome
Knowing it will save you time. Time is everything in programming.

<!--more-->

## You can always be faster
I often find myself repeating certain commands over and over (e.g.  `cd /Documents/projects/`). This takes a couple seconds, but when I type this a couple hundred times a day, it can add up.

What can you do about it?

## Magic
From the command line, use your favorite text editor to open your `.bash_profile`. On a mac, it's located in your root directory (`~/`).

ex. `subl ~/.bash_profile`

If it doesn't exist, make it with `touch ~/.bash_profile`.

Add your custom alias pretty much anywhere like this:
`alias proj="cd ~/Documents/projects"`, where what follows `cd` is the route to your project and `proj` is the command you want to call.

Note: There are some commands that you may not want to replace, do a quick google search before making things whatever you want to avoid some undesireable behavior.

Once that's done, save and reload your bash source (`source ~/.bash_profile` or restart your shell) give it a try.

`proj` now takes you directly to `~/Documents/projects`.

This little bit of knowledge will make your bash experience significanly better.

Also be aware of the fact that you can set aliases to other things as well. Think `git status` too many characters to deal with?
(also note that `bower` and `npm` have some default aliases like `npm i` to `npm install` may be a bad example).

Change this long tedious command to to `gs` and save a ton of time.

Hope this helps.