# Phase-Two-Project-Repository
<img src="images/house.jpg" alt="House" width=400 height=400 />

# Overview
This project analyzes the aspects of houses in order to reccommend renovations for a real estate office. Descriptive analysis of various aspects of house, such as how many sqft it is, how many floors, and how many bathrooms were used in a linear regression inferential anaylsis to find the highest correlation between the features. Our recommendation for the real estate office in renovating properties is to possibly expand the sqft of homes, including adding more bathrooms and bedrooms. 

# Business Problem
<img src="images/floorplan.jpg" width=400 height=400 />
The local real estate company wants to know what renovations improve the house prices in their area. Inferential statistics of the data provided are depicted in order to aid the the real estate office in understanding the market value in local house renovations in comparison to others in order to recommend profitable renovations to their clients. 

# Data Understanding
<img src="images/interiordesign.jpg" width=400 height=400 />
The data provided is csv file of many different aspects of homes in the area such as how many floors, bathrooms, bedrooms they contain. And also when they were built, renovated, and other aspects such as having a waterfront or a view. 

The highest correlation with price of the houses was sqft feet of the houses. It correlated about 70% with the raw data before modeling for linear regression. 

![image](https://user-images.githubusercontent.com/65221687/174551337-2f84dbe2-bb7a-4304-b9dc-a795b0190da8.png)
![image](https://user-images.githubusercontent.com/65221687/174551503-9117f928-1ada-4592-9cc3-e83b7adc2d66.png)

# Modeling
A baseline model with sqft_living as the most correlated feature was initially created and had similar train and validation scores:
Train score: 0.4877465936487044 Validation score: 0.5024006604207555

A second model was created with streamlining of the features and removing those which had low correlation and little relation: "id", "floors", "yr_renovated". It yielded the highest R-square value and a statistically significant F-statistic. 

A third model was created by singling out two of the significant features: "sqft_living", "bedrooms" however it did not improve the train and test scores:
Train score:      0.5021647986901715
Validation score: 0.515767645499425

A final model from the baseline model was created using the best three features, "sqft_living", "bedrooms", "bathrooms", however it only yielded a fnal test score of .50.

A dummies model including the dummy variables made of the categorical variables Waterfront and View, along with sqft_living onto price was created but had a much lower r-squared value of .283 with a non-statistical significant F-statistic. 

# Regression Results 

The best model, consisting of sqft_living, bedrooms, bathrooms, sqft_lot, sqft_above, sqft_living15 onto price, only accounts for about 50% of the variance as shown below in the OLS Regression results consisting of the R-square = .516 and p-values. 

    OLS Regression Results                            
Dep. Variable:                  price   R-squared:                       0.516
Model:                            OLS   Adj. R-squared:                  0.516
Method:                 Least Squares   F-statistic:                     3838.
Date:                Mon, 20 Jun 2022   Prob (F-statistic):               0.00
Time:                        07:41:45   Log-Likelihood:            -2.9955e+05
No. Observations:               21597   AIC:                         5.991e+05
Df Residuals:                   21590   BIC:                         5.992e+05
Df Model:                           6                                         


 # Issues of multicollinearity within the models
There is also an issue of multicollinearity that became apparent. 
The predicted price shown below does not align well with the perfect line.

![image](https://user-images.githubusercontent.com/65221687/174583786-5bf1c0be-e00d-49ba-a8a8-ee428e030b8c.png)

The Q-Q Plot below showes a curved line indicative of non-normal distribution.

![image](https://user-images.githubusercontent.com/65221687/174579378-d5beb106-8a4a-415b-9c91-e66f66b1b454.png)

High homoscedasticity (Goldfeld-Quandt test) was recorded as well as depicted in the 'funnel' shape below.

![image](https://user-images.githubusercontent.com/65221687/174573378-520bd5af-0980-48a3-a44b-bfc80b58994b.png)

# Conclusions
I would tentatively advise the local real estate office that renovations for more sqft of space within the house and additions of bathrooms and bedrooms could gain more of a profit than other poetential renovations. 

# Next Steps
Perhaps collecting a wider pool of data would add in adding variance and leading to a stronger correlation between the values as well as looking into other aspects of what renovations entell, such as the expense for particular jobs, trends in home making magazines and many other aspects that could lead to different renovation reccommendations for the most profit in resell. 

# For More Information
See the full analysis in the [Jupyter Notebook](https://github.com/rabrya0072/Phase-Two-Project-Repository/blob/main/Real%20estate%20Resale%20Needs%20Analysis.ipynb) or [presentation](https://github.com/rabrya0072/Phase-Two-Project-Repository/blob/main/Phase%202%20Project%20presentation%20(1).pdf) in this repository.

For additional info, contact Rachael Bryant at Rachaelbryant@flatironschool.com
# Repository Structure
├── code
│   ├── __init__.py
│   ├── data_preparation.py
│   ├── visualizations.py
├── data
├── images
├── README.md
├── Real estate Resale Needs Analysis.pdf
└── Real estate Resale Needs Analysis.ipynb




