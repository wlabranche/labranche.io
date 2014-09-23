---
layout: post
title: Continuos Integration with Node, Mocha, Travis-CI and Coveralls
---

## Why?
It's useful and will allow you to better manage your repos.

You also get fancy badges.

## How?

installs//

Get accounts at [Travis-CI](https://travis-ci.org/) and [Coveralls.io](https://coveralls.io/). They're free for open projects.

Once there, find the repo you want to test on both sites and turn them on.

To get these to work on your project, you will need both a `.travis.yml` and `.coveralls.yml` in your root directory.

Set these up like this // get to this later

**IMPORTANT**: By default mocha hates test directories that don't follow it's rules. This pretty much just means you need to name it `test`. Otherwise, you may spend hours doing everything else right with terrible results. 