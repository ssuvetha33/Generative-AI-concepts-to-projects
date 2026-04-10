# Real World Text Processing and Encoding

This project shows a complete text-processing workflow using real review data.

## Project files

- `amazon_raw_reviews.csv` — raw review data
- `amazon_processed_reviews.csv` — cleaned review data generated after preprocessing
- `real_world_text_processing_and_encoding.ipynb` — main notebook containing the full workflow
- `real_world_questions_interview_prep.md` — interview preparation notes for theory and real-world questions

## What this project covers

- text cleaning and preprocessing
- vocabulary creation
- one-hot encoding
- bag of words
- TF-IDF
- comparison of feature engineering methods
- sparse matrix analysis
- sentiment classification using Logistic Regression

## Workflow summary

1. Load the raw review dataset.
2. Clean and preprocess the review text.
3. Build a vocabulary from the processed text.
4. Create BoW, TF-IDF, and one-hot feature representations.
5. Compare the feature engineering methods.
6. Train a sentiment classification model using Logistic Regression.

## Output

The main processed file generated in this project is:

- `amazon_processed_reviews.csv`

## Notes

- The notebook is designed to be run step by step.
- The project uses traditional NLP feature-engineering approaches rather than embeddings.
- It is suitable for practice, assignments, and interview preparation.
