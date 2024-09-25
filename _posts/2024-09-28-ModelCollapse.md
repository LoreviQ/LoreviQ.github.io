---
layout: post
title: Simulating Model Collapse in AI - A Personal Project
tags: [python, ai, data anlaysis]
comments: false
---
In recent years, the rise of AI-generated content has raised important questions about the robustness of AI models. My latest project aimed to explore one such question: how quickly do AI models degrade when trained on data that they themselves generate? This exploration led me to investigate model collapse, particularly in the context of sentiment analysis using Amazon reviews.

## Project Overview

The primary objective of my project was to analyze how AI models, once trained, perform when exposed to progressively generated data. I focused on a sentiment classification task, where reviews were categorized as either positive (4-5 stars) or negative (1-2 stars), intentionally excluding 3-star reviews to streamline the classification challenge. I developed this project using Python.

You can find the code and additional resources on my [GitHub page](https://github.com/LoreviQ/ModelCollapse).

### Step 1: Training the Classification Model

I began by developing a sentiment classification AI, testing it across various dataset sizes ranging from 100 to 400,000 reviews. As anticipated, I observed an increase in accuracy with larger datasets, although the gains diminished as the size grew. This initial phase was crucial for establishing a baseline performance level.

### Step 2: Simulating a Total Collapse Scenario

Next, I set up a ‘total collapse scenario’. Here, I trained the model normally up to a certain point (the collapse point) and then allowed it to generate its own training data, increasing the dataset size to 400,000 reviews. The results were striking: the model's performance quickly deteriorated towards randomness (a score of 0.5), regardless of how well it initially performed before the collapse.

### Step 3: Exploring Different Collapse Rates

To deepen my understanding, I then simulated various collapse rates. Starting with an initial dataset of 50,000 reviews—where the model had already reached a substantial level of accuracy—I gradually increased the dataset size to 80,000, incorporating self-generated data at collapse rates from 0% to 100%. Unsurprisingly, models with higher collapse rates experienced faster declines in performance.

### Step 4: Investigating Lower Collapse Rates

In a subsequent phase, I refined my analysis by working with smaller sample sizes (1,000 to 10,000 reviews) and lower collapse rates (0% to 30% in 3% increments). Notably, I found that a 3% collapse rate had a negligible impact on the model’s accuracy, nearly mirroring the performance of a model trained solely on original data. This prompted further investigation into the effects of small amounts of AI-generated data, as I expected that even minor contributions could influence performance.

### Final Analysis: The Impact of AI-Generated Data

In the final stage of my project, I repeated the lower collapse rate experiments, focusing on a narrower range (0% to 10% in 1% increments). Through multiple iterations and averaging scores, I confirmed that any inclusion of AI-generated data, even as low as 1%, resulted in a decline in model performance. The difference between 0% and 10% at a 1,000-review sample size was minimal, illustrating that while small proportions of AI-generated data can seem insignificant, they still exert a negative influence.

## Real-World Implications

The insights gained from this project highlight a pressing concern in the modern AI landscape. As AI-generated content becomes more prevalent, the risk of "polluting" new training datasets grows significantly. Models trained on self-generated data can quickly deteriorate, undermining their efficacy and reliability. This phenomenon is particularly relevant for industries relying on accurate sentiment analysis and decision-making based on AI predictions.

The findings underscore the importance of curating high-quality, human-verified data for training AI models. As we navigate an era increasingly characterized by AI, awareness of these issues is crucial for developing robust systems that maintain accuracy and trustworthiness.

## Conclusion

This project not only deepened my understanding of model collapse but also emphasized the critical balance between leveraging AI and ensuring data integrity. With the rise of AI-generated content, it is more important than ever to be vigilant about the data we use to train our models. I look forward to continuing my exploration in this fascinating field, contributing insights that could help shape the future of AI. 

Feel free to explore the graphs and datasets I generated throughout this project, which illustrate these findings in greater detail.