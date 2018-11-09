---
title: Performance of different model types on MNIST by year
layout: post
date: 2018-11-08 11:35
tags: data science, history
---

Today I was trying to answer the question of why it seems like so much attention was given to support vector machines in the past. I had assumed that before the Deep Learning renaissance in 2006, SVMs were the dominate model because they outperformed Deep Learning models of the time. But if that was true, I wanted to see how it changed over time and how SVMs and DL models compared to less practical models like KNN.

To investigate this, I went to a table of top performances on the MNIST dataset maintained by Yann LeCun. This table is helpfully organized by model type and year.

I made a bunch of hand modifications (which you can find [here](images/mnist-history.csv)) to allow me to plot the performance of different model types. To my surprise, SVMs were actually never the dominant. The reasons SVMs were favored over Deep Learning turn out to be much more subtle and I'll save them for later.

<img src="/images/mnist-history.png">
