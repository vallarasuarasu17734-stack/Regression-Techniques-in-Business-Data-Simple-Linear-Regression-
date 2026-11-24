# Experiment 3: Regression Techniques in Business Data(Simple Linear Regression)

##  Aim
To implement Simple Linear Regression in Python to study and predict the relationship between two business-related variables.

## Dataset
A sample business dataset representing the relationship between **Advertising Expenditure** (in Lakhs) and **Sales Revenue** (in Crores). The goal is to analyze how changes in advertising investment affect sales performance.

| Index | Advertising (Lakhs) | Sales (Crores) |
| :---: | :---: | :---: |
| 0 | 18 | 12 |
| 1 | 22 | 18 |
| 2 | 25 | 20 |
| 3 | 30 | 24 |
| 4 | 35 | 28 |
| 5 | 40 | 35 |
| 6 | 45 | 38 |
| 7 | 50 | 40 |
| 8 | 55 | 42 |
| 9 | 60 | 45 |

## Algorithm / Steps Followed
1. Import required Python libraries (`numpy`, `pandas`, `matplotlib`, `scikit-learn`).
2. Create and load the dataset into a Pandas DataFrame.
3. Display the dataset.
4. Select independent ($X$) and dependent ($Y$) variables and reshape $X$ into a 2D array.
5. Build a `LinearRegression` model using `sklearn.linear_model`.
6. Fit the model and calculate the intercept ($a$) and slope ($b$).
7. Predict $Y$ values for given $X$ values and evaluate performance using the $R^2$ score.
8. Plot the actual data points alongside the fitted regression line and predict sales for a new advertising budget.

##  Functions and Methods Used

| Category | Function / Method | Purpose / Description |
| :--- | :--- | :--- |
| **Data Creation / Handling** | `np.array()` | Create numerical arrays for regression input data |
| | `pd.DataFrame()` | Create or manage tabular data for regression |
| **Model Building (Scikit-learn)** | `LinearRegression()` | Initialize the Simple Linear Regression model |
| | `model.fit()` | Train the linear regression model using $X$ and $Y$ values |
| | `model.predict()` | Predict $Y$ values for given $X$ inputs using the fitted model |
| | `model.score()` | Calculate model performance ($R^2$ score) |
| **Visualization (Matplotlib)** | `plt.scatter()` | Plot scatter points (actual data points) |
| | `plt.plot()` | Plot regression line (predicted relationship) |
| | `plt.title()`, `plt.xlabel()`, `plt.ylabel()`, `plt.show()` | Configure and display the regression plot |

##  Program 
 import numpy as np
    import pandas as pd
    import matplotlib.pyplot as plt
    from sklearn.linear_model import LinearRegression
    
    # Create dataset
    data = {
        'Advertising': [18, 22, 25, 30, 35, 40, 45, 50, 55, 60],
        'Sales': [12, 18, 20, 24, 28, 35, 38, 40, 42, 45]
    }
    
    # Create DataFrame
    df = pd.DataFrame(data)
    
    # Display dataset
    print("Business Dataset:")
    print(df)
    
    # Select independent and dependent variables
    X = df[['Advertising']]
    Y = df['Sales']
    
    # Create Linear Regression model
    model = LinearRegression()
    
    # Train the model
    model.fit(X, Y)
    
    # Calculate intercept and slope
    print("\nIntercept:", model.intercept_)
    print("Slope:", model.coef_[0])
    
    # Predict sales
    y_pred = model.predict(X)
    
    # Calculate R2 score
    print("\nR2 Score:", model.score(X, Y))
    
    # Predict sales for new advertising budget
    new_budget = np.array([[65]])
    predicted_sales = model.predict(new_budget)
    
    print("\nPredicted Sales for Advertising Budget 65 Lakhs:",
          predicted_sales[0])
    
    # Plot actual data and regression line
    plt.scatter(X, Y, color='blue', label='Actual Sales')
    plt.plot(X, y_pred, color='red', label='Regression Line')
    
    plt.title("Advertising vs Sales")
    plt.xlabel("Advertising Expenditure (Lakhs)")
    plt.ylabel("Sales Revenue (Crores)")
    plt.legend()
    plt.grid()
    plt.show()
## Output
        Business Dataset:
       Advertising  Sales
    0           18     12
    1           22     18
    2           25     20
    3           30     24
    4           35     28
    5           40     35
    6           45     38
    7           50     40
    8           55     42
    9           60     45
    
    Intercept: 0.5811563169164877
    Slope: 0.7794432548179872
    
    R2 Score: 0.9736353629160855
    
    Predicted Sales for Advertising Budget 65 Lakhs: 51.24496788008565
    /usr/local/lib/python3.13/dist-packages/sklearn/utils/validation.py:2739: UserWarning: X does not have valid feature names, but LinearRegression was fitted with feature names
      warnings.warn(
      
   <img width="447" height="361" alt="Screenshot 2026-11-24 072622" src="https://github.com/user-attachments/assets/4a2e94f5-d8d6-4159-93e1-25a5bdb558c9" />




##  Result
Thus, Simple Linear Regression was successfully implemented using Python and Scikit-learn. The relationship between advertising expenditure and sales revenue was analyzed, and a regression line was plotted. The model was evaluated using the R² score and used to predict sales revenue for a new advertising budget. The results indicate a positive relationship between advertising investment and sales revenue.
