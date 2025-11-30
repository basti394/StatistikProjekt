# Comparative Analysis of Economic Structures: China vs. The West

## Project Overview
This project performs a statistical deep dive into the **IMF World Economic Outlook** dataset to analyze the structural economic differences between **China** and major Western economies (**Switzerland, Germany, USA**).

We move beyond simple visualizations to test economic theories (Okun's Law, Phillips Curve) and validate findings using rigorous hypothesis testing (Kruskal-Wallis, Spearman Correlation, Chi-Square, and t-Tests).

## Repository Structure
The analysis is divided into four sequential notebooks. Please run them in the following order to ensure data dependencies are met.

| Order | Notebook | Description |
| :--- | :--- | :--- |
| **01** | `01_Data_Preparation_and_EDA.ipynb` | **Start Here.** Loads raw IMF data, cleans/reshapes it into a usable format, performs initial Exploratory Data Analysis (EDA), and saves the clean dataset (`imf_data_clean.pkl`). |
| **02** | `02_Analysis_Structural_Differences.ipynb` | **Univariate Analysis.** Focuses on GDP Growth. Uses Kruskal-Wallis and Dunn's Post-hoc tests to statistically prove that China forms a distinct economic cluster compared to the West. |
| **03** | `03_Analysis_Market_Mechanisms.ipynb` | **Bivariate Analysis.** Tests traditional economic theories. Analyzes the Phillips Curve (Inflation vs. Unemployment) and Okun's Law (GDP vs. Unemployment) using Spearman correlation with FDR correction. |
| **04** | `04_Deep_Dive_Stability_and_Rivalry.ipynb` | **Synthesis & Deep Dive.** Validates findings regarding stability risks (Chi-Square test on volatility) and directly compares inflation pressures between the two superpowers, USA and China (t-Test). |

## Key Findings

### 1. The "China Model" is Structurally Unique
* **Growth:** China exhibits significantly higher GDP growth rates (Median ~8.9%) compared to Western economies (~1.7% - 2.7%).
* **Variance:** While growth is higher, it is also more volatile (wider Confidence Intervals), representing a "High Risk / High Reward" regime.
* **Statistical Proof:** The Kruskal-Wallis test ($H \approx 100$, $p \approx 0$) confirms China's growth distribution is statistically distinct from the CH/DE/US cluster.

### 2. Economic Theories have Limits
* **Phillips Curve:** Holds true for **Switzerland** and **China** (significant negative correlation between inflation and unemployment), but **failed** for Germany and the USA in this dataset.
* **Okun's Law:** We observed a **decoupling** of GDP growth and unemployment across all four nations ($p_{adj} > 0.05$), suggesting growth does not automatically guarantee lower unemployment in modern structural contexts.

### 3. Superpower Stability
* **Volatility:** China experiences "Extreme Growth" years ($>8\%$) significantly more frequently than stable economies like Switzerland (confirmed via Chi-Square).
* **Inflation Parity:** Despite systemic differences, there is **no significant difference** in mean inflation rates between the USA and China, suggesting both are subject to similar global inflationary cycles.

## Methodology & Tech Stack
* **Language:** Python 3
* **Libraries:** `pandas`, `numpy`, `scipy.stats`, `seaborn`, `matplotlib`, `statsmodels`, `scikit_posthocs`
* **Statistical Methods:** * Shapiro-Wilk (Normality check)
    * Spearman Rank Correlation (Robust to outliers)
    * Benjamini-Hochberg FDR (Multiple testing correction)
    * Kruskal-Wallis H-Test & Dunn's Test (Non-parametric ANOVA)
    * Welch's t-Test (Comparing means with unequal variance)

## Usage
1.  Ensure `data.csv` (raw IMF data) is in the root directory.
2.  Install dependencies: `pip install pandas numpy scipy seaborn matplotlib statsmodels scikit-posthocs`
3.  Run `01_Data_Preparation_and_EDA.ipynb` first to generate the pickle file.
4.  Run notebooks 02, 03, and 04 in any order thereafter.