# `TF-IDF` = Term Frequency – Inverse Document Frequency
## It’s a numerical statistic used in text mining/NLP to measure how important a word is in a document compared to a collection of documents (the corpus).

1. TF (Term Frequency)
 - Measures how frequently a word appears in a single document.
 - Formula:
   - TF(t,d) = Number of times term **t** appears in document d​ / Total number of terms in document **d**

## 📌 Example:

### Document = "The sun is bright. The sun shines."
  - Count of “sun” = 2
  - Total words = 6
  - TF("sun") = 2 / 6 = 0.33

2. IDF (Inverse Document Frequency) :
   - Measures how `rare` a word is across all documents.
   - How `importance` a word is across all documents.
   - Words like `"the", "is", "and"` appear everywhere → low importance. (Stop words)
   - Rare words like `"volcano", "hurricane"` → `high importance.`
   - Formula :
     - IDF (t) = log(Number of documents / Number of docuemnts containing t)

## 📌 Example:
  - Corpus = `100` documents = `total documents`
  - Word "sun" appears in `5 documents `]
    - IDF("sun") = log(100 / 5) = 2
3. TF-IDF :
  - Final weight = `TF × IDF`
  - **High** `TF-IDF` → word is frequent in a document but rare in the corpus.
  - **Low** TF-IDF → word is either too common (appears everywhere) or absent.

📌 Example :
  - TF("sun") = 0.33, IDF("sun") = 2
  - TF-IDF("sun") = 0.33 × 2 = 0.66

4. Normalization :
   1. Calculates all `TF-IDF` value for a doc
   2. Squares them , sum them , - takes Square root = `Vector length`
   3. Divides each value by that length

- - - - - -





