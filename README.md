# EU Health Insurance Premium Analysis

**Statistical Modeling and Market Efficiency Assessment**

## Project Overview

This project analyzes health insurance premium pricing patterns for EU/EFTA residents in Switzerland using advanced statistical modeling techniques. The analysis investigates regional pricing disparities, demographic factors, and coverage characteristics that influence premium costs, with implications for regulatory oversight and market efficiency.

## Research Questions

1. **Premium Determinants**: How do country/region of origin, age demographics, and deductible choices jointly influence health insurance premiums for EU/EFTA residents in Switzerland?

2. **Premium Classification**: Can insurance policies be accurately classified into high vs. low premium tiers based on demographic and coverage characteristics, enabling automated identification of potentially discriminatory pricing?

## Methodology

### Dataset
- **Source**: Swiss health insurance premium records for EU/EFTA residents
- **Size**: 2,230 observations after data cleaning
- **Variables**: Country of origin, age demographics, accident coverage, deductible levels, premium amounts
- **Time Period**: Cross-sectional data from Swiss insurance market

### Statistical Models

**1. Generalized Additive Model (GAM)**
- Simplified model with 6 regional groupings (Benelux, DACH, Southern Europe, Nordic, Eastern Europe, Other EU)
- Numeric age variable for linear age-effect modeling
- Interaction terms: Region × Age, Age × Accident Coverage
- Model complexity: ~15-20 parameters (reduced from 80+ for improved interpretability)
- Performance: R² ≈ 70-80%, explaining substantial premium variance

**2. Support Vector Machine (SVM)**
- Binary classification: High vs. Low premium tiers
- RBF kernel with optimized hyperparameters (cost=10, gamma=0.1)
- Feature engineering: Geographic risk factors, age scaling, coverage indicators
- Performance: ~75-80% accuracy, Kappa > 0.5

### Key Techniques
- **Log transformations** for premium amounts
- **Train/test split** (80/20) for model validation
- **Smoothers** (LOESS and GAM) for exploratory data analysis
- **Comprehensive coefficient interpretation** with exp() transformations

## Key Findings

### Regional Premium Disparities
- Significant premium variations across European regions (20-50% differentials)
- Regional groupings reveal systematic market inefficiencies
- Premium differences persist even after controlling for age and coverage characteristics

### Age-Based Pricing
- Premiums systematically increase with age categories
- Linear age effect captured efficiently through numeric modeling
- Regional differences in age-based pricing slopes (interaction effects)

### Policy Implications
- Models can serve as automated screening tools for regulatory oversight
- Regional premium differentials exceeding 20-30% warrant actuarial justification
- GAM coefficients provide transparent benchmark for "expected" premiums

## Project Structure

```
├── ArnoldOlympio_ML1_Assessment.Rmd     # Main analysis (R Markdown)
├── ArnoldOlympio_ML1_Assessment.html    # Rendered report
├── data/
│   └── Prämien_EU.csv                   # Insurance premium dataset
├── README.md                             # Project documentation
└── Complete ML1 Alternative Assessment Requirements.docx  # Assessment guidelines
```

## Technical Requirements

### Software Dependencies
- **R** (version 4.0+)
- **R Packages**:
  - `tidyverse` - Data manipulation and visualization
  - `mgcv` - Generalized Additive Models
  - `e1071` - Support Vector Machines
  - `caret` - Model training and evaluation
  - `ggplot2` - Statistical graphics
  - `knitr` - Dynamic report generation

### Installation
```r
install.packages(c("tidyverse", "mgcv", "e1071", "caret", "ggplot2", "knitr"))
```

## Reproducing the Analysis

1. **Clone the repository**:
   ```bash
   git clone https://github.com/arnoldolympio/ml1-insurance-analysis.git
   cd ml1-insurance-analysis
   ```

2. **Open R/RStudio** and set working directory:
   ```r
   setwd("path/to/ml1-insurance-analysis")
   ```

3. **Knit the R Markdown document**:
   ```r
   rmarkdown::render("ArnoldOlympio_ML1_Assessment.Rmd")
   ```

4. **View the output**: Open `ArnoldOlympio_ML1_Assessment.html` in a web browser

## Results Summary

### Model Performance
- **GAM Model**: 70-80% variance explained, interpretable coefficients with clear practical meaning
- **SVM Model**: 75-80% classification accuracy, high sensitivity for detecting high-premium policies
- **Complementary Strengths**: GAM provides explanatory depth ("why"), SVM provides predictive power ("what")

### Academic Contribution
This analysis demonstrates:
- Effective model simplification techniques (80+ parameters → 15-20) without sacrificing explanatory power
- Practical application of statistical learning to insurance market regulation
- Transparent methodology for identifying potential pricing discrimination

## Limitations

- **Cross-sectional data**: Prevents causal inference about temporal premium evolution
- **Unobserved factors**: Regional effects may reflect regulatory environments, health system structures, or actuarial risk differences not captured in available variables
- **Sample scope**: Limited to EU/EFTA residents in Switzerland; generalizability to other markets unclear
- **Temporal dynamics**: Premium changes over time not analyzed

## Future Research Directions

1. **Longitudinal analysis**: Incorporate temporal premium changes to strengthen causal claims
2. **Enhanced risk adjustment**: Add health status indicators, claims history, and insurer-specific variables
3. **Market expansion**: Compare multiple insurance providers across full Swiss market
4. **Causal inference**: Apply quasi-experimental methods to identify causal effects of policy changes

## Author

**Arnold Olympio**

Alternative Assessment for Machine Learning 1 Course
Master's Program
2024-2025 Academic Year

## License

This project is an academic assessment submitted for course evaluation. The dataset is proprietary and provided for educational purposes. Code and analysis methodology are available for academic review and educational use.

## Acknowledgments

This analysis was completed as an alternative assessment for the ML1 course, demonstrating proficiency in:
- Generalized Additive Models (GAM)
- Support Vector Machines (SVM)
- Statistical inference and coefficient interpretation
- Data visualization with smoothers
- Reproducible research with R Markdown

---

**Note**: This repository contains the complete analysis, source code, and documentation for academic evaluation purposes. For questions or collaboration inquiries, please open an issue in this repository.
