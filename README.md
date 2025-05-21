### Developed by: LOKESH KUMAR P
### Reg no: 212222240054
### Date:
# Ex.No: 08     MOVINTG AVERAGE MODEL AND EXPONENTIAL SMOOTHING
 


### AIM:
To implement Moving Average Model and Exponential smoothing Using Python on Annual Change of India's GDP
.
### ALGORITHM:
1. Import necessary libraries
2. Read the electricity time series data from a CSV file,Display the shape and the first 20 rows of
the dataset
3. Set the figure size for plots
4. Suppress warnings
5. Plot the first 50 values of the 'Value' column
6. Perform rolling average transformation with a window size of 5
7. Display the first 10 values of the rolling mean
8. Perform rolling average transformation with a window size of 10
9. Create a new figure for plotting,Plot the original data and fitted value
10. Show the plot
11. Also perform exponential smoothing and plot the graph
### PROGRAM:
```python
# Import necessary libraries
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import warnings
from statsmodels.tsa.holtwinters import ExponentialSmoothing

# Suppress warnings
warnings.filterwarnings('ignore')

# Read the dataset (adjust the path accordingly)
data = pd.read_csv('india-gdp.csv')

# Convert 'Date' to datetime format and set it as the index
data['date'] = pd.to_datetime(data['date'], format='%Y-%m-%d')
data.set_index('date', inplace=True)

# Focus on the 'Adj Close' column
adj_close_data = data[['AnnualChange']]

# Display the shape and the first 5 rows of the dataset
print("Shape of the dataset:", adj_close_data.shape)
print("First 5 rows of the dataset:")
print(adj_close_data.head())

# Plot Original Dataset (Adj Close Data)
plt.figure(figsize=(12, 6))
plt.plot(adj_close_data['AnnualChange'], label='Original Adj Close Data', color='blue')
plt.title('Annual Change of GDP in India')
plt.xlabel('Date')
plt.ylabel('Annual Change)')
plt.legend()
plt.grid()
plt.show()

# Moving Average
# Perform rolling average transformation with a window size of 10
rolling_mean_10 = adj_close_data['AnnualChange'].rolling(window=10).mean()

# Plot Moving Average
plt.figure(figsize=(12, 6))
plt.plot(adj_close_data['Annual Change'], label='Original Adj Close Data', color='blue')
plt.plot(rolling_mean_10, label='Moving Average (window=10)', color='orange')
plt.title('Moving Average of GDP')
plt.xlabel('Date')
plt.ylabel('Annual Change')
plt.legend()
plt.grid()
plt.show()

# Exponential Smoothing
model = ExponentialSmoothing(adj_close_data['Trades'], trend='add', seasonal=None)
model_fit = model.fit()

# Make predictions for the next 30 periods (you can adjust this)
predictions = model_fit.predict(start=len(adj_close_data), end=len(adj_close_data) + 30)

# Plot the original data and Exponential Smoothing predictions
plt.figure(figsize=(12, 6))
plt.plot(adj_close_data['Annual Change'], label='Original Adj Close Data', color='blue')
plt.plot(predictions, label='Exponential Smoothing Forecast', color='orange')
plt.title('Exponential Smoothing Predictions for trades')
plt.xlabel('Date')
plt.ylabel('Annual Change')
plt.legend()
plt.xticks(rotation=45)
plt.grid(True)
plt.tight_layout()
plt.show()
```

### OUTPUT:

  ![Screenshot 2024-10-18 130332](https://github.com/user-attachments/assets/7c5f45fe-dc7c-4d21-89c8-69fafe9a8cf3)


#### Moving Average

![Screenshot 2024-10-18 130347](https://github.com/user-attachments/assets/a0eb7e77-9721-4f45-9872-4bb9cea64dd2)

#### Plot Transform Dataset

![Screenshot 2024-10-18 130356](https://github.com/user-attachments/assets/270ed863-004d-4d78-9f2f-1ea7b0b0213f)


#### Exponential Smoothing

![Screenshot 2024-10-18 130406](https://github.com/user-attachments/assets/11de86d1-4684-4bf9-8d18-95c6c320716f)


### RESULT:
Thus , successful implemention of the Moving Average Model and Exponential smoothing using python is done.
