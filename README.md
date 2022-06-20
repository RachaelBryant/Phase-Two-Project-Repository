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

# Regression Results
The highest correlation with price of the houses was sqft feet of the houses. It correlated about 70% with the raw data before modeling for linear regression. 
![image](https://user-images.githubusercontent.com/65221687/174551337-2f84dbe2-bb7a-4304-b9dc-a795b0190da8.png)
![image](https://user-images.githubusercontent.com/65221687/174551503-9117f928-1ada-4592-9cc3-e83b7adc2d66.png)

However, the best model only accounts for about 50% of the variance as shown below in the table consisting of the R-square and p-values.
    OLS Regression Results                            
==============================================================================
Dep. Variable:                  price   R-squared:                       0.516
Model:                            OLS   Adj. R-squared:                  0.516
Method:                 Least Squares   F-statistic:                     3838.
Date:                Mon, 20 Jun 2022   Prob (F-statistic):               0.00
Time:                        07:41:45   Log-Likelihood:            -2.9955e+05
No. Observations:               21597   AIC:                         5.991e+05
Df Residuals:                   21590   BIC:                         5.992e+05
Df Model:                           6                                         
Covariance Type:            nonrobust                                         
=================================================================================
                    coef    std err          t      P>|t|      [0.025      0.975]
---------------------------------------------------------------------------------
const          2.529e+04   7767.497      3.256      0.001    1.01e+04    4.05e+04
bedrooms      -5.849e+04   2344.638    -24.945      0.000   -6.31e+04   -5.39e+04
bathrooms      8484.0009   3510.979      2.416      0.016    1602.223    1.54e+04
sqft_living     306.6200      4.857     63.127      0.000     297.100     316.141
sqft_lot         -0.3643      0.043     -8.481      0.000      -0.449      -0.280
sqft_above      -41.7428      4.505     -9.265      0.000     -50.574     -32.912
sqft_living15    68.7786      3.986     17.255      0.000      60.966      76.592
==============================================================================
Omnibus:                    15038.016   Durbin-Watson:                   1.984
Prob(Omnibus):                  0.000   Jarque-Bera (JB):           600535.454
Skew:                           2.858   Prob(JB):                         0.00
Kurtosis:                      28.193   Cond. No.                     2.02e+05
==============================================================================

Notes:
[1] Standard Errors assume that the covariance matrix of the errors is correctly specified.
[2] The condition number is large, 2.02e+05. This might indicate that there are
strong multicollinearity or other numerical problems.

The dummies model including the dummy variables made of the categorical variables Waterfront and View, along with sqft_living onto Price also had similar R-squared values and explained variance:
   OLS Regression Results                            
==============================================================================
Dep. Variable:                  price   R-squared:                       0.552
Model:                            OLS   Adj. R-squared:                  0.552
Method:                 Least Squares   F-statistic:                     4437.
Date:                Mon, 20 Jun 2022   Prob (F-statistic):               0.00
Time:                        07:41:03   Log-Likelihood:            -2.9872e+05
No. Observations:               21597   AIC:                         5.974e+05
Df Residuals:                   21590   BIC:                         5.975e+05
Df Model:                           6                                         
Covariance Type:            nonrobust                                         
================================================================================
                   coef    std err          t      P>|t|      [0.025      0.975]
--------------------------------------------------------------------------------
Intercept     1.028e+05   9175.960     11.204      0.000    8.48e+04    1.21e+05
sqft_living    256.6538      1.900    135.083      0.000     252.930     260.378
cyl_YES        5.31e+05   2.49e+04     21.360      0.000    4.82e+05     5.8e+05
yr_EXCELLENT  2.878e+05   1.85e+04     15.583      0.000    2.52e+05    3.24e+05
yr_FAIR       4.909e+04   1.56e+04      3.152      0.002    1.86e+04    7.96e+04
yr_GOOD       8.156e+04   1.34e+04      6.095      0.000    5.53e+04    1.08e+05
yr_NONE      -1.189e+05   7989.878    -14.880      0.000   -1.35e+05   -1.03e+05
==============================================================================
Omnibus:                    13485.396   Durbin-Watson:                   1.976
Prob(Omnibus):                  0.000   Jarque-Bera (JB):           489867.377
Skew:                           2.450   Prob(JB):                         0.00
Kurtosis:                      25.812   Cond. No.                     3.75e+04
==============================================================================

Notes:
[1] Standard Errors assume that the covariance matrix of the errors is correctly specified.
[2] The condition number is large, 3.75e+04. This might indicate that there are
strong multicollinearity or other numerical problems.

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




