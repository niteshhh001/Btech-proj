# Spotify Song Recommendation System

This project is a song recommendation system that uses the Spotify Million Song Dataset to recommend songs based on their audio features and artist similarity. The recommendation engine is built using a content-based filtering approach and leverages the `Annoy` library for efficient nearest-neighbor search. 🎧

-----

## Features

  * **Song Recommendation:** Recommends a list of songs similar to a given song title.
  * **Exploratory Data Analysis:** Includes a detailed EDA of the Spotify dataset, with visualizations of audio feature distributions and trends over time.
  * **Model Evaluation:** The recommendation model is evaluated using the Precision@k metric.
  * **Advanced Visualization:** Uses t-SNE to visualize song clusters based on their features.

-----

## Dataset

The project uses the **Spotify Million Song Dataset**, which contains audio features for over a million songs. The dataset is available on Kaggle.

The following data files are included in this repository:

  * `data.csv`: The main dataset with audio features for each song.
  * `data_by_genres.csv`: A dataset with audio features aggregated by genre.
  * `data_by_year.csv`: A dataset with audio features aggregated by year.

-----

## Installation

To run this project, you'll need Python 3 and the following libraries. You can install them using pip:

```bash
pip install numpy pandas matplotlib seaborn scikit-learn annoy
```

-----

## Usage

1.  **Run the `Song_Recommendation.ipynb` notebook:** This notebook contains the complete workflow for building and testing the recommendation model.
2.  **Use the `get_recommendations_annoy` function:** You can use this function to get recommendations for any song in the dataset.

<!-- end list -->

```python
# Example of how to get song recommendations
song_to_recommend = 'Bohemian Rhapsody - Remastered 2011'
recommendations = get_recommendations_annoy(song_to_recommend, 'song_recommendation.ann', df)
print(f"Recommendations for '{song_to_recommend}':")
print(recommendations)
```

-----

## Methodology

### 1\. Exploratory Data Analysis (EDA)

The `EDA.ipynb` notebook provides a comprehensive analysis of the dataset. It includes:

  * Distributions of audio features like `danceability`, `energy`, `valence`, and `acousticness`.
  * The trend of song popularity over the years.
  * Correlation between different audio features.

### 2\. Feature Engineering

The following feature engineering steps are performed in `Song_Recommendation.ipynb`:

  * **Numerical Features:** Audio features are scaled to a range between 0 and 1 using `MinMaxScaler`.
  * **Categorical Features:** The `year` is converted into decades to capture the sound of different eras.
  * **Text Features:** The `artists` column is processed using `TfidfVectorizer` to convert artist names into a numerical format.

### 3\. Model Building

The recommendation model is built using the following steps:

  * **Combined Features:** All the engineered features are combined into a single sparse matrix.
  * **Annoy Index:** An `AnnoyIndex` is built for fast approximate nearest neighbor search. This allows for efficient retrieval of similar songs. The index is saved to `song_recommendation.ann`.

### 4\. Model Evaluation

The model's performance is evaluated using **Precision@k**. This metric measures the proportion of recommended songs that are relevant, where "relevance" is defined as being by the same artist as the input song.

-----

## File Descriptions

  * **`.gitignore`**: Specifies which files and directories to ignore in Git.
  * **`EDA.ipynb`**: Jupyter Notebook for Exploratory Data Analysis of the dataset.
  * **`README.md`**: This file.
  * **`Song_Recommendation.ipynb`**: Jupyter Notebook containing the main code for the song recommendation system.
  * **`data.csv`**, **`data_by_genres.csv`**, **`data_by_year.csv`**: The datasets used in the project.

-----

## Advanced Visualization

The `Song_Recommendation.ipynb` notebook includes a t-SNE visualization to plot the songs in a 2D space based on their features. This helps in understanding how songs are clustered together by decade and popularity.

-----

## Future Improvements

  * **Hybrid Recommendation System:** Combine the content-based approach with collaborative filtering for more personalized recommendations.
  * **Web Application:** Develop a simple web interface to make the recommendation system more user-friendly.
  * **More Features:** Incorporate more features, such as song lyrics or user listening history, to improve the recommendations.
