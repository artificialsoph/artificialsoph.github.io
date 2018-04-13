---
title: Paperspace how-to (cheap cloud GPU)
layout: post
date: 2018-02-01 16:11:40
tags: drafts
---

The use of GPUs have become quite important for applications of Deep Learning. The landscape of this hardware has lately become quite interesting. The [cryptocurrency fad](https://arstechnica.com/tech-policy/2018/01/cryptocurrency-boom-creates-insane-global-graphics-card-shortage/) has led to GPUs becoming expensive and/or unavailable. One solution to this problem is to rent a computer with a GPU from Google, Amazon, Microsoft, and others. Google even [recently lowered](https://cloudplatform.googleblog.com/2017/11/new-lower-prices-for-GPUs-and-preemptible-Local-SSDs.html) their GPU prices quite substantially. I'll save doing a full comparison of each platform for later, but what I'll go over today is getting started with a relatively new service, [PaperSpace](https://techcrunch.com/2017/05/03/paperspace-launches-gpu-powered-virtual-machines-loaded-with-tools-for-data-scientists/) based in my home of Brooklyn <3.

The virtue of paperspace is that their entry-level GPU offering costs $0.40/hr (compared to Google's new $0.45/hr and Amazon's $0.90/hr) but [benchmarks ahead](https://medium.com/initialized-capital/benchmarking-tensorflow-performance-and-cost-across-different-gpu-options-69bd85fe5d58) of Amazon and other offers based on the Tesla K80.

Below, I'll show you how to get up and running quickly and how to set up cost-saving measures, like auto-shutdown.

# Steps to get running

First, as with any new machine, update the current packages with

```
sudo apt update
sudo apt upgrade
```

(Note: I had to add the `--fix-missing` flag to `sudo apt update`)

Add a new user according to [these instructions](https://www.digitalocean.com/community/tutorials/how-to-create-a-sudo-user-on-ubuntu-quickstart).



## open ports with ufw

By default, Paperspace has a very strict firewall (this is a good thing). We're going to want to get to our jupyter notebooks, though, so we need to open up some ports. You can do that with [these instructions](https://www.digitalocean.com/community/tutorials/how-to-setup-a-firewall-with-ufw-on-an-ubuntu-and-debian-cloud-server).

My version is pretty unsafe (it allows access from any IP) so feel free to check that link for info on restricting the IP that can access your jupyter port.

```
sudo ufw allow 8888
sudo ufw allow 60000:61000/udp
```

# set up jupyter


# fix autoshutdown with ssh

https://paperspace.zendesk.com/hc/en-us/articles/115002807447-How-do-I-use-Auto-Shutdown-on-my-Linux-machine-when-connecting-through-SSH-

# set up ssh keys

https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys--2

https://apple.stackexchange.com/questions/48502/how-can-i-permanently-add-my-ssh-private-key-to-keychain-so-it-is-automatically

# Install cuda 9.1

You can use the [official guide](http://docs.nvidia.com/cuda/cuda-installation-guide-linux/) but I prefer [these instructions](https://askubuntu.com/questions/967332/how-can-i-install-cuda-9-on-ubuntu-17-10).

# Install cudnn

http://docs.nvidia.com/deeplearning/sdk/cudnn-install/index.html
