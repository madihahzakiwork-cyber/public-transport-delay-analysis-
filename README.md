# public-transport-delay-analysis-

## Overview
This analysis explores factors influencing public transport delays using a dataset of ~2,000 trips across bus, metro, train, and tram services in January. Key drivers of delay were identified through exploratory analysis and a Random Forest classifier, with hour of day and weekday emerging as the strongest predictors of delay likelihood. While the model achieved 73.75% accuracy, class imbalance limited its ability to correctly identify non-delayed trips, highlighting an area for further refinement.

## Dataset
This project uses the [Public Transport Delay dataset](https://www.kaggle.com/datasets/khushikyad001/public-transport-delays-with-weather-and-events) from Kaggle. Due to file size/licensing, the raw dataset is not included in this repository. 
You can download it directly from Kaggle and place it in the `data/` folder to reproduce this analysis. 

This dataset has 2000 rows and 32 columns, it contains delay frequency for public transports in January 2023. It was
synthetically generated and does not reflect real-world data.

## Key Findings
1. Delay rates peak at 08:00, particularly for train services, likely reflecting morning rush-hour commuter traffic as passengers travel to work.
2. A second peak occurs around 19:00, again most pronounced for trains, consistent with the evening commute as passengers return home from work.
3. On weekends, bus usage appears to dominate over other transport types, suggesting a shift in travel behaviour away from commuter-focused modes like trains.
4. Overall delay rates are higher on weekends than on weekdays, despite lower reliance on train travel — indicating that weekend delays may be driven by factors other than commuter volume (e.g., reduced service frequency, maintenance schedules, or leisure-driven congestion).
5. The importance of each variable to delay was calculated using the feature RandomForestClassifier. The Random Forest model achieved an overall accuracy of 73.8%. However, performance was highly imbalanced across classes: the model correctly identified 99% of actual delayed trips (recall = 0.99) but only 4% of actual non-delayed trips (recall = 0.04), indicating a strong bias toward predicting "delayed" regardless of input features. This suggests the headline accuracy figure overstates the model's true predictive power, and that class imbalance in the dataset (294 delayed vs. 106 non-delayed cases in the test set) is likely driving this behaviour.
<img width="3143" height="1650" alt="heatmap_hour" src="https://github.com/user-attachments/assets/939e5308-8261-4272-8a1b-f74804711581" />
<img width="3194" height="1651" alt="heatmap_weekday" src="https://github.com/user-attachments/assets/fcbfc034-9ffa-4738-908a-5589418aae16" />
<img width="3168" height="1650" alt="heatmap_weekend" src="https://github.com/user-attachments/assets/a0293a7f-8a41-4e7f-9365-4878c5a6e711" />



## Limitations & Future Work
1. The dataset covers only January, limiting seasonal generalisability.
2. Class imbalance (75% delayed vs 25% not delayed) affected model performance; 
  addressing this via class weighting or resampling (e.g., SMOTE) would likely improve results.
3. Temperature's relationship with delay appears non-linear; future analysis could 
  explore polynomial features or non-linear models to better capture this.
4. With a longer time span of data, next-day/lag effects (e.g., snow melting) could 
  be tested more robustly with larger sample sizes.

## Tools Used
Python, pandas, seaborn, scikit-learn, matplotlib

## How to Run
[Brief instructions, e.g., pip install -r requirements.txt, then open notebook]
