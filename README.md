# Brazilian E-commerce Review Prediction

This project analyzes Brazilian e-commerce order, logistics, payment, geolocation, and review data to identify what drives customer satisfaction and to predict whether an order is likely to receive a positive or negative review.

This portfolio version reframes the project as an end-to-end data analytics case study, focusing on problem framing, data preparation, feature engineering, model comparison, and business interpretation.

## Business Question

How can an e-commerce platform use order, logistics, payment, seller, customer, and review data to understand the drivers of customer satisfaction and predict low-review-risk orders?

## Data Context

The project uses Brazilian e-commerce marketplace data covering customers, sellers, orders, order items, payments, products, reviews, and geolocation. The original dataset contained roughly:

- 3,095 sellers
- 89,322 customers
- 99,441 orders
- 96,096 reviews

After cleaning, merging, and feature preparation, the modelling dataset contained approximately 82,000 usable records. Review scores were converted into a binary target:

- Positive review: 4-5 stars
- Negative review: 1-3 stars

The cleaned dataset was imbalanced, with approximately 78% positive reviews and 22% negative reviews.

## Project Highlights

- Built a multi-table analytical dataset from customer, order, payment, review, seller, product, and geolocation sources.
- Engineered operational features such as waiting time, logistics time, delivery accuracy, late or early arrival time, customer-seller distance, same-state delivery, freight value, and payment value.
- Converted review score into a binary classification target for positive vs. negative customer experience.
- Addressed class imbalance using SMOTE and class-weighted modelling.
- Compared Random Forest, Gradient Boosting, and XGBoost models.
- Used review text translation and word cloud analysis to explore customer perception themes.

## Repository Structure

```text
.
├── Code/
│   ├── Step.1_Processing Geolocation Dataset.ipynb
│   ├── Step.2_Data Cleaning.ipynb
│   ├── Step.3_Feature Engineering.ipynb
│   ├── Step.4_Feature correlation.ipynb
│   ├── Step.5_Modelling and Evaluation.ipynb
│   └── Appendix_WordCloud.ipynb
├── ecommerce_review_prediction_presentation.pdf
├── planning/
│   └── Kick off planning.pdf
└── README.md
```

## Methodology

1. **Data preparation**
   - Standardized geolocation records by averaging latitude and longitude at zip-code level.
   - Cleaned order, payment, review, customer, seller, product, and order-item tables.
   - Merged the cleaned tables into a modelling-ready order-level dataset.

2. **Feature engineering**
   - Created delivery and logistics metrics, including waiting time, logistics time, delivery accuracy, estimated vs. actual delivery time, and late or early arrival time.
   - Added marketplace context features such as seller order volume, same-state delivery, freight value, payment value, and customer-seller distance.

3. **Exploratory analysis**
   - Checked feature correlations with review score.
   - Explored review text using translated comments and word clouds.

4. **Modelling**
   - Trained classification models with SMOTE and class-weight strategies.
   - Compared Random Forest, Gradient Boosting, and XGBoost.
   - Tuned Random Forest using randomized search.

## Model Results

The modelling stage compared five configurations across Random Forest, Gradient Boosting, and XGBoost using SMOTE and class-weight strategies for imbalance handling.

The selected communication focus was **Random Forest with class weighting**, because it performed strongly for identifying likely positive reviewers. In the presentation artifact, the model is summarized by its positive-class precision:

- Positive-class precision: 82%

Hyperparameter tuning improved balance between the positive and negative classes, but introduced a trade-off: the tuned model detected more negative-review cases while missing more positive-review cases. For the business objective of targeting customers likely to leave positive reviews, the class-weighted Random Forest before tuning aligned well with the prototype goal.

The tuned class-weighted Random Forest achieved:

- Accuracy: 0.74
- Macro precision: 0.64
- Macro recall: 0.67
- Macro F1-score: 0.65

This distinction matters because overall accuracy alone is not sufficient for an imbalanced dataset. Model selection depends on whether the business goal prioritizes targeting likely positive reviewers or detecting negative-review risk.

## Business Interpretation

The analysis suggests that customer review outcomes are strongly connected to logistics and fulfillment experience. Features such as delivery timeliness, waiting time, estimated vs. actual delivery accuracy, distance between seller and customer, and freight/payment context are useful signals for identifying review satisfaction patterns.

For an e-commerce platform, the model can support:

- Early warning for low-review-risk orders.
- Seller logistics monitoring.
- Customer service prioritization.
- Delivery experience dashboard design.
- Post-purchase retention analysis.

## Limitations

- The dataset is heavily skewed toward positive reviews, so imbalance handling is central to model interpretation.
- The data covers 2016-2018, which limits the model's ability to capture more recent customer behavior and market changes.
- Review score is treated as the target measure of customer sentiment, but customer experience is more nuanced than a numeric star rating.
- Review text was explored through word clouds, but deeper sentiment analysis was not fully integrated into the predictive model.
- Some engineered features may interact in ways that simple correlation analysis does not fully capture.

## Next Steps

- Add SHAP or permutation importance to explain model predictions more clearly.
- Integrate review-text sentiment features into the modelling dataset.
- Build a dashboard for monitoring review-risk patterns by seller, region, and delivery performance.
- Test additional feature interactions, especially between delivery time, distance, freight value, and seller behavior.
- Design a retraining and monitoring process so model performance can adapt as customer behavior changes.

## Tech Stack

- Python
- pandas
- NumPy
- scikit-learn
- imbalanced-learn
- XGBoost
- matplotlib / seaborn
- Jupyter Notebook
