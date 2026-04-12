# Encoding and Embedding Notebook Collection

A practical NLP learning collection focused on converting text into machine-readable vectors, from classic sparse techniques to dense Word2Vec embeddings.

## Contents

- `one-hot-encoding.ipynb`
   - Word-level one-hot encoding with `OneHotEncoder`
   - Tokenization and dense output inspection
- `bag_of_words.ipynb`
   - Bag of Words using `CountVectorizer`
   - Vocabulary extraction and count matrix examples
- `tf-idf-encoding.ipynb`
   - TF-IDF using `TfidfVectorizer`
   - Term weighting and interpretation
- `word2vec-cbow.ipynb`
   - CBOW training with Gensim (`sg=0`)
   - Pretrained Google News vectors (`word2vec-google-news-300`)
   - Average Word2Vec sentence representation and cosine similarity demo
- `word2vec-skip-gram.ipynb`
   - Skip-gram training with Gensim (`sg=1`)
   - Similar-word queries and practical Word2Vec usage
- `interview_prep.md`
   - Interview-focused notes for BoW, One-Hot, TF-IDF, CBOW, Skip-gram, and Average Word2Vec
   - Pros, cons, practical use cases, and quick comparison
- `interview_prep.pdf`
   - PDF export of interview notes for easy reading and revision
- `requirements.txt`
   - Project dependencies
- `uv_help.txt`
   - Environment and tooling notes

## Concepts Covered

- One-Hot Encoding
- Bag of Words (BoW)
- TF-IDF
- Word2Vec CBOW (`sg=0`)
- Word2Vec Skip-gram (`sg=1`)
- Average Word2Vec
- `most_similar(positive, negative)` for vector arithmetic
- Word2Vec `window` context behavior

## Setup

1. Create or activate your environment.
2. Install dependencies:

```bash
pip install -r requirements.txt
```

3. Open notebooks in VS Code or Jupyter:

```bash
jupyter notebook
```

## Learning Notes

- Notebooks are structured for interview preparation and concept clarity.
- Small corpora are intentionally used so outputs are easy to inspect.
- Pretrained Google News vectors are large and may take time on first download.
- Dense outputs are shown for readability; sparse formats are better for scale.

## Author

LinkedIn/GitHub: ssuvetha33
