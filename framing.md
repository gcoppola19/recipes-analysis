---
layout: default
title: Framing a Prediction Problem
nav_order: 3
---
## Framing a Prediction Problem
Clearly state your prediction problem and type (classification or regression). If you are building a classifier, make sure to state whether you are performing binary classification or multiclass classification. Report the response variable (i.e. the variable you are predicting) and why you chose it, the metric you are using to evaluate your model and why you chose it over other suitable metrics (e.g. accuracy vs. F1-score). Make sure to justify what information you would know at the “time of prediction” and to only train your model using those features. For instance, if we wanted to predict your Final Exam grade, we couldn’t use your Portfolio Homework grade, because we (probably) won’t have the Portfolio Homework graded before the Final Exam! Feel free to ask questions if you’re not sure.

We are looking to predict the rating of recipes from the percent daily values of saturated fat and sugar in the recipe. If we are given the nutrition information, can we predict an accurate rating? This prediction problem will be answered through a linear regression model, with the response variable being a recipe's rating
---