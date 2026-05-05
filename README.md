# Brazilian E-commerce Review Prediction

This project analyzes Brazilian e-commerce order, logistics, payment, geolocation, and review data to identify what drives customer satisfaction and to predict whether an order is likely to receive a positive or negative review.

This portfolio version reframes the project as an end-to-end data analytics case study, focusing on problem framing, data preparation, feature engineering, model comparison, and business interpretation.

## Business Question

How can an e-commerce platform use order, logistics, payment, seller, customer, and review data to understand the drivers of customer satisfaction and predict low-review-risk orders?

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
├── planning/
    └── AIP_kickoff_mindmap.pdf
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

The final evaluation focused on balancing predictive performance with minority-class detection. After tuning Random Forest with class weighting, the model achieved:

- Accuracy: 0.74
- Macro precision: 0.64
- Macro recall: 0.67
- Macro F1-score: 0.65

Earlier model comparisons showed that several models achieved higher overall accuracy, but the tuned class-weighted Random Forest provided a more balanced treatment of positive and negative review classes.

## Business Interpretation

The analysis suggests that customer review outcomes are strongly connected to logistics and fulfillment experience. Features such as delivery timeliness, waiting time, distance between seller and customer, and freight/payment context are useful signals for identifying orders at risk of poor customer satisfaction.

For an e-commerce platform, the model can support:

- Early warning for low-review-risk orders.
- Seller logistics monitoring.
- Customer service prioritization.
- Delivery experience dashboard design.
- Post-purchase retention analysis.

## Tech Stack

- Python
- pandas
- NumPy
- scikit-learn
- imbalanced-learn
- XGBoost
- matplotlib / seaborn
- Jupyter Notebook
