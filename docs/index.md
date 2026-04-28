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

## Dataset Overview

The dataset used in this project was sourced from an academic institution and contains physicochemical measurements of wine samples, each evaluated and assigned a quality score by expert tasters.
<table>
  <tr><th>Property</th><th>Value</th></tr>
  <tr><td>Observations</td><td>~4600</td></tr>
  <tr><td>Features</td><td>11 physicochemical variables</td></tr>
  <tr><td>Target variable</td><td>Quality score (3–9)</td></tr>
  <tr><td>Source</td><td>Academic dataset</td></tr>
</table>

<table>
  <tr>
    <th>Feature</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>fixed.acidity</td>
    <td>Non-volatile acids in the wine</td>
  </tr>
  <tr>
    <td>volatile.acidity</td>
    <td>Amount of acetic acid, linked to vinegar taste</td>
  </tr>
  <tr>
    <td>citric.acid</td>
    <td>Adds freshness and flavor</td>
  </tr>
  <tr>
    <td>residual.sugar</td>
    <td>Sugar remaining after fermentation</td>
  </tr>
  <tr>
    <td>chlorides</td>
    <td>Salt content in the wine</td>
  </tr>
  <tr>
    <td>free.sulfur.dioxide</td>
    <td>Free form of SO₂, acts as antimicrobial</td>
  </tr>
  <tr>
    <td>total.sulfur.dioxide</td>
    <td>Total SO₂, indicator of preservation</td>
  </tr>
  <tr>
    <td>density</td>
    <td>Mass per unit volume</td>
  </tr>
  <tr>
    <td>pH</td>
    <td>Acidity level on a 0–14 scale</td>
  </tr>
  <tr>
    <td>sulphates</td>
    <td>Additive that contributes to SO₂ levels</td>
  </tr>
  <tr>
    <td>alcohol</td>
    <td>Percentage of alcohol by volume</td>
  </tr>
  <tr>
    <td>quality</td>
    <td>Expert rating from 3 to 9 (target variable)</td>
  </tr>
</table>
As part of the data preparation process, the original quality score was transformed into a binary classification label — High (score > 6) and Low (score ≤ 6) — to align the problem with the business objective and reflect the winery's decision context.

## Exploratory Data Analysis

### Target Variable Distribution
The quality scores are heavily concentrated around values 5 and 6, which together account for the vast majority of observations. Scores at the extremes — 3, 4, 8, and 9 — are significantly underrepresented, reflecting the natural difficulty of producing wines at the quality boundaries.
<p align="center">
  <img src="images/quality_dist" width="600" alt="Profit comparison by model">
</p>
This concentration has a direct implication for the modeling phase: once the target is transformed into a binary label, the resulting class distribution is notably imbalanced, with Low quality wines representing approximately 78% of the dataset. Standard accuracy metrics are therefore insufficient to evaluate model performance in this context.

### Feature Correlations
<p align="center">
  <img src="images/correlation_heatmap.png" width="600" alt="Profit comparison by model">
</p>
The heatmap reveals several relevant relationships. Alcohol shows the strongest positive correlation with quality (0.43), suggesting that higher alcohol content tends to be associated with better-rated wines. On the other hand, density presents a notable negative correlation (-0.31), which is partly explained by its strong inverse relationship with alcohol (-0.78).
Two pairs of variables also show signs of multicollinearity worth noting: residual sugar and density (0.84), and free sulfur dioxide and total sulfur dioxide (0.62). This was taken into account during the modeling phase, particularly for Logistic Regression, which is sensitive to correlated features.

### Key Variable Relationships
As part of the exploratory analysis, pairwise relationships between all variables were examined. The following plots focus on two relationships that stood out due to their strong correlation and the presence of extreme observations.
<p align="center">
  <img src="images/scatterplots_1.png" width="600" alt="Profit comparison by model">
</p>
The plots reveal clear directional relationships between the variables, but also expose a small number of extreme observations positioned far from the main data cluster — particularly visible in the Density vs Residual Sugar plot. These findings motivated the outlier treatment applied in the following data preparation phase.

<p align="center">
  <img src="images/profit_chart.png" width="600" alt="Profit comparison by model">
</p>

