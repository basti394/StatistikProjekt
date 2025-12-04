# Comparative Analysis of Economic Structures: China vs. The West

## Project Overview
This project performs a statistical deep dive into the **IMF World Economic Outlook** dataset to analyze the structural economic differences between **China** and major Western economies (**Switzerland, Germany, USA**).

We move beyond simple visualizations to test economic theories (Okun's Law, Phillips Curve) and validate findings using rigorous hypothesis testing (Kruskal-Wallis, Chi-Square, t-Tests) and **Linear Regression models**.

## Repository Structure
The analysis is divided into five sequential notebooks. Please run them in the following order to ensure data dependencies are met.

| Order | Notebook | Description |
| :--- | :--- | :--- |
| **01** | `01_Data_Preparation_and_EDA.ipynb` | **Start Here.** Loads raw IMF data, cleans/reshapes it, performs initial Exploratory Data Analysis (EDA), and saves the clean dataset (`imf_data_clean.pkl`). |
| **02** | `02_Analysis_Structural_Differences.ipynb` | **Univariate Analysis.** Focuses on GDP Growth. Uses Kruskal-Wallis and Dunn's Post-hoc tests to statistically prove that China forms a distinct economic cluster compared to the West. |
| **03** | `03_Analysis_Market_Mechanisms.ipynb` | **Bivariate Analysis.** Tests traditional economic theories using robust correlation (Spearman). Identifies where theories like the Phillips Curve hold or fail. |
| **04** | `04_Deep_Dive_Stability_and_Rivalry.ipynb` | **Hypothesis Testing.** Deep dive into stability risks (Chi-Square test on volatility) and a direct inflation comparison between the USA and China (t-Test). |
| **05** | `05_Regression_Analysis.ipynb` | **Modelling & Trends.** Uses OLS Regression to quantify trade-offs (Phillips Curve coefficient) and test long-term growth deceleration trends in China. Includes model diagnostics. |

## Key Findings

### 1. The "China Model": High Growth, High Risk, but Slowing Down
* **Structure:** China exhibits significantly higher growth rates (Median ~8.9%) but also higher volatility ("Boom/Bust" frequency) compared to Western economies.
* **Trend Analysis:** Regression confirms that China is not growing linearly. We detected a statistically significant **structural deceleration** of approx. **-0.10 percentage points per year**, supporting the "economic maturation" theory.

### 2. Economic Mechanisms: Quantifying the Trade-offs
* **Phillips Curve:** While the US and Germany show no clear pattern, **Switzerland** follows classic economic rules. Our model quantifies a significant trade-off: A **1% increase in unemployment** lowers inflation by approx. **0.87 percentage points** ($R^2 \approx 39\%$).
* **Okun's Law:** We observed a **decoupling** of GDP growth and unemployment across all four nations, suggesting that growth alone does not guarantee job creation in the modern era.

### 3. Superpower Convergence
* **Inflation Parity:** Despite vast political differences, there is **no significant difference** in mean inflation rates between the USA and China ($p > 0.05$), suggesting both are driven by similar global macroeconomic cycles.

## Methodology & Tech Stack
* **Language:** Python 3
* **Libraries:** `pandas`, `numpy`, `scipy.stats`, `seaborn`, `matplotlib`, `statsmodels`, `scikit_posthocs`
* **Statistical Methods:**
    * **Descriptive & Robust Diagnostics:** Mean, Median, IQR, Boxplots (VL 2A, VL 3).
    * **Correlation Analysis:** Spearman Rank Correlation (Non-linear/Robust) (VL 4).
    * **Group Comparisons:** Kruskal-Wallis H-Test & Dunn's Post-hoc Test (VL 9).
    * **Hypothesis Testing:** Welch's t-Test & Chi-Square Test of Independence (VL 7, VL 8).
    * **Regression Analysis:** Ordinary Least Squares (OLS), t-Test on Coefficients, Model Diagnostics (Shapiro-Wilk for residuals) (VL 10).
    * **Significance Correction:** Benjamini-Hochberg FDR for multiple testing (VL 8).

## Usage
1.  Ensure `data.csv` (raw IMF data) is in the root directory.
2.  Install dependencies: `pip install pandas numpy scipy seaborn matplotlib statsmodels scikit-posthocs`
3.  Run `01_Data_Preparation_and_EDA.ipynb` first to generate the pickle file.
4.  Run notebooks 02 through 05 in order.