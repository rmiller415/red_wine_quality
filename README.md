# red_wine_quality  
## Overview  

**Objectives:** To predict the quality rating of a sampling of red wines.  
**The Dataset:** The dataset comes from the [Kaggle Red Wine Quality Dataset](https://www.kaggle.com/datasets/uciml/red-wine-quality-cortez-et-al-2009). This dataset is the [Wine Quality Dataset](https://archive.ics.uci.edu/dataset/186/wine+quality) from the UC Irvine's Machine Learning Repository and posted on Kaggle by [UCI Machine Learning](https://www.kaggle.com/organizations/uciml). The data come from the paper [Modeling wine preferences by data mining from physiochemical properties](https://www.semanticscholar.org/paper/Modeling-wine-preferences-by-data-mining-from-Cortez-Cerdeira/bf15a0ccc14ac1deb5cea570c870389c16be019c) by Cortez, Cerdeira, et. al.  

## Tools Used:  
Python was used as the primary coding language.  
**Visualization:** Matplotlib and Seaborn
**Data Storage/Structures:** Pandas and NumPy  
**Data Transformation and Feature Selection:** sklearn, 
**Models:** sklearn (LinearRegression, RandomForestRegressor, SVM), lightgbm, xgboost, pytorch ([tabnet](https://arxiv.org/abs/1908.07442) based architecture)  

## Methods:  
**Data Visualization:** I plotted the features with kernel density plots, violin plots, and heatmaps of the correlation coefficients.  
**Exploratory Data Analysis:** Using my understanding of chemistry and biophysics, I realized that there was a significant amount of data leakage amongst the features. I used a linear regressor and iterated through pairs of features to find high correlation (for example pH, volatile acidity, and fixed acidity). Then I grouped the leakage pairs into categories by placing them into a matrix and minimizing it. Finally, I made several sets of features to test.  
**Feature Selection:** I took the feature sets and used XGBoost and lightGBM models to find the best feature set by evaluating their r2_score, mean absolute percentage error, and mean squared error.  
**Model Selection:** Once I found the best feature set, I tried several models to find the best model. Since I had already used gradient boosting models to select the features, I already knew their predictive power. I tried using a SVM and a Bayesian Ridge Regressor model to see if they worked well. I also read about a neural network architecture called tabnet that performed well on tabular data. So I tried the tabnet architecture.  

## Results:  

The best model was the Bayesian Ridge Regressor, which is one of the simplest models to implement and required the least computational time.

The model was only able to get a mean squared error of around 0.4 to 0.41. The data is subject to human tastes because the ratings were done by human judges. Each judge could have a wildly different view of what makes a good wine, and it could easily vary from person to person, time to time, and other factors. I looked at several other notebooks on the same data and saw the same results. Many of the best-performing models had accuracies of approximately 50% (usually using a Gaussian Naive Bayesian model).  
