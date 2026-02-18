# ChessRank: Bayesian Skill Estimation

A Python-based implementation of the TrueSkill ranking system to model player proficiency and predict match outcomes. This project moves beyond frequentist win-rate metrics to implement a Bayesian inference engine that accounts for both skill $(\mu)$ and uncertainty $(\sigma)$.

## Overview
Standard Elo ratings struggle with low sample sizes and lack a formal measure of confidence. This engine implements the TrueSkill algorithm to derive a "Conservative Rating" ($R = \mu - 3\sigma$), ensuring rankings are statistically grounded. 

The system was validated against a dataset of **20,000+ matches**, demonstrating a significant predictive lift over traditional methods.

## Technical Implementation
- **Bayesian Modeling:** Utilized the `trueskill` library to maintain Gaussian distributions for 1,600+ unique players.
- **Predictive Validation:** Conducted an 80/20 train-test split on chronological match data to evaluate the model's forecasting ability.
- **Statistical Analysis:** Used `scipy.stats` to calculate Pearson and Spearman correlations between TrueSkill ratings and actual score rates.
- **Data Pipeline:** Preprocessed raw match telemetry using `pandas` to handle three-way outcomes (Win/Loss/Draw).

## Results & Performance
- **Prediction Accuracy:** Achieved **64.4% accuracy** in forecasting match outcomes, an **11.5% improvement** over the baseline win-rate model (52.9%).
- **Uncertainty Convergence:** Statistical profiling confirmed a negative correlation ($r = -0.353$) between games played and uncertainty ($\sigma$), proving the model correctly gains confidence as data density increases.
- **Top Tier Identification:** Identified top 20 players by conservative rating, filtering for statistical significance to ensure high-rank stability.



## Setup & Usage
1. **Clone:** `git clone https://github.com/sabhal35/ChessRank-Bayesian-Skill-Estimation.git`
2. **Environment:** `pip install trueskill pandas seaborn scipy`
3. **Execution:** Run `179project.ipynb` to regenerate the ranking engine and visualization suite.
