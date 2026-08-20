# Disney Live-Action Diversity Casting: Audience Perception Analysis

## Overview

Disney's live-action remakes have introduced more diverse casting choices — but how do audiences actually respond? This project investigates how character skin color in Disney live-action films affects audience **cognitive dissonance** and **watching willingness**, using a between-subjects survey experiment (n=551).

The study finds that diversity casting (Black skin condition) significantly increases cognitive dissonance, which in turn reduces watching willingness. Importantly, this effect is **fully mediated** by cognitive dissonance — skin condition alone does not directly suppress willingness to watch.

## Research Questions & Hypotheses

| # | Hypothesis | Result |
|---|-----------|--------|
| H1 | Skin condition affects cognitive dissonance | ✅ Supported (ANOVA F=22.92, p<0.001) |
| H2 | Skin condition affects watching willingness | ✅ Supported (ANOVA F=3.48, p=0.03) |
| H3 | Cognitive dissonance negatively predicts watching willingness | ✅ Supported (β=-0.488, R²=0.223) |
| H4 | Cognitive dissonance mediates skin condition → watching willingness | ✅ Partially supported (full mediation for White condition only) |

## Experimental Design

- **Design**: Between-subjects with 3 conditions (White / Yellow / Black character skin color)
- **Sample**: 551 respondents, predominantly Taiwanese college students
- **Instrument**: Likert-scale survey measuring attitudes toward diversity casting, cognitive dissonance, and behavioral intentions (watching/spending willingness)

## Methodology

### 1. Data Cleaning (`01_Data_Cleaning.ipynb`)
- Merged three separate condition-level Excel files (White, Yellow, Black) into a unified dataset
- Standardized column names across conditions with different survey branch structures
- Encoded binary variables, converted data types, and removed incomplete responses

### 2. Statistical Analysis (`02_reliability_anova_regression.ipynb`)
- **Reliability Analysis**: Cronbach's α to validate composite constructs
  - Cognitive dissonance (2 items): α = 0.626
  - Watching willingness (4 items): α = 0.894
- **One-Way ANOVA** with Levene's test for homogeneity of variance
- **Tukey HSD** post-hoc pairwise comparisons
- **Multiple Linear Regression** (OLS) — 3-model progression testing direct and combined effects
- **Mediation Analysis** using `pingouin` — testing whether cognitive dissonance mediates the skin condition → willingness path

## Key Findings

### Cognitive Dissonance Differs Across Groups
All three pairwise comparisons are significant (Tukey HSD). The Black condition group reports the highest cognitive dissonance, followed by Yellow, then White.

| Comparison | Mean Diff | p-value | Significant |
|-----------|-----------|---------|-------------|
| Black vs White | 0.642 | <0.001 | Yes |
| Black vs Yellow | 0.380 | <0.001 | Yes |
| Yellow vs White | 0.262 | 0.012 | Yes |

### Watching Willingness: Only One Pair Differs
Only the Black vs White comparison reaches significance. Yellow does not differ from either group.

| Comparison | Mean Diff | p-value | Significant |
|-----------|-----------|---------|-------------|
| Black vs White | -0.260 | 0.028 | Yes |
| Black vs Yellow | -0.094 | 0.637 | No |
| Yellow vs White | 0.166 | 0.204 | No |

### Mediation: Cognitive Dissonance Explains the Effect
For the White condition, cognitive dissonance **fully mediates** the relationship between skin condition and watching willingness:
- Indirect effect = 0.214 (significant)
- Direct effect = -0.004 (not significant)

No mediation effect is found for the Yellow condition.

## Repository Structure

```
├── 01_Data_Cleaning.ipynb        # Data merging, standardization, and cleaning
├── 02_reliability_anova_regression.ipynb  # Full statistical analysis pipeline
└── README.md
```

> **Note**: Raw survey data is not included in this repository to protect respondent privacy.

## Tools & Libraries

Python · pandas · NumPy · SciPy · statsmodels · pingouin · Matplotlib
