# Youth Tobacco Smoke Exposure Across India
## Exploratory & Regressional Data Analysis using Python

## Overview
This notebook explores the state-level patterns in youth exposure to tobacco and examines how education, geographical location, awareness and policy enforcement affect exposure outcomes. The target group is school-going youth below the age of 18.

## Data
- **Unit of analysis:** Indian states
- **Nature:** Cross-sectional, state-level aggregated data
- **Dependent variable:** Tobacco smoke exposure (%) among youth

> Raw data files are not uploaded due to licensing restrictions.
> Variable construction and cleaning logic are documented in the notebook.

## Research Questions:
1. Are urban students more exposed to second-hand smoke than rural students?
2. Is anti-tobacco education associated with support for smoking bans?
3. Does policy enforcement (COTPA - Cigarettes & Other Tobacco Products Act) correlate with reduced exposure?
4. Is geographical location associated with different levels of smoke exposure?

## Methodology
- Regional grouping and comparative distributional analysis
- Bar charts with overlaid state-level dot plots to capture within-group variation
- Reference line benchmarking against national mean
- Assessment of within-group vs. between-group variance to evaluate the robustness of predictors

## Key Findings

### RQ1: Urban Vs Rural Exposure
Do urban students experience higher tobacco smoke exposure than rural students?

<img src="output/figures/Smoke exposure & Geographical Location.png" width="550">

### Interpretation
From the boxplot, urban areas show higher median tobacco exposure and greater upper tail dispersion compared to rural areas, suggesting higher average exposure along with more extreme outliers. 

However, while urban areas show higher exposure than rural areas descriptively, this finding loses significance in the multivariate regression done later in the project. This indicates that the urban-rural gap is due to other compositional factors included but not limited to education and enforcement across areas rather than urbanisation itself. 



















