---
title: Imbalanced Classes Guide
layout: post
date: 2018-11-05 15:51
tags: howto
---

Let's start by thinking of the problem that unbalanced classes creates. If we have 900 examples from class A and 100 examples from class B. The main problem is that accuracy doesn't work as a metric (a model can get 90% just by predicting A). We can solve this trivially by just using a different metric, say f1 or f_beta, and then continuing on our model selection process: try a bunch of models and select the one with the best f1 score.

Your first step is to solve this main problem by selecting a better metric. Look at your options and figure out what you want. You've got precision, recall, and the f_beta family that combines the two (sklearn guide). Area under the ROC curve is often used but has recently fallen out of favor for good reasons so watch out (good kaggle notebook). The precision-recall curve (sklearn guide) is a good alternative. My recommendation: if you need a top-line number for model comparison, use f_beta and set your beta to weigh the balance between precision and recall. Use a confusion matrix regularly to get a more detailed view of your data. And finally, look at the PR-curve.

The main problem (that accuracy isn't helpful with unbalanced classes) is easy to fix without sampling. We just get a better metric. Okay, why then does sampling come up so often with unbalanced classes? This is the second step: once we have selected a better metric, in some cases emphasizing the minority class(es) can improve model performance. This is because many models use the frequency of classes as a proxy for emphasis: if class A is 9x as common as class B, many models assume it's also worth 9x the attention.

I'll list out a bunch of ways of tackling this problem of emphasis starting with the ones you should try first. You'll have to pick the one that best fits your situation.

1 Literally do nothing
This should be your first step and your base case of comparison. Start here.

2 Thresholding
Train a model just like you would normally and modify the threshold (predict class A if p_a >.1) to find the value of t that gives the best performance. This is essentially what happens in a PR-curve. Many models, like the random forest family of models, tend to benefit less from the methods below.

3 Use class weights
Many classification models in sklearn have a class_weight parameter. This lets you weight rare classes higher and common classes lower. You can also set class_weights to balanced to have sklearn automatically weight the classes (this is a good default).

4 Naive Oversampling
In the case above, we have 900 observations in class A and 100 in class B. In oversampling we sample 800 more examples from class B so that now we have 900/900 examples in each class. Note that if a model has class weights, this is often equivalent to using class weights except that we're now running the model on more examples. So naive oversampling is only preferred over class weights when a model cannot use class weights.

5 Naive Undersampling
Undersampling is just like above except that instead of adding samples to class B, we're going to randomly remove 800 samples from class A so that now we have 100/100 examples in each class. Naive undersampling is very rarely a good idea. This is because, like naive oversampling, class_weights is often equivalent in terms of emphasis. Additionally, undersampling removes data, sometimes a lot of data. If we compare a model that uses class_weights with one that undersamples, the class weights one will have 9 times as many examples from class A to learn from, while the model that undersamples has the same effect of emphasis as class_weights. Who do you think is going to do better?

6 Advanced sampling techniques
The imblearn library has a ton of techniques for dealing with this second problem.
- SMOTE: like oversampling but adds noise to new examples based on neighbors
- ADASYN: is like SMOTE but it further emphasizes difficult to learn classes
- There's a bunch of undersampling techniques that intelligently undersample based on neighborhoods and prototypes.
- Combinations: The one case where I see undersampling being useful is in very unbalanced classes where oversampling would lead to more data than I could run an analysis on. In that case, It's often useful to undersample the majority class slightly while oversampling the minority class.

Also be super careful with model evaluation. Testing on sampled data is a cardinal sin of data science. Your customer wants to know how your model will perform in the real world, so you should test on raw data from that real world and never sample on test.
- Always use stratified methods in cross validation.
- Carve off a validation and hold-out set at the very beginning of your work. Do not sample these two. Use the validation set for model selection and hold-out for the performance you report.
- In lieu of a validation set, you can use K-fold for model evaluation, but you will have to be very careful with how you set up your pipeline so that you don't sample the test set in each fold. The imblearn package plays nice with sklearn pipelines so that imblearn samplers automatically respect the test/train split in cross validation (imblearn model selection examples).
