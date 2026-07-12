# What Drives the Price of a Used Car?

**UC Berkeley Professional Certificate in Machine Learning and Artificial Intelligence**
Module 11 — Practical Application II

[View the full notebook on GitHub](https://github.com/jtie/Module11_Assignment11_1)

---

## Overview

This project applies the CRISP-DM framework to a dataset of approximately 426,000 used car listings sourced from Kaggle. The goal is to identify which vehicle attributes most strongly influence price, and to deliver actionable inventory recommendations to used car dealerships.

---

## Summary of Findings

### Model Results

A Ridge Regression model was selected as the best-performing model after comparing three approaches:

| Model | RMSE (USD) | R-squared |
|---|---|---|
| Linear Regression | baseline | baseline |
| **Ridge Regression** | **best** | **best** |
| Lasso Regression | comparable | comparable |

Ridge regression outperformed plain linear regression due to its L2 regularization, which handles the large number of one-hot encoded features more effectively. Lasso provided useful feature selection, confirming which features Ridge identified as important.

---

### Key Price Drivers

**Attributes that decrease price:**

| Attribute | Estimated Price Impact |
|---|---|
| Parts-only title | -73% vs clean title |
| Missing title | -57% vs clean title |
| Salvage title | -37% vs clean title |
| 3-cylinder engine | -53% vs 8-cylinder |
| Gas fuel type (vs diesel) | -50% vs diesel |
| Each additional ~8 years of age | -31% |
| Each additional ~100,000 miles | -24% |

**Attributes that increase price:**

| Attribute | Estimated Price Premium |
|---|---|
| Brand: Porsche | +67% vs reference brand |
| Brand: Tesla | +52% vs reference brand |
| Type: Off-Road | +42% vs sedan |
| Type: Convertible | +25% vs sedan |
| Engine: 12-cylinder | +24% vs 8-cylinder |
| Type: Pickup | +22% vs sedan |
| Brand: Lexus | +20% vs reference brand |
| Transmission: Manual | +15% vs automatic |

---

### Recommendations for Used Car Dealers

1. **Always prioritize clean-title vehicles.** Title issues are the single largest controllable price killer — a parts-only or salvage title can reduce resale value by 37–73%.

2. **Favor newer, lower-mileage inventory.** Every ~8 additional years of age reduces price by approximately 31%; every ~100,000 additional miles reduces price by approximately 24%.

3. **Stock off-road vehicles, pickups, and convertibles.** These vehicle types consistently command 22–42% premiums over standard sedans.

4. **Luxury brands hold value.** Porsche, Tesla, and Lexus command significant premiums. Acquiring these at the right price offers strong resale upside.

5. **Manual transmission is a niche premium.** Manual transmission vehicles command approximately 15% more than automatics, likely driven by enthusiast demand.

---

### Limitations

- The model is linear and does not capture interaction effects (e.g., brand x age combinations)
- Vehicle condition data was missing for ~41% of rows and was imputed with the mode
- Prices reflect listing prices, not final sale prices
- Fuel type results (gas/electric negative vs diesel) may reflect dataset composition rather than universal market trends

---

## Project Structure

```
Module11_Assignment11_1/
├── data/
│   └── vehicles.csv          # 426K used car listings from Kaggle
├── images/
│   └── crisp.png             # CRISP-DM framework diagram
├── prompt_II.ipynb           # Full analysis notebook (CRISP-DM walkthrough)
└── README.md                 # This file
```

## Notebook Sections

The notebook follows the full CRISP-DM process:

1. **Business Understanding** — Reframe the dealer's question as a supervised regression problem
2. **Data Understanding** — Explore 18 features across 426K listings; identify missingness and outliers
3. **Data Preparation** — Clean outliers, impute missing values, engineer features, encode categoricals, scale numerics
4. **Modeling** — Train and cross-validate Linear Regression, Ridge, and Lasso models
5. **Evaluation** — Assess model quality via residual analysis and interpret price drivers
6. **Deployment** — Deliver business-ready findings and inventory recommendations

---

[View the full notebook on GitHub](https://github.com/jtie/Module11_Assignment11_1)
