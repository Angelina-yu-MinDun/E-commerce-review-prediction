# Data and File Notes

## Source Context

This portfolio folder is a copy of the original academic group assignment. The original files remain unchanged in the Warwick course directory. All portfolio edits should happen only in this copied folder.

## Main Files

| File | Purpose | GitHub Recommendation |
|---|---|---|
| `Code/Step.1_Processing Geolocation Dataset.ipynb` | Processes geolocation zip-code data and normalizes city names. | Include |
| `Code/Step.2_Data Cleaning.ipynb` | Cleans and merges raw operational datasets. | Include |
| `Code/Step.3_Feature Engineering.ipynb` | Creates delivery, logistics, payment, seller, and geolocation features. | Include |
| `Code/Step.4_Feature correlation.ipynb` | Examines correlations between engineered features and review score. | Include |
| `Code/Step.5_Modelling and Evaluation.ipynb` | Trains and evaluates review prediction models. | Include |
| `Code/Appendix_WordCloud.ipynb` | Explores translated review text using word clouds. | Include |
| `brazilian_ecommerce_review_prediction_report.pdf` | Original group report, renamed for portfolio presentation. | Optional; include only if comfortable sharing group work |
| `brazilian_ecommerce_review_prediction_presentation.pdf` | Original group presentation, renamed for portfolio presentation. | Optional; include only if comfortable sharing group work |
| `planning/AIP_kickoff_mindmap.xmind` | Kickoff mind map showing early analytical thinking. | Optional; useful for Notion portfolio narrative |

## Processed Data Files

| File | Notes |
|---|---|
| `datasetfinal2.0.csv` | Cleaned merged dataset before final modelling features. |
| `Feature.csv` | Feature-engineered modelling dataset. This file may need to be rehydrated from cloud storage before copying or uploading. |
| `olist_geolocation_dataset_2.0.csv` | Processed zip-code geolocation dataset. |
| `olist_order_reviews_dataset_translation.csv` | Reviews with English-translated comment message. |

## Data Sharing Recommendation

For a public GitHub portfolio, avoid committing large processed CSV files directly. Instead:

- Keep notebooks and documentation public.
- Add data files to `.gitignore`.
- Mention the data source and processing steps in the README.
- If needed, provide a small sample dataset under `sample_data/`.

## Personal Portfolio Positioning

Use this project to emphasize:

- End-to-end analytics workflow.
- Multi-table data modelling.
- Feature engineering from operational timestamps and geolocation.
- Handling imbalanced classification.
- Translating model results into business actions.

Suggested title:

**Predicting Customer Review Satisfaction from Brazilian E-commerce Logistics Data**
