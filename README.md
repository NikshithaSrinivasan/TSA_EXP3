# Ex.No: 03   COMPUTE THE AUTO FUNCTION(ACF)
Date: 02.05.2026

### AIM:
To Compute the AutoCorrelation Function (ACF) of the data for the first 35 lags to determine the model
type to fit the data.
### ALGORITHM:
1. Import the necessary packages
2. Find the mean, variance and then implement normalization for the data.
3. Implement the correlation using necessary logic and obtain the results
4. Store the results in an array
5. Represent the result in graphical representation as given below.
### PROGRAM:
import matplotlib.pyplot as plt
import numpy as np
import pandas as pd

# Load the dataset
file_path = "/content/sales.csv"
df = pd.read_csv(file_path)

# Display columns to choose from
print(df.columns)

# Select a numeric column (change this to your actual column name)
# Example: 'Stress_Level', 'Anxiety_Score', etc.
data = df.select_dtypes(include=[np.number]).iloc[:, 0].dropna().values

# Length of data
N = len(data)

# Define lags
lags = range(35)

# Mean and variance
mean_data = np.mean(data)
variance_data = np.var(data)

# Autocorrelation calculation
autocorr_values = []

for lag in lags:
    if lag == 0:
        autocorr_values.append(1)
    else:
        auto_cov = np.sum((data[:-lag] - mean_data) * (data[lag:] - mean_data)) / N
        autocorr_values.append(auto_cov / variance_data)

# Plot
plt.figure(figsize=(10, 6))
plt.stem(lags, autocorr_values)
plt.title('Autocorrelation of Data')
plt.xlabel('Lag')
plt.ylabel('Autocorrelation')
plt.grid(True)
plt.show()

### OUTPUT:
<img width="598" height="411" alt="image" src="https://github.com/user-attachments/assets/52167c30-45aa-44e1-8bfd-b34eeeb64559" />

### RESULT:
        Thus we have successfully implemented the auto correlation function in python.
