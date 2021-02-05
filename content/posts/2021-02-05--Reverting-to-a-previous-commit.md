---
title: Reverting to a previous commit
date: '2021-02-05T22:40:32.169Z'
template: 'post'
draft: false
slug: 'Reverting to a previous commit'
category: 'Git'
tags:
  - 'Git'
description: 'Reverting to a previous commit.'
socialImage: '/media/42-line-bible.jpg'
---

Trying to revert to a previous commit is something that I do fairly frequently. There are two main commands that can be used here"

`git reset --hard HEAD` will take you back to the last commit that was made, and none of your changes will be present.

`git reset --soft HEAD` will take you back to the last commit that was made, but will keep your changes, so that you can amend them.
