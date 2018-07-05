---
title: Soph's VM tweaks
layout: post
date: 2018-02-14 11:11:48
tags:
---


# What's this

(hi, this is a test)

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

# Access Jupyter from your server

I typically set up a jupyter server mostly according to Chris Albon's instructions [here](https://chrisalbon.com/software_engineering/cloud_computing/run_project_jupyter_on_amazon_ec2/).

# Start Jupyter on restart

Previously, my workflow was something like this: go to console in browser and start ec2, go to terminal and mosh into ec2, start jupyter notebook, go back to
browser and use jupyter. That's an annoying amount of steps. I like to simplify this so that on every device restart, my machine automagically starts a jupyter notebook server and glances (which I use to monitor the machine's resource usage).

Here's the solution I found, which is a modification of [this](http://rodriguezandres.github.io/2017/01/18/jupyter-aws/). Modify your `/etc/rc.local` to include the following above the `exit 0` line:
```bash
export PATH="$PATH:/home/ubuntu/miniconda3/bin"
nohup jupyter notebook --notebook-dir=/home/ubuntu/ &
nohup glances -w &

exit 0
```
