---
title: Module 8, Exercise
description: 
kt: 5342
audience: 
doc-type: tutorial
activity: 
---

# Module 8: Adobe Experience Platform Data Science Workspace

**Authors: [Jonathan Lancar](https://www.linkedin.com/in/jonathanlancar/), [Wouter Van Geluwe](https://www.linkedin.com/in/woutervangeluwe/)**

## Lab Overview

Retailers like Luma and La Boutique want to deliver personalized recommendations. When customers visit the website and click on a product, they should be presented with personalized product recommendations.

This lab will enable you to create a simple Machine Learning model that generates product recommendations for this website using Data Science Workspace.

## Key Takeaways

* Become familiar with the Adobe Experience Platform UI
* Explore Adobe Experience Platform Data Science Workspace
* Analyze and transform your data.
* Author a model and operationalize it
* Train your model and experiment
* Score your model and consume the insights

## Prerequisites

* Adobe Experience Platform
* Datasets (dataset used during lab, pre-loaded for you)
* Zip-file containing the 3 required notebooks

## Your Environment Variables

This documentation has been created to be reused across multiple Adobe Experience Platform instances for enablement purposes.
In order to complete some of the modules, you'll need to change some variables and replace them by your specific ``Environment Variables``.

You can view these variables [here](../../environment.md).

## Content

### [Exercise 8.1 - Data Exploration and Transformation](./ex1.md)

To create a machine learning model that will recommend products that users might like when they are looking at a particular product, you need to analyze previous purchases made by users on the website. In this lesson, you will explore purchase data flowing via Adobe Analytics to Platform and transform that data into a Feature DataSet that can help train your machine learning model.

### [Exercise 8.2 - Model Authoring and Operationalization](./ex2.md)

In exercise 1 we created the Training Data required to power our Machine Learning model. In this lesson we will show you how you can use this data and author a machine learning model. In the real world, creating a dataset and a machine learning model will be an iterative process.

### [Exercise 8.3 - Model Training and Experimentation](./ex3.md)

So we’ve prepared our data, authored our model and packaged it to test it at scale as a recipe. Now let’s go ahead and train and test the model at scale.

### [Exercise 8.4 - Scoring and Consumption of Insights](./ex4.md)

Now that we’ve experimented with our recommendations model and have determined the optimal run, we can move on to scoring the model to generate product recommendations for customers.

[Go Back to All Modules](../../README.md)
