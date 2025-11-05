# Credit Risk Prediction Challenge

This repository contains my solution to the credit risk prediction assignment. The goal is to identify customers at high risk of serious delinquency (90+ days past due) within the next 2 years using historical credit bureau data.

## 📁 Repository Structure

src/
└── credit_risk_prediction/
├── analysis.ipynb # Exploratory Data Analysis (EDA)
└── modeling.ipynb # Model Development & Evaluation

## 🔍 Exploratory Data Analysis (`analysis.ipynb`)

This notebook covers comprehensive preliminary analysis of the training dataset, including:
- **Data quality assessment**: Handling of missing values and outliers
- **Population profiling**: Distribution of key features (e.g., age, income, delinquency counts)
- **Target variable analysis**: Class imbalance and default rate characteristics
- **Feature relationships**: Correlation analysis and interaction exploration
- **Preprocessing decisions**: Justification for transformations (e.g., log-scaling skewed variables) tailored for linear models

## 🧠 Modeling Approach (`modeling.ipynb`)

I iterated through multiple modeling strategies to balance interpretability and performance:

1. **Baseline Logistic Regression**  
   - Handled missing `MonthlyIncome` via median imputation within risk groups  
   - Demonstrated limitations of linear approaches on this non-linear problem

2. **Rule-Based Point System**  
   - Created an interpretable, business-friendly scoring logic using domain knowledge  
   - Evaluated precision/recall trade-offs for operational feasibility

3. **Optimized LightGBM Model**  
   - Achieved significantly higher AUC and recall vs. baselines  
   - Performed feature importance analysis and threshold optimization  
   - Proposed an **economics-driven decision framework**:  
     - Approval threshold dynamically adjusted based on order size, margin (5%), and expected lifetime value  
     - Explicit expected value calculation to maximize profit while controlling risk

## 📝 Notes on Test Set Predictions

I did **not generate predictions on the unlabeled test set**, as this appears to be a third-party challenge dataset where ground truth labels are likely unavailable to candidates. If you’d like me to:
- Output predictions in your required format, or  
- Discuss deployment considerations (monitoring, recalibration, etc.)  

I’d be happy to extend this work accordingly.

## 💡 Key Takeaways

- **Interpretability matters**: Even with powerful models like LightGBM, business logic (e.g., "ban past defaulters") must anchor the strategy.
- **Economics > metrics**: Threshold selection should optimize profit, not just F1-score.
- **Iterative refinement**: Starting simple (logistic regression) builds intuition before advancing to complex models.