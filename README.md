# Ex.No: 03   COMPUTE THE AUTO FUNCTION(ACF)
Date: 06/11/2026.

Data set: Tesla stock price.

### AIM:
To compute the Autocorrelation Function (ACF) of the Tesla (TSLA) stock closing price data for the first 35 lags to identify the correlation between current and previous stock prices and determine the suitable time series model.
### ALGORITHM:
1.Import the necessary Python libraries such as Pandas, NumPy and Matplotlib.

2.Load the Tesla (TSLA) stock price dataset using Pandas.

3.Remove the missing values from the closing price column.

4.Calculate the mean and variance of the Tesla closing prices.

5.Normalize the data using the calculated mean and variance.

6.Compute the Autocorrelation Function (ACF) for the first 35 lags.

7.Store the calculated autocorrelation values in an array.

8.Plot the ACF values using a stem plot with appropriate labels and title.

9.Analyze the autocorrelation graph to understand the relationship between Tesla stock prices at different time lags.

### PROGRAM:
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

df = pd.read_csv("/content/TSLA.csv")
df = df.dropna(subset=["Close"])
data = df["Close"].to_numpy()

N = len(data)
lags = range(35)
mean_data = np.mean(data)
variance_data = np.var(data)
normalized_data = (data - mean_data) / np.sqrt(variance_data)

autocorr_values = []
for lag in lags:
    if lag == 0:
        autocorr_values.append(1)
    else:
        auto_cov = np.sum(
            normalized_data[:-lag] * normalized_data[lag:]
        ) / N
        autocorr_values.append(auto_cov)

plt.figure(figsize=(10,6))
plt.stem(lags, autocorr_values)
plt.title("Autocorrelation Function (ACF) of TSLA Close Price")
plt.xlabel("Lag")
plt.ylabel("Autocorrelation")
plt.grid(True)
plt.show()
```
### OUTPUT:
<img width="758" height="435" alt="image" src="https://github.com/user-attachments/assets/9a4aadd2-9c40-4082-b838-d27de770f6c6" />


### RESULT:
Thus, the Autocorrelation Function (ACF) was successfully computed for the Tesla (TSLA) stock closing price dataset for the first 35 lags using Python. The autocorrelation values were stored and visualized using a stem plot to analyze the relationship between current and previous stock prices
