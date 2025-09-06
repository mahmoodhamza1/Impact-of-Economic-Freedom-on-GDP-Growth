# 🌍 Impact of Economic Freedom on GDP Growth

This project explores the relationship between **economic freedom** and **GDP growth** using the **Heritage Foundation’s Economic Freedom Index 2019** dataset.  
The analysis applies **exploratory data visualization, non-parametric correlation analysis, and multiple regression modeling** to test whether greater economic freedom is associated with higher growth rates, and whether subcomponents such as **investment, labor, and trade freedom** play significant roles.

---

## ⚙️ Methodology

### Data
- **Dataset:** Heritage Foundation – *Economic Freedom Index 2019*.  
- **Variables used in analysis:**  
  - `2019 Score`: overall economic freedom score (0–100 scale).  
  - `Investment Freedom`, `Labor Freedom`, `Trade Freedom`: three key policy subcomponents.  
  - `GDP Growth Rate`: dependent variable (%).  
- Additional macroeconomic and institutional variables are available (e.g., property rights, inflation, unemployment, FDI inflows, government spending), but this study focuses on overall freedom and selected subcomponents.  

### Pre-processing
- Imported data into R and ensured all key columns were numeric.  
- Conducted initial **exploratory checks** for missing values, outliers, and data distribution.  
- Created visual summaries (violin plots, scatterplots) to inspect the spread of GDP growth relative to freedom scores.

### Step 1 – Normality Testing
- Applied **Shapiro-Wilk test** to both:  
  - `2019 Score` (economic freedom)  
  - `GDP Growth Rate`  
- **Finding:** both variables significantly deviated from normality (p < 0.001).  
- **Implication:** Pearson correlation was inappropriate. A **non-parametric correlation** measure (Spearman) was required.  

### Step 2 – Exploratory Visualization
- **Violin plot + jittered scatterplot** constructed:  
  - Showed GDP Growth distribution at different levels of economic freedom.  
  - Highlighted clustering of countries around mid-level freedom scores.  
  - Identified outliers (countries with unusually high/low growth).  
- Purpose: visually check for **linearity vs. non-linear/multimodal patterns**.

### Step 3 – Correlation Analysis
- Chose **Spearman’s rank correlation (ρ)** due to:  
  - Non-normal distributions.  
  - Absence of linearity but potential monotonic relationships.  
- Tested relationship between **Economic Freedom Score (2019)** and **GDP Growth Rate**.

### Step 4 – Multiple Regression Analysis
- Built regression model:  
  \[
  \text{GDP Growth Rate} = \beta_0 + \beta_1 (\text{2019 Score}) + \beta_2 (\text{Investment Freedom}) + \beta_3 (\text{Labor Freedom}) + \beta_4 (\text{Trade Freedom}) + \epsilon
  \]
- Checked **Variance Inflation Factor (VIF)** for multicollinearity.  
  - All VIF values < 5 → predictors were sufficiently independent.  
- Examined **residuals** for heteroskedasticity and model fit.  
- Visualized **Predicted vs. Actual GDP Growth** to evaluate predictive accuracy.  

### Step 5 – Model Evaluation
- Reported:  
  - Coefficients and their statistical significance.  
  - R² and Adjusted R² for explanatory power.  
  - F-statistic for overall model significance.  
- Interpreted coefficients both statistically (p-values) and economically (practical significance).  

---

## 📊 Results & Insights

### Normality & Initial Visualization
- Shapiro-Wilk results:  
  - `2019 Score`: W ≈ 0.96, p < 0.001 → non-normal.  
  - `GDP Growth Rate`: W ≈ 0.91, p < 0.001 → non-normal.  
- Violin plot revealed **multimodal distribution** of growth, with clusters at mid-range scores.  
- No strong linear pattern, supporting choice of non-parametric methods.  

### Spearman Correlation
- **ρ = 0.02, p = 0.76** → negligible monotonic relationship.  
- Suggests that overall freedom alone does not directly explain growth differences.  
- Interpretation: economic freedom may matter in **interaction with other variables** (institutions, demographics, capital flows), not as a standalone predictor.

### Multiple Regression Results
- **Overall Model Fit:**  
  - R² ≈ 0.06, Adj. R² ≈ 0.04 → explains ~6% of GDP growth variation.  
  - F-statistic: p < 0.05 → model is statistically significant overall.  

- **Key Predictors:**  
  - `2019 Economic Freedom Score`: positive and significant (β ≈ 0.116, p < 0.01).  
    - Interpretation: each 1-point increase in the index is linked to ~0.12% higher GDP growth.  
  - `Investment Freedom`: negative, weak significance (p ≈ 0.09).  
  - `Labor Freedom`: negative, not significant.  
  - `Trade Freedom`: negative, not significant.  

- **Multicollinearity:** VIF values < 5 → not a concern.  
- **Residuals:** wide dispersion in Predicted vs. Actual GDP Growth plot → limited predictive power.  

### Interpretation
- **Main takeaway:** Economic freedom matters, but its direct effect on GDP growth is **modest**.  
- Subcomponents (investment, labor, trade freedom) show **mixed or negative coefficients**, highlighting complexities:  
  - For example, liberalizing trade or labor markets may create short-term disruptions that do not immediately translate into growth.  
- The model’s low R² implies that **other macroeconomic variables** (inflation, political stability, human capital, technology) drive most of the variation in growth.  

### Policy Insights
- **Positive but modest link** between freedom and growth aligns with literature (Gwartney et al., Rode & Coll).  
- Policymakers should consider **which freedoms matter most**:  
  - Property rights and governance may be stronger drivers than labor/trade freedom.  
- Simple correlations overlook complexity — a **multifactor and possibly non-linear approach** is needed to fully capture the freedom–growth nexus.  
