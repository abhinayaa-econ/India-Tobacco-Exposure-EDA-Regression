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

<img src="output/figures/Smoke exposure grouped by Area" width="450">

### Interpretation
From the boxplot, urban areas show higher median tobacco exposure and greater upper tail dispersion compared to rural areas, suggesting higher average exposure along with more extreme outliers. 

However, while urban areas show higher exposure than rural areas descriptively, this finding loses significance in the multivariate regression done later in the project. This indicates that the urban-rural gap is due to other compositional factors included but not limited to education and enforcement across areas rather than urbanisation itself. 

### RQ2: Education Vs Support for Ban
Is anti-tobacco education associated with support for smoking bans?

<img src="output/figures/Anti-tobacco Edu vs Ban Support" width="450">

### Interpretation
The relationship between anti-tobacco school education and support for banning tobacco is positive (correlation = 0.32) in both rural and urban areas. However, the slope coefficient of the regression is higher for rural areas than urban areas, suggesting that education may more strongly translate into pro-ban support for tobacco in rural areas. 

However, the fitted regression line only suggests correlation and no causaul inference due to "omitted variable bias and reverse causality". 

### RQ3: 
Does policy enforcement (COTPA) correlate with reduced exposure?¶

<img src="output/figures/Smoke exposure vs Enforcement" width="450">

### Interpretation
It is evident that smoke exposure is "higher" in high enforcement areas(42.71%) than in low enforcement areas (34.99%). This is counterintuitive as in enforcement policies are more reactive than preventive, as seen from the positive slope of the regression plot between the variables. 

This is further reinforced from the regression analysis done later where the COTPA enforcement variable is statistically insignificant (p= 0.127) once other factors are controlled for. 

### RQ4:
Are geographic locations associated with different levels of smoke exposure?

<img src="output/figures/Smoke exposure & Geographical Location.png" width="450">

### Interpretation
On average, north-eastern states show higher smoke exposure(57.1%), than northern states(34.4%) and rest of India (32.5%) - more than 20.4pp above the national mean of 36.7%. 

Statistically, for the north-eastern states, the distribution is skewed upwards with several states clustering between 50-75% range and there is higher within-group variation. However, in northern states, there seems to be greater within-group consistency with state-level observations clustering between 10-30%. The other states behave very close to the national mean of 32.5% but is the most dispersed among the 3 groups. 

However, there is considerable overlap in individual state exposures across the categories. Therefore, group-level averages should not be interpreted deterministically - regression analysis provodes a more robust test to see if region is a statistically significant predictor of smoke exposure.

### CORRELATION ANALYSIS

<img src="output/figures/Correlation Heatmap.png" width="350">

### DESCRIPTION TO MODELLING
The descriptive statistics identify 4 important predictors - Education, Enforcement, Cold/Non-cold States and Urban/Rural areas of states. The following regression analysis aims to study the isolated associations of these predictors with tobacco smoke exposure, controlling for any confounding between them.

### REGRESSION ANALYSIS












