# Stats-101A-Film-Revenue-Prediction-Model
# 🎬 Predicting Box Office Revenue with Multiple Linear Regression  

## 📌 Project Overview  
This project (completed as part of **STATS 101A at UCLA**) explores the use of **multiple linear regression (MLR)** to predict movie gross revenue using film-level metrics. Our analysis is based on a Kaggle dataset containing **7,545 movies and 11 variables**, pared down to 510 usable observations after cleaning.  

The main goal: identify which factors (budget, runtime, rating, and rating count) are significant predictors of box office revenue and build interpretable regression models.  

---

## 📊 Dataset Description  
- **Source:** [Kaggle Movie Performance Dataset](https://www.kaggle.com/datasets/thedevastator/movies-performance-and-feature-statistics/data)  
- **Variables used:**
  - `Budget` (production + release costs, in USD)  
  - `Gross` (box office revenue, in USD)  
  - `Runtime` (movie duration in minutes)  
  - `Rating` (IMDb viewer rating, 1–10 scale)  
  - `Rating.Count` (number of IMDb votes)  

> Categorical variables (`Genre`, `Release Date`, `MPAA Rating`) were excluded for this analysis due to encoding complexity.  

---

## ⚙️ Methodology  
We built and compared three regression models:  

1. **Model 1: Raw Linear Regression**  
   - Gross ~ Budget + Runtime + Rating + Rating.Count  
   - $R^2 = 0.5319$  
   - Issues: non-normal residuals, leverage points.  

2. **Model 2: Box-Cox Transformations**  
   - Applied transformations on predictors and response.  
   - $R^2 = 0.6178$, assumptions upheld.  
   - Drawback: interpretation of coefficients becomes difficult.  

3. **Model 3: Log-Log Model (Final Model)**  
   - $\log(\text{Gross}) = 8.629 + 0.294\log(\text{Budget}) - 0.002(\text{Rating})^{2.89} + 0.491\log(\text{Rating.Count})$  
   - $R^2 = 0.5946$  
   - Most interpretable, satisfies regression assumptions.  
   - Runtime found to be insignificant and removed.  

---

## 📈 Key Findings  
- A **1% increase in Budget** is associated with a **0.29% increase in Gross Revenue**.  
- A **1% increase in Rating.Count** is associated with a **0.49% increase in Gross Revenue**.  
- Higher `Rating` values slightly **decrease predicted Gross**, suggesting that audience count matters more than rating itself.  
- Case 199 (“The Blair Witch Project”) highlighted as a leverage point: very low budget, extremely high revenue.  

---

## Challenges  
- No single variable strongly predicted revenue.  
- Power transformations improved assumptions but reduced interpretability.  
- Outliers and leverage points influenced regression diagnostics.  

---

## 🔧 Tech Stack  
- **Language:** R  
- **Libraries:** `ggplot2`, `car`, `MASS`, `dplyr` 
- **Methods:** MLR, Box-Cox transformations, ANOVA, VIF analysis, diagnostic plots  

---

## Future Work  
- **Feature Engineering:** Encode categorical variables (`Genre`, `MPAA Rating`) using one-hot encoding to capture more variance.  
- **Model Expansion:** Explore non-linear models such as Random Forests, Gradient Boosted Trees, or Neural Networks for higher predictive accuracy.  
- **Time Effects:** Incorporate `Release Date` to study seasonal or temporal box office trends.  
- **Regularization:** Apply Ridge/LASSO regression to address multicollinearity between predictors.  
- **Cross-Validation:** Improve generalizability by using k-fold cross-validation and train/test splits.  

---

## Authors  
- Moulik Chatterjee  
- Isaac Yu  
- Jason Chung  
- Peyton Garrett  
- Uriel Santa Cruz  

---

## 📖 References  
- Box Office Mojo, IMDb.com. *Top Lifetime Grosses by MPAA Rating*.  
- Rubin, R. (2025). *Box Office 2025 Predictions*. Variety.  

---

**Takeaway:** Budget and audience engagement (rating count) are stronger predictors of revenue than runtime or ratings alone.  
