# 🎬 End-to-End Movie Recommendation System

## 📌 Project Overview

This project focuses on building an **End-to-End Movie Recommendation System** using a combination of **Natural Language Processing (NLP)**, **Machine Learning (ML)**, and **Web Development** technologies. The system recommends movies based on their content by analyzing movie descriptions, genres, and taglines.

The recommendation engine is built using **Content-Based Filtering**, where movies with similar textual features are identified and suggested to users.

---

# 🚀 Features

* Movie recommendations based on content similarity
* NLP-based text preprocessing pipeline
* TF-IDF Vectorization for feature extraction
* Cosine Similarity for recommendation scoring
* FastAPI backend for serving recommendations
* Streamlit frontend for an interactive user interface
* TMDB API integration for posters, movie details, and metadata
* Pickle-based model deployment for fast inference

---

# 🧠 Theory and Key Concepts

## Natural Language Processing (NLP)

The recommendation engine relies heavily on NLP techniques to process textual movie data.

### Text Preprocessing Includes:

* Tokenization
* Stopword Removal
* Lemmatization
* Lowercasing
* Punctuation Removal

These steps ensure the textual data is cleaned and standardized before model training.

---

## TF-IDF Vectorization

TF-IDF (**Term Frequency-Inverse Document Frequency**) converts textual movie information into numerical vectors.

It assigns higher importance to words that:

* Appear frequently within a movie description
* Appear less frequently across the entire dataset

This helps capture unique movie characteristics.

---

## Cosine Similarity

Cosine Similarity measures how similar two movie vectors are.

### Interpretation

* Cosine Similarity = **1**

  * Movies are highly similar
* Cosine Similarity = **0**

  * Movies are unrelated

The recommendation engine uses this score to find and rank similar movies.

---

# 🛠️ Tech Stack

| Technology   | Purpose                                    |
| ------------ | ------------------------------------------ |
| Python       | Core programming language                  |
| Pandas       | Data cleaning and manipulation             |
| NumPy        | Numerical computations                     |
| Scikit-Learn | TF-IDF Vectorizer and recommendation logic |
| NLTK         | NLP preprocessing                          |
| Pickle       | Model serialization                        |
| FastAPI      | Backend API                                |
| Streamlit    | Frontend web application                   |
| TMDB API     | Movie metadata and posters                 |

---

# 📂 Project Workflow

## 1. Data Preparation

The movie dataset is loaded into a Pandas DataFrame.

### Cleaning Steps

* Remove duplicate rows
* Handle missing values
* Extract genre information
* Drop invalid records

---

## 2. Feature Engineering

A new feature called **Tags** is created by combining:

* Overview
* Genres
* Tagline

This consolidated text serves as the movie representation.

Example:

```text
Overview + Genres + Tagline
```

---

## 3. NLP Pipeline

Each movie tag undergoes:

### Lowercasing

```python
text.lower()
```

### Punctuation Removal

Using Regular Expressions.

### Tokenization

Splitting sentences into words.

### Stopword Removal

Removing common words such as:

```text
the, is, and, a, an
```

### Lemmatization

Converting words to their root form.

Example:

```text
running → run
movies → movie
```

---

## 4. TF-IDF Matrix Creation

The processed tags are converted into numerical vectors using:

```python
TfidfVectorizer(
    max_features=50000,
    ngram_range=(1,2)
)
```

This creates a high-dimensional sparse matrix representing all movies.

---

## 5. Recommendation Logic

The recommendation function:

1. Accepts a movie title
2. Finds the corresponding movie vector
3. Computes cosine similarity with all other movies
4. Sorts similarity scores
5. Returns the top recommendations

---

## 6. Model Export

The trained artifacts are stored as Pickle files.

### Generated Files

```text
df.pkl
indices.pkl
tfidf_matrix.pkl
tfidf.pkl
```

### Purpose

#### df.pkl

Contains the cleaned movie dataset.

#### indices.pkl

Maps movie titles to dataframe indices.

#### tfidf_matrix.pkl

Stores the TF-IDF feature matrix.

#### tfidf.pkl

Stores the trained TF-IDF vectorizer.

---

# ⚙️ Backend Architecture (FastAPI)

The backend is implemented using FastAPI.

## Responsibilities

* Load trained model artifacts
* Serve recommendation endpoints
* Fetch movie metadata from TMDB
* Handle recommendation requests

### Startup Process

When the server starts:

1. Load all Pickle files
2. Initialize recommendation resources
3. Build title-to-index mappings
4. Make recommendation endpoints available

### Main API Endpoints

```text
/health
/home
/tmdb/search
/movie/id/{tmdb_id}
/recommend/genre
/recommend/tfidf
/movie/search
```

---

# 🎨 Frontend Architecture (Streamlit)

The Streamlit application provides:

* Search interface
* Movie suggestions
* Movie details page
* Similar movie recommendations
* Genre-based recommendations
* Poster display using TMDB

### Features

* Dynamic search
* Home feed
* Interactive navigation
* Recommendation visualization

---

# 📊 Recommendation Pipeline

```text
Movie Dataset
      │
      ▼
Data Cleaning
      │
      ▼
Feature Engineering
      │
      ▼
NLP Processing
      │
      ▼
TF-IDF Vectorization
      │
      ▼
Cosine Similarity
      │
      ▼
Top Similar Movies
      │
      ▼
FastAPI Backend
      │
      ▼
Streamlit Frontend
```

---

# 📁 Project Structure

```text
project/
│
├── app.py
├── main.py
├── df.pkl
├── indices.pkl
├── tfidf.pkl
├── tfidf_matrix.pkl
├── requirements.txt
├── .env
│
└── README.md
```

---

# 🔑 Environment Variables

Create a `.env` file:

```env
TMDB_API_KEY=YOUR_TMDB_API_KEY
```

---

# 📦 Installation

Clone the repository:

```bash
git clone <repository-url>
cd <repository-name>
```

Install dependencies:

```bash
pip install -r requirements.txt
```

---

# ▶️ Running the Application

### Start FastAPI Backend

```bash
uvicorn main:app --reload
```

### Start Streamlit Frontend

```bash
streamlit run app.py
```

---

# 📈 Future Improvements

* Hybrid Recommendation System
* Collaborative Filtering
* User Authentication
* Personalized Recommendations
* Watchlist Feature
* Movie Rating Prediction
* Model Optimization

---

# 👨‍💻 Author

Developed as an End-to-End Machine Learning and NLP project demonstrating:

* Data Processing
* Feature Engineering
* NLP
* Recommendation Systems
* API Development
* Full Stack ML Deployment

---

## Quick Start

```bash
pip install -r requirements.txt
streamlit run app.py
```
