---
title: Wine Quality Classification
---

<style>
h1:first-of-type {
  display: none;
}
</style>


# Wine Quality Classification with Cost-Sensitive Evaluation

Problem Definition

A growing winery aiming to expand into international markets faces a critical decision challenge: how to reliably identify which wines should be positioned as premium products.

Premium wines represent a significant opportunity for the business. They are sold at higher prices, packaged differently, and contribute directly to both profitability and brand reputation. In contrast, standard wines are sold with minimal margins and play a more operational role in the product portfolio.

However, the company currently lacks access to sommeliers or expert evaluators to assess wine quality before commercialization. This creates a risk in the decision process:

If a high-quality wine is classified as standard, the company misses a potential revenue opportunity.
If a low-quality wine is classified as premium, the consequences are substantially more severe: customer dissatisfaction, potential returns of entire batches, and reputational damage in new markets.

To address this, the company relies on historical laboratory data, where wines were evaluated by experts and assigned quality scores based on physicochemical properties such as acidity, pH, and alcohol content.

The objective of this project is to build a predictive model that supports this classification decision, not only in terms of accuracy, but in terms of maximizing business value.

Unlike traditional classification problems, this scenario requires explicitly incorporating the asymmetric cost of errors. In particular, false positives (incorrectly labeling a low-quality wine as premium) carry a significantly higher cost than false negatives.

Additionally, the classification decision is not fixed: it depends on selecting an appropriate decision threshold, which directly impacts the trade-off between capturing premium opportunities and avoiding costly mistakes.

This project approaches the problem as a cost-sensitive classification task, where model performance is evaluated based on its contribution to overall profitability rather than purely statistical metrics.

Note: This is a simulated business case designed to reflect real-world decision-making scenarios.


<p align="center">
  <img src="images/profit_chart.png" width="600" alt="Profit comparison by model">
</p>

