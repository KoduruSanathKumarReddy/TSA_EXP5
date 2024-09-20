### Date: 
### Name: Koduru Sanath Kumar Reddy 
### Register no:212221240024
# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION



### AIM:
To Illustrates how to perform time series analysis and decomposition on electrict production of a city.

### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the decomposition process for the required data.
4. Plot the data according to need, either seasonal_decomposition or trend plot.
5. Display the overall results.

### PROGRAM:



~~~

import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose

df = pd.read_csv('Electric_Production.csv')
print(df.head())

df['DATE'] = pd.to_datetime(df['DATE'])
df.set_index('DATE', inplace=True)
print(df.info())

plt.figure(figsize=(12, 6))
plt.plot(df, label='Electric Production', color='blue')
plt.title('Electric Production Over Time')
plt.xlabel('Date')
plt.ylabel('Production')
plt.legend()
plt.show()


decomposition = seasonal_decompose(df['IPG2211A2N'], model='additive') # Changed 'Value' to 'IPG2211A2N' 
seasonal = decomposition.seasonal
plt.figure(figsize=(12, 6))
plt.plot(seasonal, label='Seasonal Component', color='green')
plt.title('Seasonal Component of Electric Production')
plt.xlabel('Date')
plt.ylabel('Seasonal Effect')
plt.legend()
plt.show()

trend = decomposition.trend
plt.figure(figsize=(12, 6))
plt.plot(trend, label='Trend Component', color='orange')
plt.title('Trend Component of Electric Production')
plt.xlabel('Date')
plt.ylabel('Trend Effect')
plt.legend()
plt.show()

plt.subplot(4, 1, 4)
plt.plot(decomposition.resid, label='Residual', color='red')
plt.title('Over All Component')
plt.legend()

plt.tight_layout()
plt.savefig('decomposition_plots.png')  # Save decomposition plots as an image
plt.show()
~~~













### OUTPUT:
FIRST FIVE ROWS:
<img width="256" alt="image" src="https://github.com/user-attachments/assets/958cdfa4-dc0b-4c94-96e5-d9264147179a">




PLOTTING THE DATA:
<img width="644" alt="image" src="https://github.com/user-attachments/assets/83844a95-43b3-4258-8797-e226e2a2ef4b">


SEASONAL PLOT REPRESENTATION :
<img width="644" alt="image" src="https://github.com/user-attachments/assets/9ed1dfa9-e862-4d14-a90b-44e1a55cd8ec">




TREND PLOT REPRESENTATION :
<img width="644" alt="image" src="https://github.com/user-attachments/assets/101832fd-edf7-4c78-bd78-1f0795cdcaf6">


OVERAL REPRESENTATION:
<img width="644" alt="image" src="https://github.com/user-attachments/assets/96439a48-519d-46c1-aed2-f9affc516588">




### RESULT:
Thus a python code has beem successfully executed for time series analysis and decomposition.
