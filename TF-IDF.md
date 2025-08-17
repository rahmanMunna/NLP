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

## 📌 Example :
  - TF("sun") = 0.33, IDF("sun") = 2
  - TF-IDF("sun") = 0.33 × 2 = 0.66

4. Normalization :
   1. Calculates all `TF-IDF` value for a doc
   2. Squares them , sum them , - takes Square root = `Vector length`
   3. Divides each value by that length

- - - - - -
# 📌 Full Example :
 - Here 4 doc :
```
corpus = ['The sky is blue.', # 0
          'The sun is bright today.', # 1
          'The sun in the sky is bright.', # 2
          'We can see the shining sun, the bright sun.'] # 3
```
## Tokenizes your text (splits into words).
```
# Vocabulary
0: 'blue'
1: 'bright'
2: 'can'
3: 'in'
4: 'is'
5: 'see'
6: 'shining'
7: 'sky'
8: 'sun'
9: 'the'
10: 'today'
11: 'we'
```
## Step 1 – Document 0 tokenization
 - Document 0 = "The sky is blue."
 -  Lowercased and tokenized → `["the", "sky", "is", "blue"]`
 -  Total terms = 4
   
## Step 2 – TF (Term Frequency)
 - Term `"sky"` appears `1` time in Doc 0.
 - TF("sky",d0​) = 1 / 4 = .25
   
## Step 3 – IDF (Inverse Document Frequency) : 
 - `"sky"` appears in:
   - Doc 0: ✅
   - Doc 1: ❌ ("The sun is bright today." no "sky")
   - Doc 2: ✅ ("The sun in the sky is bright.")
   - Doc 3: ❌
     - So, "sky" appears in 2 documents out of 4.
  - IDF("sky") = log(4/2) = .6932

## Step 4 – TF × IDF (Raw TF-IDF) : 
 - TF-IDF("sky",d0​) = 0.25 × 0.6931 ≈ 0.173275

## Step 5 – Normalization : 
 - By default, TfidfVectorizer normalizes using L2 norm (vector length = 1).
 - We need to do this for all terms in `Document 0` before scaling.
   - Terms in Doc 0 and their raw TF-IDF:
     1. "blue": TF = 0.25, appears in 1 doc → IDF = log(4/1) = log(4) ≈ 1.3863 → raw TF-IDF = 0.25 × 1.3863 ≈ 0.346575
     2. "sky": 0.173275 (calculated above)
     3. "is": TF = 0.25, appears in 3 docs → IDF = log(4/3) ≈ 0.287682 → raw TF-IDF ≈ 0.0719205
     4. "the": TF = 0.25, appears in all docs → IDF = log(4/4) = 0 → raw TF-IDF = 0
## Step 6 – L2 Norm calculation : 
  - Norm = (0.346575)^2 + (0.173275)^2 + (0.0719205)^2 + 0^2
  - Sqrt(Norm)

## Step 7 – Normalized TF-IDF : 
 - Now divide `"sky"’s` raw value by the norm:
 - 0.393970 / 173275 ​≈ 0.4398


## Code : 





