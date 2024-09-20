### Date: 
### Name: Koduru Sanath Kumar Reddy
### Register no: 212221240024
# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION



### AIM:
To Illustrates how to perform time series analysis and decomposition for electricity production

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

<img width="644" alt="image" src="https://github.com/user-attachments/assets/6d6712a7-73fa-4a67-83ef-b0644e34f797">



PLOTTING THE DATA:


<img width="644" alt="image" src="https://github.com/user-attachments/assets/f7292fb8-5d78-4357-aa2d-f9c437eff486">


SEASONAL PLOT REPRESENTATION :


<img width="644" alt="image" src="https://github.com/user-attachments/assets/fda3fab5-c7bc-454d-baa6-b11ad0755514">




TREND PLOT REPRESENTATION :


<img width="644" alt="image" src="https://github.com/user-attachments/assets/6f527058-ce15-4286-b097-aacf212e6d55">



OVERAL REPRESENTATION:


<img width="644" alt="image" src="https://github.com/user-attachments/assets/9a15a9a7-f34f-476f-b6cb-b77f73204b37">




### RESULT:
Thus a python code has been successfully executed for  time series analysis and decomposition of electricity production data.
