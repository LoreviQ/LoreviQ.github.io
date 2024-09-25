---
layout: post
title: Simulating Model Collapse in AI - A Personal Project
tags: [python, ai, data anlaysis]
comments: false
---
# Exploring Model Collapse in AI: A Deep Dive into Sentiment Analysis  

In recent years, AI has reshaped industries by generating content faster than ever before—but there's a hidden risk that could undermine its power: what happens when AIs train on their own outputs? This was the core question behind my latest project.

In this project, I explored the critical issue of model collapse—the deterioration of AI models when they are repeatedly trained on data they themselves generate. Focusing on sentiment analysis using Amazon reviews, I investigated how AI models perform when exposed to progressively generated data. Reviews were categorized as either positive (4-5 stars) or negative (1-2 stars), with 3-star reviews intentionally excluded to simplify the classification task and sharpen the focus on model performance.

I developed the project in Python using several libraries:
- **nltk** for preparing the dataset and tokenizing the text.
- **pandas** for manipulating the data.
- **joblib** for parallelization, ensuring the project could be completed efficiently.
- **scikit-learn (sklearn)** for AI model processing and evaluation.
- **matplotlib** for visualizing the results.

You can find the code and additional resources on my [GitHub page](https://github.com/LoreviQ/ModelCollapse).

## Step 1: Training the Classification Model  

I began by developing a sentiment classification AI, testing it across various dataset sizes, ranging from 100 to 400,000 reviews. As anticipated, I observed an increase in accuracy with larger datasets, although the gains diminished as the size grew. This initial phase was crucial for establishing a baseline performance level. 

**Why Sentiment Analysis?**  
Sentiment analysis is a practical and well-documented AI application, making it ideal for testing model robustness. By focusing on Amazon reviews, I had access to a large, diverse dataset, and excluding 3-star reviews allowed me to simplify the analysis into clearer extremes: positive or negative sentiment.

## Step 2: Simulating a Total Collapse Scenario  

Next, I set up a ‘total collapse scenario’. In this phase, after training the model normally to a high level of accuracy, I let it generate its own training data, increasing the dataset size to 400,000 reviews. This is similar to someone trying to teach themselves by continually re-reading and revising their own notes.

The results were striking: the model's performance quickly deteriorated toward randomness (a score of 0.5), regardless of how well it initially performed before the collapse.

The performance graph showed a rapid and dramatic decline, represented by a steep downward curve—plummeting towards the baseline, which signified random guessing.

## Step 3: Exploring Different Collapse Rates  

To deepen my understanding, I simulated various collapse rates. Starting with an initial dataset of 50,000 reviews—where the model had already reached a substantial level of accuracy—I gradually increased the dataset size to 80,000, incorporating self-generated data at collapse rates ranging from 0% to 100%.

As expected, models with higher collapse rates experienced faster and more severe declines in performance. This phase revealed important thresholds where performance started to rapidly degrade, even when only small amounts of AI-generated data were introduced.

## Step 4: Investigating Lower Collapse Rates  

In the next phase, I focused on lower collapse rates (0% to 30% in 3% increments) and smaller sample sizes (1,000 to 10,000 reviews). Interestingly, I found that a 3% collapse rate had a negligible impact on the model’s accuracy. In fact, the model's performance nearly mirrored that of a model trained entirely on original data. This finding led me to investigate the effects of smaller amounts of AI-generated data in more detail.

## Final Analysis: The Impact of AI-Generated Data  

In the final stage, I further refined my analysis by focusing on a narrower range of collapse rates (0% to 10% in 1% increments). Through multiple iterations and averaging the results, I confirmed that any inclusion of AI-generated data—no matter how small—resulted in a decline in model performance.

For instance, the difference in accuracy between 0% and 10% AI-generated data at a 1,000-review sample size was small but notable, illustrating that even seemingly insignificant amounts of AI-generated data still negatively impacted the model.

## Real-World Implications  

In an age where AI is being increasingly used to generate content—from reviews to news articles—this project reveals a hidden danger. If companies rely too much on AI-generated data to train their models, they could see a sharp decline in performance. This degradation could affect industries ranging from online retail, which depends on accurate sentiment analysis, to finance, where predictive models are crucial for decision-making.

The findings underscore the importance of curating high-quality, human-verified data for training AI models. As AI-generated content becomes more prevalent, the risk of polluting new training datasets grows, and awareness of these issues is essential for developing robust, trustworthy systems.

## Conclusion  

This project not only deepened my understanding of model collapse but also emphasized the critical balance between leveraging AI and ensuring data integrity. The rise of AI-generated content makes it more important than ever to be vigilant about the quality of data used to train our models.

I look forward to continuing my exploration in this fascinating field. My future projects will likely expand this research into domains such as text generation and recommendation systems, where model collapse could pose significant risks.  

Feel free to explore the graphs and datasets I generated throughout this project, which illustrate these findings in greater detail. I welcome any feedback or opportunities for collaboration.

You can find my code and all related resources on my [GitHub page](https://github.com/LoreviQ/ModelCollapse).