# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION
### Date: 01/09/2026


### AIM:
To Illustrates how to perform time series analysis and decomposition on the monthly average temperature of a city/country and for airline passengers.

### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the decomposition process for the required data.
4. Plot the data according to need, either seasonal_decomposition or trend plot.
5. Display the overall results.

### PROGRAM:
```
# Imports
import os
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose

# Show current folder
print("Current Directory:")
print(os.getcwd())

# Show files in folder
print("\nFiles:")
print(os.listdir())

# Load dataset
data = pd.read_csv(
    'DailyDelhiClimate.csv',   # change filename if needed
    parse_dates=['date'],
    index_col='date'
)


# Sort by date
data = data.sort_index()

# Preview dataset
print("\nFirst 5 Rows:")
print(data.head())

# Select target column
X = data['meantemp']

# Seasonal decomposition
decomposition = seasonal_decompose(
    X,
    model='additive',
    period=30
)

# Plot graphs
plt.figure(figsize=(12, 10))

# Original Data
plt.subplot(411)
plt.plot(X, label='Mean Temperature')
plt.legend(loc='upper left')
plt.title('Mean Temperature')

# Trend
plt.subplot(412)
plt.plot(decomposition.trend, label='Trend', color='orange')
plt.legend(loc='upper left')
plt.title('Trend Plot')

# Seasonal
plt.subplot(413)
plt.plot(decomposition.seasonal, label='Seasonal', color='green')
plt.legend(loc='upper left')
plt.title('Seasonality Plot')

# Residual
plt.subplot(414)
plt.plot(decomposition.resid, label='Residual', color='red')
plt.legend(loc='upper left')
plt.title('Residual Plot')

plt.tight_layout()
plt.show()

```

### OUTPUT:
FIRST FIVE ROWS:

<img width="756" height="263" alt="image" src="https://github.com/user-attachments/assets/52a3b2e0-96d8-4616-9346-a8c070be2b56" />


PLOTTING THE DATA:
<img width="1189" height="989" alt="image" src="https://github.com/user-attachments/assets/42dae173-2d89-44c0-89f2-ee14ede8aa76" />



### RESULT:
Thus we have created the python code for the time series analysis and decomposition.
