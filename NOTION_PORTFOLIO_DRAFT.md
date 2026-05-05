# Predicting Customer Review Satisfaction from Brazilian E-commerce Logistics Data

## Portfolio Summary

This project investigates how delivery, logistics, payment, seller, customer, and review information can be used to understand customer satisfaction in a Brazilian e-commerce marketplace. I built an end-to-end analytics workflow from multi-table data preparation to feature engineering, model comparison, and business interpretation.

The project began with a structured kickoff mind map, where I mapped the available datasets, possible assumptions, feature ideas, and modelling directions. This helped turn a broad e-commerce dataset into a focused business problem: identifying the operational factors associated with review score and predicting whether an order is likely to receive a positive or negative review.

## Problem

Customer reviews are a direct signal of marketplace experience, but poor reviews often reflect upstream operational issues such as delayed delivery, long waiting time, high freight cost, or mismatches between customer and seller location.

The core question was:

> Can we use order, logistics, payment, seller, customer, and geolocation data to predict review satisfaction and identify the operational drivers behind low-review-risk orders?

## My Analytics Approach

### 1. Data Understanding and Planning

I started by mapping the raw tables and possible analytical paths:

- Customer and seller location.
- Order status and timestamps.
- Review score and review comments.
- Product and order item information.
- Payment value and payment type.
- Geolocation data for distance-based features.

The kickoff mind map helped define assumptions, potential features, and modelling choices before moving into notebooks.

### 2. Data Cleaning and Integration

The project involved merging multiple e-commerce tables into a single analytical dataset. Key preparation steps included:

- Cleaning order, payment, review, product, customer, seller, and order-item data.
- Normalizing geolocation records at zip-code level.
- Handling missing values and inconsistent city names.
- Converting date columns into usable timestamp formats.
- Creating a merged order-level dataset for modelling.

### 3. Feature Engineering

The most important part of the project was transforming operational events into analytical features. I engineered features such as:

- Total waiting time.
- Logistics time.
- Estimated vs. actual delivery time.
- Delivery accuracy.
- Late or early arrival time.
- Same-state customer-seller indicator.
- Distance between seller and customer.
- Freight value and payment value.
- Seller order volume.

These features helped connect customer satisfaction to concrete operational behavior.

### 4. Review Text Exploration

The original review comments were translated into English and explored using word clouds. This gave a qualitative layer to the analysis by showing recurring themes in high-score and low-score reviews.

### 5. Modelling and Evaluation

The target variable was transformed into a binary classification problem: positive vs. negative review experience.

Because the review classes were imbalanced, I compared two strategies:

- SMOTE oversampling.
- Class-weighted modelling.

Models tested included:

- Random Forest.
- Gradient Boosting.
- XGBoost.

The final tuned Random Forest with class weighting achieved:

- Accuracy: 0.74
- Macro precision: 0.64
- Macro recall: 0.67
- Macro F1-score: 0.65

Although some models produced higher overall accuracy, the final selected model offered a more balanced view of both positive and negative review classes, which is more useful for customer-risk detection.

## Business Insights

The analysis shows that review satisfaction is closely linked to operational fulfillment. Delivery-related features, customer-seller geography, waiting time, and freight/payment context provide meaningful signals for predicting customer experience.

This type of model could help an e-commerce platform:

- Flag orders at risk of receiving poor reviews.
- Prioritize customer service outreach.
- Monitor seller delivery performance.
- Build dashboards for logistics and customer satisfaction.
- Identify where delivery promises may be misaligned with actual customer experience.

## Skills Demonstrated

- Data cleaning and multi-table joining.
- Feature engineering from timestamps and geolocation.
- Exploratory data analysis.
- Imbalanced classification.
- Model comparison and evaluation.
- Translating analytical results into business recommendations.
- Communicating a group academic project as a portfolio-ready analytics case.

## Suggested Interview Story

The strongest way to present this project in an interview is:

> I started with a broad marketplace dataset and narrowed it into a customer satisfaction problem. The most valuable part was not just modelling review score, but designing operational features that explained why a customer might leave a poor review. I compared different imbalance-handling strategies and chose the final model based on balanced classification performance, because identifying negative experiences mattered more than maximizing overall accuracy.

## Next Improvements

- Add SHAP or permutation importance to explain model predictions more clearly.
- Build a dashboard showing delivery risk by seller, region, and order timing.
- Create a public sample dataset for GitHub reproducibility.
- Convert notebooks into a clean pipeline with `src/` scripts and reusable functions.
- Add a concise model card explaining target definition, limitations, and ethical considerations.
