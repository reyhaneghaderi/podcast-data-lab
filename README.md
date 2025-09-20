# Podcast

A simple, end-to-end pipeline for podcast data analysis and audience prediction.
# Technologies Used

  - Languages: Python 3

  - Libraries: pandas, NumPy, scikit-learn, matplotlib, seaborn

   - Models: Linear, Ridge, Lasso, Random Forest Regression

  -  Environment: Jupyter Notebook

## Contents

- **podcast.ipynb**: use Rndomforestregression.
- **podcast-regression.ipynb**: Load, clean, and explore podcast metadata (titles, dates, durations, listener counts). Creates charts and features (day of week, keywords).Train and evaluate regression models (Linear, Ridge, Lasso) to predict listener counts and find growth drivers.

## Results

After training and testing on your dataset, here are the observed metrics for each model:

| Model                        | Test RMSE (minutes) | Test R²   |
|------------------------------|---------------------|-----------|
| Linear Regression            | 17.72               | 0.5308    |
| Ridge Regression             | 17.72               | ~0.53     |
| Lasso Regression             | ~17.72              | ~0.53     |
| **Random Forest Regression** | **13.00**           | **0.75**  |

> **Note:** Random Forest Regression shows a lower RMSE (13.00 vs. 17.72) and higher R² (0.75 vs. 0.53) compared to Linear Regression, indicating more accurate predictions.

## Feature Importance

**Linear, Ridge, and Lasso Regression Coefficients**

- **Episode Length (minutes)**: The largest positive coefficient (~0.6), indicating longer episodes drive higher listener counts in all three linear models.
- **Number of Ads**:
  - 3 ads: Moderate positive effect (~0.08).
  - 2 ads: Smaller positive effect (~0.05).
  - 1 ad: Small positive effect (~0.02).
- **Host Popularity Percentage**: Slight positive impact (~0.02–0.03).
- **Guest Popularity Percentage**: Essentially zero (dropped by Lasso and heavily penalized by Ridge).
- **Other Features** (day of week, genre, sentiment, publication time): Coefficients near zero, indicating minimal linear effect.

**Random Forest Regression Importances**

The Random Forest model’s built-in feature_importances_ shows relative contributions:

| Feature                     | Importance |
|-----------------------------|------------|
| Episode Length (minutes)    | 0.96       |
| Host Popularity Percentage  | 0.05       |
| Number of Ads 3             | 0.03       |
| Guest Popularity Percentage | 0.02       |
| Number of Ads 2             | 0.01       |
| All Other Features          | <0.01     |

> **Note:** In the Random Forest model, episode length overwhelmingly drives predictions, with host popularity and ad counts playing minor roles. The linear and tree-based feature importance align in highlighting episode length as the key predictor.

## Data

Place your raw podcast data file (CSV or JSON) in the `data/` folder and update the file path in the first cell of `podcast.ipynb`.

# Key Skills Demonstrated

  - End-to-end ML pipeline design.

  - Feature engineering from structured metadata.

  - Regression modeling (Linear, Ridge, Lasso, Random Forest).

  - Model evaluation (RMSE, R², cross-validation).

  - Interpretability: comparing coefficients vs. feature_importances_.

  - Visualization with matplotlib and seaborn.
  # Impact & Applications

    - Helps media companies optimize podcast strategies (episode length, ad placement).

    - Supports data-driven content recommendations and marketing.

     - Demonstrates transferable skills in audience prediction, recommender systems, and digital media analytics.
  # Research Extensions
    - Multimodal Analysis
        Integrate NLP embeddings (titles, transcripts) and audio embeddings (wav2vec2, MFCCs).
        Use multimodal fusion to capture richer signals for audience prediction.
    - Stochastic Modeling of Audience Dynamics
       Apply stochastic processes (Poisson, Hawkes) to model listener arrivals and long-term growth.
      Connects directly with my background in stochastic data science.  
  # 📚 What I Learned

        - How to build an end-to-end ML pipeline: from raw podcast metadata → feature engineering → model evaluation.

        - Practical differences between linear models (Linear, Ridge, Lasso) and tree-based models (Random Forest) in terms of performance and interpretability.

        - Importance of feature importance analysis for explaining model predictions and identifying key drivers (episode length as the dominant factor).

        -  How regularization (Ridge/Lasso) penalizes less useful features (guest popularity, minor metadata).

        - Hands-on experience with cross-validation, error metrics (RMSE, R²), and visualization.

         - The importance of reproducibility: structuring notebooks, documenting results, and saving plots for clear reporting.

         - Awareness of research-level extensions (bias detection, causal inference, multimodal learning) and how industry projects can inspire academic research.

## License

MIT License. See [LICENSE](LICENSE) for details.
