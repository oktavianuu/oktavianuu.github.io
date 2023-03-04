---
title: Testing linear regression assumptions in python
date: 2023-02-27 18:50:00 +07:00
modified: 
description:
image:
---
Regresi adalah salah satu model statistik yang digunakan untuk memprediksi satu variabel berdasarkan variabel lain. Esensi dari regresi adalah memasukan sebuah model ke data set yang sedang kita kerjakan untuk memprediksi nilai dari variabel terikat (y) dari satu atau lebih variabel bebas (x). Analisis regresi adalah cara untuk memprediksi nilai variabel terikat berdasarkan satu variabel prediktor (sederhana) atau beberapa variabel prediktor (berganda). Analisis regresi sangat bermanfaat karena dapat membantu kita untuk melihat/memaknai data lebih dalam. 

Sebelum melakukan analisis regresi linear, terdapat beberapa asumsi yang harus terpenuhi agar model regresi dapat menginterpretasikan data dengan tepat. Linear regresi memberikan kelebihan dari algoritma regresi lainnya dilihat dari segi kesederhanaannya, kecepatan dalam <em>training</em> data sehingga menjadikannya cocok untuk digunakan untuk kasus-kasus regresi yang umum ditemukan. Terdapat lima asumsi yang harus dan wajib terpenuhi dalam regresi linear yaitu:
1. Linearitas
2. Normalitas
3. Homoskedastisitas
4. Autokorelasi
5. Multikolinearitas


Tulisan ini menjelaskan uji asumsi-asumsi yang harus terpenuhi dalam regresi linear menggunankan python. 
Data dan uji regresi linier menggunakan R dapat didownload di lampiran pada bagian akhir postingan ini.

Untuk memudahkan pengujian, kita menggunakan beberapa library yaitu ```numpy, pandas, matplotlib, seaborn dan sklearn.``` Tutorial ini dapat dilakukan menggunakan Jupyter Notebook atau IPython. 

##### Mendownload dan memasukan data
```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
from sklearn import datasets
%matplotlib inline

"""
Kita menggunakan data perumahan Boston,
Dokumentasi lengkap data ini dapat diakses pada alamat https://www.cs.toronto.edu/~delve/data/boston/bostonDetail.html

Attributes:
data: Features/predictors
label: Target/label/response variable
feature_names: Abbreviations of names of features
"""
data_boston = datasets.load_boston()

"""
Artificial linear data using the same number of features and observations as the
Boston housing prices dataset for assumption test comparison
"""
linear_X, linear_y = datasets.make_regressin(n_samples=boston.data.shape[0], n_features=boston.data.shape[1], noise=75, random_state=46)

# Setting feature names to x1, x2, x3, etc. if they are not defined
linear_feature_names = ['X'+str(feature+1) for feature in range(linear_X.shape[1])]
```
Setelah data dimasukkan, kita dapat melihat/ <em>mempreview</em> data menggunakan <em>script</em> berikut:
```python
df = pd.DataFrame(boston.data, columns=boston.feature_names)
df['HousePrice] = boston.target

df.head()
```
Script di atas akan menampilkan lima baris data pertama. 

##### Initial Setup
Sebelum menguji kelima asumsi regresi linear, kita harus <em>mem-fit</em> model regresi linear terlebih dahulu. Beberapa uji akan menggunakan residual, jadi kita juga harus membuat fungsi untuk menghitung residual. 
```python
from sklearn.linear_model import LinearRegression

# memfitting model
boston_model = LinearRegression()
boston_model.fit(boston_data, boston_target)

# Menghitung R^2 model
boston_r2 = boston_model.score(boston_data, boston_target)
print('R^2: {0}'.format(boston_r2))
```

output: 
```python 
R^2: 0.7406077428649428
```
Kemudian kita harus <em>memfitting</em> model:
```python
# Fitting the model
linear_model = LinearRegression()
linear_model.fit(linear_X, linear_y)

# menghitung R^2 untuk model
linear_r2 = linear_model.score(linear_X, linear_y)
print('R^2: {0}'.format(linear_r2))
```
output:
```python 
R^2: 0.873743725796525
```
Kemudian kita hitung residual dengan membuat fungsi berikut:
```python
def calculate_residuals(model, features, label):
    """
    Creates predictions on the features with the model and calculates residuals
    """
    predictions = model.predict(features)
    df_results = pd.DataFrame({'Actual': label, 'Predicted': predictions})
    df_results['Residuals'] = abs(df_results['Actual']) - abs(df_results['Predicted'])
    
    return df_results
```
Uji asumsi regresi linier

```python
def linear_regression_assumptions(features, label, feature_names=None):
    """
    Tests a linear regression on the model to see if assumptions are being met
    """
    from sklearn.linear_model import LinearRegression
    
    # Setting feature names to x1, x2, x3, etc. if they are not defined
    if feature_names is None:
        feature_names = ['X'+str(feature+1) for feature in range(features.shape[1])]
    
    print('Fitting linear regression')
    # Multi-threading if the dataset is a size where doing so is beneficial
    if features.shape[0] < 100000:
        model = LinearRegression(n_jobs=-1)
    else:
        model = LinearRegression()
        
    model.fit(features, label)
    
    # Returning linear regression R^2 and coefficients before performing diagnostics
    r2 = model.score(features, label)
    print()
    print('R^2:', r2, '\n')
    print('Coefficients')
    print('-------------------------------------')
    print('Intercept:', model.intercept_)
    
    for feature in range(len(model.coef_)):
        print('{0}: {1}'.format(feature_names[feature], model.coef_[feature]))

    print('\nPerforming linear regression assumption testing')
    
    # Creating predictions and calculating residuals for assumption tests
    predictions = model.predict(features)
    df_results = pd.DataFrame({'Actual': label, 'Predicted': predictions})
    df_results['Residuals'] = abs(df_results['Actual']) - abs(df_results['Predicted'])

    
    def linear_assumption():
        """
        Linearity: Assumes there is a linear relationship between the predictors and
                   the response variable. If not, either a polynomial term or another
                   algorithm should be used.
        """
        print('\n=======================================================================================')
        print('Assumption 1: Linear Relationship between the Target and the Features')
        
        print('Checking with a scatter plot of actual vs. predicted. Predictions should follow the diagonal line.')
        
        # Plotting the actual vs predicted values
        sns.lmplot(x='Actual', y='Predicted', data=df_results, fit_reg=False, size=7)
        
        # Plotting the diagonal line
        line_coords = np.arange(df_results.min().min(), df_results.max().max())
        plt.plot(line_coords, line_coords,  # X and y points
                 color='darkorange', linestyle='--')
        plt.title('Actual vs. Predicted')
        plt.show()
        print('If non-linearity is apparent, consider adding a polynomial term')
        
        
    def normal_errors_assumption(p_value_thresh=0.05):
        """
        Normality: Assumes that the error terms are normally distributed. If they are not,
        nonlinear transformations of variables may solve this.
               
        This assumption being violated primarily causes issues with the confidence intervals
        """
        from statsmodels.stats.diagnostic import normal_ad
        print('\n=======================================================================================')
        print('Assumption 2: The error terms are normally distributed')
        print()
    
        print('Using the Anderson-Darling test for normal distribution')

        # Performing the test on the residuals
        p_value = normal_ad(df_results['Residuals'])[1]
        print('p-value from the test - below 0.05 generally means non-normal:', p_value)
    
        # Reporting the normality of the residuals
        if p_value < p_value_thresh:
            print('Residuals are not normally distributed')
        else:
            print('Residuals are normally distributed')
    
        # Plotting the residuals distribution
        plt.subplots(figsize=(12, 6))
        plt.title('Distribution of Residuals')
        sns.distplot(df_results['Residuals'])
        plt.show()
    
        print()
        if p_value > p_value_thresh:
            print('Assumption satisfied')
        else:
            print('Assumption not satisfied')
            print()
            print('Confidence intervals will likely be affected')
            print('Try performing nonlinear transformations on variables')
        
        
    def multicollinearity_assumption():
        """
        Multicollinearity: Assumes that predictors are not correlated with each other. If there is
                           correlation among the predictors, then either remove prepdictors with high
                           Variance Inflation Factor (VIF) values or perform dimensionality reduction
                           
                           This assumption being violated causes issues with interpretability of the 
                           coefficients and the standard errors of the coefficients.
        """
        from statsmodels.stats.outliers_influence import variance_inflation_factor
        print('\n=======================================================================================')
        print('Assumption 3: Little to no multicollinearity among predictors')
        
        # Plotting the heatmap
        plt.figure(figsize = (10,8))
        sns.heatmap(pd.DataFrame(features, columns=feature_names).corr(), annot=True)
        plt.title('Correlation of Variables')
        plt.show()
        
        print('Variance Inflation Factors (VIF)')
        print('> 10: An indication that multicollinearity may be present')
        print('> 100: Certain multicollinearity among the variables')
        print('-------------------------------------')
       
        # Gathering the VIF for each variable
        VIF = [variance_inflation_factor(features, i) for i in range(features.shape[1])]
        for idx, vif in enumerate(VIF):
            print('{0}: {1}'.format(feature_names[idx], vif))
        
        # Gathering and printing total cases of possible or definite multicollinearity
        possible_multicollinearity = sum([1 for vif in VIF if vif > 10])
        definite_multicollinearity = sum([1 for vif in VIF if vif > 100])
        print()
        print('{0} cases of possible multicollinearity'.format(possible_multicollinearity))
        print('{0} cases of definite multicollinearity'.format(definite_multicollinearity))
        print()

        if definite_multicollinearity == 0:
            if possible_multicollinearity == 0:
                print('Assumption satisfied')
            else:
                print('Assumption possibly satisfied')
                print()
                print('Coefficient interpretability may be problematic')
                print('Consider removing variables with a high Variance Inflation Factor (VIF)')
        else:
            print('Assumption not satisfied')
            print()
            print('Coefficient interpretability will be problematic')
            print('Consider removing variables with a high Variance Inflation Factor (VIF)')
        
        
    def autocorrelation_assumption():
        """
        Autocorrelation: Assumes that there is no autocorrelation in the residuals. If there is
                         autocorrelation, then there is a pattern that is not explained due to
                         the current value being dependent on the previous value.
                         This may be resolved by adding a lag variable of either the dependent
                         variable or some of the predictors.
        """
        from statsmodels.stats.stattools import durbin_watson
        print('\n=======================================================================================')
        print('Assumption 4: No Autocorrelation')
        print('\nPerforming Durbin-Watson Test')
        print('Values of 1.5 < d < 2.5 generally show that there is no autocorrelation in the data')
        print('0 to 2< is positive autocorrelation')
        print('>2 to 4 is negative autocorrelation')
        print('-------------------------------------')
        durbinWatson = durbin_watson(df_results['Residuals'])
        print('Durbin-Watson:', durbinWatson)
        if durbinWatson < 1.5:
            print('Signs of positive autocorrelation', '\n')
            print('Assumption not satisfied', '\n')
            print('Consider adding lag variables')
        elif durbinWatson > 2.5:
            print('Signs of negative autocorrelation', '\n')
            print('Assumption not satisfied', '\n')
            print('Consider adding lag variables')
        else:
            print('Little to no autocorrelation', '\n')
            print('Assumption satisfied')

            
    def homoscedasticity_assumption():
        """
        Homoscedasticity: Assumes that the errors exhibit constant variance
        """
        print('\n=======================================================================================')
        print('Assumption 5: Homoscedasticity of Error Terms')
        print('Residuals should have relative constant variance')
        
        # Plotting the residuals
        plt.subplots(figsize=(12, 6))
        ax = plt.subplot(111)  # To remove spines
        plt.scatter(x=df_results.index, y=df_results.Residuals, alpha=0.5)
        plt.plot(np.repeat(0, df_results.index.max()), color='darkorange', linestyle='--')
        ax.spines['right'].set_visible(False)  # Removing the right spine
        ax.spines['top'].set_visible(False)  # Removing the top spine
        plt.title('Residuals')
        plt.show() 
        print('If heteroscedasticity is apparent, confidence intervals and predictions will be affected')
        
        
    linear_assumption()
    normal_errors_assumption()
    multicollinearity_assumption()
    autocorrelation_assumption()
    homoscedasticity_assumption()
```

Data yang digunakan dapat didownload [disini](https://docs.google.com/spreadsheets/d/1gB3bxCaZiEfT9yozqFaLC-vQKICfkuOR/edit?usp=sharing&ouid=113871522222072694770&rtpof=true&sd=true).
Tutorial regresi linier menggunakan R dapat didownload [disini](https://drive.google.com/file/d/1A6mIc2zECq1dAnUVZPD6R29viZb3soH_/view?usp=sharing).