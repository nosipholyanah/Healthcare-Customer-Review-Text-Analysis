# Healthcare Customer Review Text Analysis

Topic modelling and sentiment analysis of healthcare customer reviews, to find out what customers are concerned about and how they feel.

## Project Overview

A medical scheme has noticed an increase in negative customer reviews and wants to understand the main areas of concern and the general sentiment of its customers. Because the scheme's own reviews are not available, this project uses Yelp reviews of US healthcare providers as a proxy.

The analysis answers two questions:

1. **What are customers saying?** Recurring themes are identified with topic modelling (LDA).
2. **How do customers feel?** Reviews are classified as positive, negative or neutral using VADER and TextBlob.

## Data

- **Source:** [Yelp Open Dataset](https://business.yelp.com/data/resources/open-dataset/), released for educational use.
- **Selection:** businesses in the Health & Medical category (11,890 of 150,346 businesses), keeping reviews that mention insurance, billing, claims and related words (insurance, claim, billing, bill, copay, deductible, coverage, authorisation, referral and similar).
- **Size:** 24,685 matching reviews, 24,596 after removing 86 duplicate texts and 3 very short reviews.
- **Not included:** the Yelp data and extracted review records are not stored in this repository, in line with Yelp's terms.

## Workflow

1. Data selection and extraction
2. Data cleaning and preprocessing (lowercase, remove links and punctuation, stopwords, lemmatisation)
3. Exploratory data analysis (star ratings, review length, word frequencies, word clouds)
4. Feature selection (vocabulary pruning with `min_df`, `max_df` and `max_features`)
5. Topic modelling with LDA, tuning the number of topics and alpha using UMass coherence
6. Sentiment analysis with VADER and TextBlob, compared against star-based labels
7. Cut-off tuning on training data and evaluation on unseen test data
8. Interpretation and recommendations

## Key Findings

**Topics (what customers are saying)**

| Topic | Share of reviews | Average stars | Reviews classified as negative |
|---|---|---|---|
| Billing, appointment and administration | 48.87% | 1.40 | 85.37% |
| Eye care and general patient experience | 29.52% | 3.81 | 38.57% |
| Dental care | 21.61% | 3.22 | 46.83% |

Billing, appointment and administration was the largest and most negative topic. Two of the three topics mainly reflect the type of provider rather than a type of concern.

**Sentiment (how customers feel)**

Overall, 63.23% of reviews were classified as negative, 27.33% as positive and 9.45% as neutral, close to the 61% of reviews rated one or two stars.

| Model | Accuracy | Macro-F1 | Negative recall |
|---|---|---|---|
| VADER (default cut-offs) | 0.712 | 0.490 | 0.611 |
| TextBlob (default cut-offs) | 0.508 | 0.393 | 0.276 |
| VADER (tuned) | 0.745 | 0.507 | 0.671 |
| TextBlob (tuned) | 0.758 | 0.550 | 0.873 |

Tuning the cut-offs on the training data improved negative recall considerably, at the cost of lower negative precision for TextBlob (0.98 to 0.84) and almost no neutral predictions. Tuned TextBlob performed best and was used for the sentiment-by-topic analysis.

## Skills Demonstrated

- Text preprocessing with NLTK and Scikit-learn
- Topic modelling with LDA, choosing settings with coherence scores
- Comparing lexicon-based sentiment tools against star-based labels
- Tuning sentiment cut-offs on training data and testing on unseen data
- Interpreting results for a business audience and making recommendations

## Tools and Technologies

| Category | Tools |
|---|---|
| Programming | Python |
| Data manipulation | Pandas, NumPy |
| Visualisation | Matplotlib, Seaborn, WordCloud |
| Text preprocessing | NLTK |
| Topic modelling | Scikit-learn (CountVectorizer, LDA) |
| Sentiment analysis | VADER, TextBlob |
| Evaluation | Scikit-learn |

## Repository Contents

- `notebooks/healthcare_review_text_analysis.ipynb` – the analysis and modelling.
- `figures/` – charts used in this README.
- `requirements.txt` – Python package dependencies.

## How to Run

1. Download the Yelp Open Dataset from the link above and accept its terms.
2. Place `yelp_academic_dataset_business.json` and `yelp_academic_dataset_review.json` in the same folder as the notebook.
3. Install the dependencies with `pip install -r requirements.txt`.
4. Open the notebook and run all cells from top to bottom. The first run reads the large review file in chunks and may take a while. A random seed of 42 is used for reproducibility.

## Limitations

- The reviews relate to US healthcare providers, so they should not be treated as representative of South African medical scheme members.
- Reviewers are self-selected, and keyword filtering may exclude relevant reviews or inflate the share of billing topics.
- Two of the three topics mainly reflect provider type, and the word "time" appears in all three topics.
- Star ratings are only an approximate reference for sentiment, and the cut-offs were tuned against them.
- Neutral reviews were only about 4% of the data, so neutral results are unreliable.
- Lexicon-based tools can miss sarcasm and mixed opinions, for example polite wording that accompanies a complaint.

## Disclaimer

This project was completed for academic and portfolio purposes. The findings are exploratory and should not be treated as representative of any specific healthcare provider or medical scheme. The Yelp data remains subject to Yelp's terms of use.
