# Movie Recommendation System

A content-based movie recommendation system that suggests movies similar to a title selected by the user. It uses movie metadata from the TMDB 5000 dataset, converts relevant information into text tags, and compares movies using vectorization and cosine similarity.

## Features

- Recommends movies based on a movie title entered by the user.
- Uses movie genres, keywords, overview, cast, and director information to find similar movies.
- Applies text preprocessing and stemming to improve text matching.
- Uses CountVectorizer to convert movie tags into numerical vectors.
- Uses cosine similarity to calculate similarity between movies.
- Returns the top 5 similar movie recommendations.

## Technologies Used

- Python
- Pandas
- NumPy
- NLTK
- Scikit-learn
- Jupyter Notebook
- Pickle

## Dataset

This project uses the TMDB 5000 Movie Dataset, consisting of:

- `tmdb_5000_movies.csv`
- `tmdb_5000_credits.csv`

The two datasets are merged using the movie title. The project then selects the movie ID, title, overview, genres, keywords, cast, and crew information for processing.

## How It Works

1. **Load the data:** Read the movies and credits CSV files using Pandas.
2. **Merge the datasets:** Combine the movie and credits information using the title field.
3. **Prepare movie information:** Keep the relevant fields and remove rows with missing values and duplicate records.
4. **Extract features:** Process genres and keywords, select the top three cast members, and extract the director from the crew information.
5. **Create tags:** Combine the overview, genres, keywords, cast, and director into a single text field for each movie.
6. **Preprocess text:** Convert text to lowercase and apply stemming using NLTK's Porter Stemmer.
7. **Vectorize tags:** Use `CountVectorizer` with a maximum of 5,000 features and English stop-word removal.
8. **Calculate similarity:** Apply cosine similarity to compare the movie vectors.
9. **Recommend movies:** Find the selected movie and return the five most similar titles.

## Project Files

```text
Movie-Recommendation-System/
│
├── movie_recommendation_system.ipynb
├── movie_list.pkl
├── similarity.pkl
├── tmdb_5000_movies.csv
├── tmdb_5000_credits.csv
└── requirements.txt
```

| File | Description |
|---|---|
| `movie_recommendation_system.ipynb` | Notebook containing data preparation, feature extraction, vectorization, similarity calculation, and recommendation logic. |
| `movie_list.pkl` | Saved processed movie data used by the recommendation system. |
| `similarity.pkl` | Saved cosine-similarity values between movies. |
| `tmdb_5000_movies.csv` | TMDB movie metadata. |
| `tmdb_5000_credits.csv` | Movie cast and crew information. |
| `requirements.txt` | Python package dependencies. |

## Setup and Installation

### 1. Clone the repository

```bash
git clone <your-repository-url>
cd Movie-Recommendation-System
```

### 2. Create and activate a virtual environment (recommended)

**Windows**
```bash
python -m venv venv
venv\\Scripts\\activate
```

**macOS / Linux**
```bash
python3 -m venv venv
source venv/bin/activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Open the notebook

```bash
jupyter notebook movie_recommendation_system.ipynb
```

Run the notebook cells in order to explore the data processing and recommendation workflow.

## Recommendation Logic

The system uses a content-based approach. Each movie is represented by a combined text tag built from its overview, genres, keywords, top cast members, and director. These tags are converted into feature vectors using `CountVectorizer`. Cosine similarity is then used to identify movies whose feature vectors are closest to the selected movie.

The notebook's recommendation function returns the five highest-ranked similar movies, excluding the selected movie itself.

## Notes

- Use a movie title that exists in the processed movie list.
- The saved `.pkl` files are generated artifacts used by the recommendation workflow. Keep them in the expected project location when loading them.
- The notebook is the source of the data-processing and model-building workflow.
- The uploaded project files do not establish that a web interface or deployed application is included, so this README describes the recommendation system and notebook workflow rather than claiming a particular frontend or deployment.

## Future Improvements

- Add a user-friendly web interface for entering movie titles and viewing recommendations.
- Display movie posters, ratings, and release information.
- Handle title searches more robustly, including spelling variations.
- Add automated tests for data processing and recommendation results.
- Evaluate recommendation quality with suitable user or ranking-based metrics.

## Acknowledgements

- TMDB 5000 Movie Dataset
- Python and the open-source libraries used in this project
