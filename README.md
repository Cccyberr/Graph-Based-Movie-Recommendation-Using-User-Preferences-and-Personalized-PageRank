# Graph-Based Movie Recommendation

A graph-based movie recommendation system that uses **user preferences, movie genres, and Personalized PageRank** to generate personalized Top-5 movie recommendations.

## Overview

This project represents users, movies, and genres as nodes in a **weighted heterogeneous graph**. User–Movie relationships represent movie ratings, while Movie–Genre relationships represent genre associations.

**Personalized PageRank** is then applied using a user's training ratings as preference information. The resulting PageRank scores are used to rank candidate movies and generate personalized recommendations while excluding movies the user has already rated.

## Dataset

The project uses the **MovieLens 2K dataset**.

The dataset contains:

- 2,113 unique users
- 10,197 movies
- 855,598 rating records
- 20 genres
- 20,809 Movie–Genre relationships

## Methodology

The recommendation pipeline consists of:

1. Data loading and preprocessing
2. Data consistency checks
3. Weighted heterogeneous graph construction
4. Graph-level analysis
5. Personalized PageRank
6. Removal of already-rated movies
7. Top-5 recommendation generation
8. Precision@5 evaluation
9. Comparison with a popularity-based baseline

### Graph Structure

The graph contains three node types:

- **User**
- **Movie**
- **Genre**

Two types of weighted relationships are used:

- **User → Movie:** rating normalized by 5
- **Movie → Genre:** reciprocal of the number of genres associated with the movie

## Personalized PageRank

For each evaluation user, a personalization vector is created from their training ratings. Personalized PageRank propagates preference information through the graph and assigns scores to movie nodes.

Movies already rated by the user are removed before generating the final Top-5 recommendations.

## Evaluation

A leakage-free **80/20 train-test split** is used for each selected evaluation user.

- 1,872 users met the minimum requirement of 50 ratings
- 20 users were reproducibly selected using `random_state=42`
- 5 recommendations were generated per user
- 100 recommendation slots were evaluated in total

### Results

| Method | Precision@5 |
|---|---:|
| Personalized PageRank | **32%** |
| Highly Rated Popularity | 25% |

The Personalized PageRank approach achieved higher Precision@5 than the implemented popularity baseline on the evaluated 20-user sample.

## Graph Statistics

The constructed graph contains:

- **12,330 nodes**
- **876,407 edges**
- **2,113 User nodes**
- **10,197 Movie nodes**
- **20 Genre nodes**

## Technologies Used

- Python
- Pandas
- NetworkX
- Scikit-learn
- Matplotlib
- Jupyter Notebook / Google Colab

## Project Structure

```text
graph-based-movie-recommendation/
│
├── notebook/
│   └── movie_recommendation.ipynb
│
├── data/
│   └── README.md
│
├── figures/
│   └── ...
│
├── README.md
└── requirements.txt
```

## Key Concepts

- Graph Mining
- Heterogeneous Graphs
- Personalized PageRank
- Recommendation Systems
- Graph-based Ranking
- Precision@5
- Train-Test Evaluation
- Network Analysis

## Limitations

The final evaluation was performed on a reproducibly selected sample of 20 users who satisfied the minimum rating requirement. Therefore, the reported 32% Precision@5 represents this evaluation setup and should not be interpreted as a general performance measure for all users or recommendation systems.

## Future Scope

Possible extensions include:

- Evaluating a larger number of users
- Adding additional recommendation baselines
- Exploring other personalization strategies
- Improving graph weighting methods
- Comparing different graph-based recommendation approaches

## Authors

**Krishna Priya M**  
**Adil Najeem**  
**Meenakshi Manoj**  
**Faais**

Computer Science and Engineering  
Amrita Vishwa Vidyapeetham, Amritapuri
