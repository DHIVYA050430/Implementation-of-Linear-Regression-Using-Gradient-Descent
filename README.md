# Implementation-of-Linear-Regression-Using-Gradient-Descent

## AIM:
To write a program to predict the profit of a city using the linear regression model with gradient descent.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1.Data Preparation: Collect historical data on city population (feature) and corresponding profits (target).

2.Initialization: Set initial values for model parameters (θ) and choose a learning rate (α).

3.Hypothesis & Cost Function: Define the hypothesis ℎ𝜃(𝑥)=𝜃0+𝜃1𝑥 and the cost function as Mean Squared Error (MSE).

4.Gradient Descent: Update parameters iteratively:
## Program:
```
/*
Program to implement the linear regression using gradient descent.
Developed by: DIVYA E
RegisterNumber:  212223230050
*/

import numpy as np
import pandas as pd
from sklearn.preprocessing import StandardScaler
def linear_regression (X1, y, learning_rate=0.01, num_iters=1000):
  X = np.c_[np.ones(len(X1)), X1]
  theta = np.zeros(X.shape[1]).reshape(-1,1)
  for _ in range(num_iters):
    predictions = (X).dot(theta).reshape(-1, 1)
    errors =(predictions -y).reshape(-1,1)
    theta -=learning_rate* (1/len(X1))* X.T.dot(errors)
  return theta
data = pd.read_csv('50_Startups.csv',header=None)
X = (data.iloc[1:,: -2].values)
X1=X.astype(float)
scaler = StandardScaler()
y = (data.iloc[1:,-1].values).reshape(-1,1)
X1_Scaled = scaler.fit_transform(X1)
Y1_Scaled = scaler.fit_transform(y)
# Example usage
#X = np.array([[1, 2], [3, 4], [5, 6], [7, 8]])
#y = np.array([2, 7, 11, 16])
# Learn model parameters
theta =linear_regression (X1_Scaled, Y1_Scaled)
new_data = np.array([165349.2,136897.8,471784.1]).reshape(-1,1)
new_Scaled =scaler.fit_transform(new_data)
prediction =np.dot(np.append(1, new_Scaled), theta)
prediction=prediction.reshape(-1,1)
pre=scaler.inverse_transform(prediction)
print (f"Predicted value: {pre}")
```
## Output:
![alt text](image.png)


## Result:
Thus the program to implement the linear regression using gradient descent is written and verified using python programming.
