---
title: Soph's VM tweaks
layout: post
date: 2018-02-14 11:11:48
tags:
---


# What's this

This is a scratch pad for me to use when I set up new virtual machines. I'm sharing it in case anyone else is interested.

# fish is by far my favorite shell

Install it and configure it following [this tutorial](https://geowarin.github.io/the-missing-fish-shell-tutorial.html)

`omf` is a handy package manager for fish. You can install [themes](https://github.com/oh-my-fish/oh-my-fish/blob/master/docs/Themes.md#sushi) with it and my fav is probably `sushi`.

If you're using anaconda, you'll have to remember to use `activate` instead of `source activate` [details](https://github.com/conda/conda/issues/2611#issuecomment-230894534).

# tmux

I love tmux! I p much always install it first thing. To make it more useful, I add options by creating the following file at `~/.tmux.conf`.

```
set-option -g mouse on
set-option -g default-command /usr/bin/fish
```

# other tools

- install [dtrx](https://github.com/moonpyk/dtrx) for common sense file extraction
  - `sudo apt install dtrx`
- [glances](http://glances.readthedocs.io/en/stable/index.html)
- [gpustat](https://github.com/wookayin/gpustat)
