# Podcast

A simple, end-to-end pipeline for podcast data analysis and audience prediction.
# Technologies Used

  **Languages: Python 3

   **Libraries: pandas, NumPy, scikit-learn, matplotlib, seaborn

   **Models: Linear, Ridge, Lasso, Random Forest Regression

  **Environment: Jupyter Notebook

## Contents

- **podcast.ipynb**: use Rndomforestregression.
- **podcast-regression.ipynb**: Load, clean, and explore podcast metadata (titles, dates, durations, listener counts). Creates charts and features (day of week, keywords).Train and evaluate regression models (Linear, Ridge, Lasso) to predict listener counts and find growth drivers.



## Usage

- Open **podcast.ipynb** in JupyterLab or Jupyter Notebook. Follow cells to load data, clean, visualize, and engineer features.
- Open **podcast-regression.ipynb** to train models, run cross-validation, and view performance plots.

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

## Dependencies

- pandas
- numpy
- matplotlib
- scikit-learn
- seaborn (optional for extra plots)

## Dependencies

- pandas
- numpy
- matplotlib
- scikit-learn
- seaborn (optional for extra plots)

## License

MIT License. See [LICENSE](LICENSE) for details.
