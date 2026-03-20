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

<img src="output/figures/Smoke exposure grouped by Area.png" width="350">

### Interpretation
From the boxplot, urban areas show higher median tobacco exposure and greater upper tail dispersion compared to rural areas, suggesting higher average exposure along with more extreme outliers. 

However, while urban areas show higher exposure than rural areas descriptively, this finding loses significance in the multivariate regression done later in the project. This indicates that the urban-rural gap is due to other compositional factors included but not limited to education and enforcement across areas rather than urbanisation itself. 

### RQ2: Education Vs Support for Ban
Is anti-tobacco education associated with support for smoking bans?

<img src="output/figures/Anti-tobacco Edu vs Ban Support.png" width="450">

### Interpretation
The relationship between anti-tobacco school education and support for banning tobacco is positive (correlation = 0.32) in both rural and urban areas. However, the slope coefficient of the regression is higher for rural areas than urban areas, suggesting that education may more strongly translate into pro-ban support for tobacco in rural areas. 

However, the fitted regression line only suggests correlation and no causaul inference due to "omitted variable bias and reverse causality". 

### RQ3: 
Does policy enforcement (COTPA) correlate with reduced exposure?¶

<img src="output/figures/Smoke exposure vs Enforcement.png" width="450">

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
**Variable selection for the regression**
The selected variables of the regression give an R² of 0.48 exlaining about 48% of the total variation in the data. The variable "% of health warnings on tobacco" (correlation with "% taught about harmful affects" = 0.78) is not included in the model due to multicollinearity. Although it inflates the R² of the model to 0.68, it renders all other included variables statistically insignificant and causes the problem of a single dominant predictor crowding out other predictors. 

Hence, the final model includes the predictors "region" dummy, "% taught about harmful effects", "% of COTPA enforcement" and "urban-rural" dummy, all lower-correlated variables that each play a distinct role in the analysis.

<img src="output/figures/Regression Output.png" width="450">

### Interpretation:

The OLS regression analysis (R² = 0.48 and F-statistic p<0.001) identifies "Regional Location" as the strongest predictor of tobacco exposure.

1. North-eastern states are associated with 22.44 pp higher exposure than the rest of India (reference category), controlling for all other factors - the single most statistically significant perdictor of this analysis. Northern states show 7.96pp lower exposure (p=0.066) than the rest of India. 
2. Anti-tobacco education shows a positive association with exposure (coeff=0.22, p=0.190), this is probably because of "Reverse Causality" i.e high exposure states respond with more education, rather than education reducing exposure. 
3. The COTPA enforcement has a statistically insignificant relationship with smoke exposure (p=0.767), this is probably because enforcement is more reactive than preventive.
4. The urban-rural dummy variable loses its significance (p=0.403), when controlled for other variables; this suggests that the urban-rural gap in smoke exposure comes from other hidden factors rather than urbanisation istelf. 

### SUMMARY 
This analysis examined state-level patterns in youth tobacco smoke exposure across India using the Global Youth Tobacco Survey (2019). Across four research questions and a multivariate OLS regression, regional location classification emerged as the only statistically significant predictor of exposure (p<0.001), with north-eastern states on average having 22.4pp higher exposure than other states of India after controlling for education, enforcement and urbanisation. The factors underlying this association, whether cultural, behavioural or environmental, cannot be determined from our current cross-sectional data alone and require further investigation. COTPA enforcement and anti-tobacco education both show counterintuitive positive associations with exposure, consistent with being reactive rather than preventive policy implementations. The urban-rural gap observed descriptively loses significance once other factors are controlled for.

### POLICY IMPLICATIONS
1. **Geographic targetting of interventions** - North eastern states show 22.4pp higher exposure than national baselines, even after controlling for education and enforcement. Thus anti-tobacco campaigns and budgets should prioritise this region, with interventions tailored to the cultural and climatic differences in this region, rather than using a uniform policy framework.
2. **Shift enforcement from reactive to preventive** - Enforcement is currently only penalising violations, but policy should shift towards youth-based preventing measures like smoke-free zones in public places and proactive monitoring by concerned authorities.
3. **Eliminating reverse causality in education** - Anti-tobacco education is positively associated with exposure i.e level of exposure determines education. But education should not just be focused on high exposure areas and should also cover lower exposure areas to prevent exposure levels from rising in the future.
4. **Adapting variations of baseline frameworks** - Northern states(−7.96pp, p=0.066) show lower exposure than national baseline. Hence, policies implemented in these regions can be studied to understand why they work better here than the rest of te country after controlling for all other cultural, social and bahavioural factors. Once understood, variations of these policies could be enforced in the other regions to ensure higher effectiveness and adaptability. 

### LIMITATIONS
1. This analysis is based on a cross-sectional dataset and hence associations between the variables cannot be interpreted as causal relationships. 
2. "Omitted Variable Bias" is a concern as variables such as peer pressure, social preferences, parental behaviour, income etc. are not available in the data, likely explaining the remaining variance (R² = 0.48) of the dataset. 
3. The regional classification - North, North-east, Rest of India is a simplified grouping based on zonal councils and treats all states within a group as homogenous. In reality, there is substantial within-group variation with individual exposures overlapping across regions. Also, the Rest of India group is a heterogenous category, combining Southern, Central and Western states which may have different exposure patterns that this analysis does not reflect. 

### FUTURE RESEARCH
There is potential to develop this project by 2 extensions which would substantially strengthen the findings of this analysis. 
1. **Difference-in-Differences (DiD) design** by introducing stricter enforcement in cold states as a treatment group and comparing exposure trends against a control group would allow causal identification of enforcement effectiveness in high-risk regions. 
2. **Time series analysis** using multiple yearly datasets of the GYTS survey would allow examination of whether youth tobacco exposure has increased or decreased over time and whether policy changes explain these trends. 

### CODES
The analysis is fully reproducible using the following Python notebook:

- [`EDA.ipynb`](https://github.com/abhinayaa-econ/India-Smoke-Exposure-EDA-Regression/blob/main/code/EDA.ipynb) – Exploratory data analysis, regression analysis and visualisations.
  
### AUTHOR
Abhinayaa Kumar Subramanian
MSc in Applied Economics
National UNiversity of Singapore
