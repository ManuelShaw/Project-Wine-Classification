---
title: Wine Quality Classification
---

<style>
h1:first-of-type {
  display: none;
}
</style>


# Wine Quality Classification with Cost-Sensitive Evaluation

## Problem Definition
.
A growing winery aiming to expand into international markets faces a critical decision challenge: how to reliably identify which wines should be positioned as premium products.

Premium wines represent a significant opportunity for the business. They are sold at higher prices, packaged differently, and contribute directly to both profitability and brand reputation. In contrast, standard wines are sold with minimal margins and play a more operational role in the product portfolio.

However, the company currently lacks access to sommeliers or expert evaluators to assess wine quality before commercialization. This creates a risk in the decision process:

- If a high-quality wine is classified as standard, the company misses a potential revenue opportunity.
- If a low-quality wine is classified as premium, the consequences are substantially more severe: customer dissatisfaction, potential returns of entire batches, and reputational damage in new markets.

To address this, the company relies on historical laboratory data, where wines were evaluated by experts and assigned quality scores based on physicochemical properties such as acidity, pH, and alcohol content.

The objective of this project is to develop a predictive model that supports this classification decision in a consistent and scalable way. Unlike traditional classification problems, this scenario requires explicitly accounting for the **asymmetric cost of errors**, where false positives (incorrectly labeling a low-quality wine as premium) are significantly more costly than false negatives.

Additionally, the classification decision is not fixed: it depends on selecting an appropriate decision threshold, which directly impacts in the decision whether to prioritize capturing premium opportunities and avoiding costly mistakes. 

This project therefore approaches the problem as a **cost-sensitive classification task**, where model performance is evaluated not only through statistical metrics, but through its impact on business outcomes.
.

> **Note:** This is a simulated business case designed to reflect real-world decision-making scenarios.


## Business Objective

The goal of this project is not only to classify wines correctly, but to maximize business value by explicitly accounting for the cost of different types of prediction errors.

To reflect real-world decision making, a cost matrix is defined:

True Positive (+5): High-quality wines correctly classified as premium
True Negative (+1): Low-quality wines correctly classified as standard
False Positive (-10): Low-quality wines incorrectly classified as premium
False Negative (0): High-quality wines incorrectly classified as standard

This cost structure reflects that incorrectly labeling a low-quality wine as premium is significantly more damaging than missing a high-quality opportunity.

As a result, the objective is to develop a model that optimizes decision-making, prioritizing the reduction of costly false positives while still capturing valuable premium wines.


<p align="center">
  <img src="images/profit_chart.png" width="600" alt="Profit comparison by model">
</p>

