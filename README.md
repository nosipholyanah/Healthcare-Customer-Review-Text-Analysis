# Healthcare Customer Review Text Analysis


## Project Overview

This project uses Natural Language Processing (NLP) techniques to analyse healthcare-related customer reviews and identify recurring service concerns and customer sentiment.
The analysis uses the Yelp Open Dataset, focusing on businesses within the Health & Medical category. Reviews containing insurance, billing, claims and related keywords were selected to explore feedback relevant to healthcare service experiences.
The project addresses two main questions:

1. What are customers saying? Identify recurring themes and areas of concern through topic modelling.
2. How do customers feel? Classify customer reviews as positive, negative or neutral through sentiment analysis.

## Objectives
- Explore and prepare healthcare-related customer review data.
- Identify recurring themes using Latent Dirichlet Allocation (LDA).
- Perform sentiment analysis using VADER and TextBlob.
- Compare default and tuned sentiment classification results.
- Interpret findings and identify areas for potential service improvement.

## Tools and Technologies
| Category | Tools |
|---|---|
| Programming | Python |
| Data manipulation | Pandas, NumPy |
| Data visualisation | Matplotlib, Seaborn |
| Text preprocessing | NLTK |
| Topic modelling | Scikit-learn (LDA, CountVectorizer) |
| Sentiment analysis | VADER, TextBlob |
| Model evaluation | Scikit-learn |

## Project Workflow

1. Data selection and extraction
2. Data cleaning and preprocessing
3. Exploratory Data Analysis (EDA)
4. Feature selection and vectorisation
5. Topic modelling using LDA
6. Sentiment analysis using VADER and TextBlob
7. Model tuning and evaluation
8. Interpretation and recommendations

## Key Findings

The topic modelling process identified three recurring themes within the selected reviews. Billing, appointments and administration represented the largest topic.
Sentiment analysis indicated that negative feedback was prominent in the selected sample. Tuned TextBlob achieved the strongest overall evaluation performance among the sentiment configurations tested.
The findings highlight billing and administrative experiences as areas requiring further investigation.

## Repository Contents
- `notebooks/` – Jupyter Notebook containing the analysis and modelling process.
- `reports/` – Final project report.
- `figures/` – Visualisations generated during the analysis.
- `requirements.txt` – Python package dependencies.

## Dataset
Source: [Yelp Open Dataset](https://business.yelp.com/data/resources/open-dataset/)
The dataset contains publicly available business information and customer reviews. Only selected healthcare-related reviews were used in this analysis.
The original dataset and extracted review records are not included in this repository.

## Limitations
The reviews relate to US healthcare providers and should not be interpreted as representative of South African medical scheme members. Keyword filtering and voluntary review submission may also influence the findings.

## Disclaimer
This project was conducted for academic and portfolio purposes. The findings are exploratory and should not be treated as representative of the experiences of a specific healthcare provider or medical scheme.
