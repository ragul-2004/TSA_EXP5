# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION
### Date: 21.09.2024


### AIM:
To Illustrates how to perform time series analysis and decomposition on the monthly average of sales of cinema ticket.

### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the decomposition process for the required data.
4. Plot the data according to need, either seasonal_decomposition or trend plot.
5. Display the overall results.

### PROGRAM:
```
import pandas as pd
from statsmodels.tsa.seasonal import seasonal_decompose
import matplotlib.pyplot as plt

data = pd.read_csv('cinemaTicket_Ref.csv')

data['date'] = pd.to_datetime(data['date'])

data.set_index('date', inplace=True)

print("FIRST FIVE ROWS:")
print(data.head())

weekly_data = data['total_sales'].resample('W').sum()

plt.figure(figsize=(10, 6))
plt.plot(weekly_data, label='Weekly Total Sales')
plt.title('Weekly Total Sales Data')
plt.xlabel('Date')
plt.ylabel('Total Sales')
plt.legend()
plt.show()

decomposition = seasonal_decompose(weekly_data, model='additive', period=4)

print("SEASONAL PLOT REPRESENTATION:")
decomposition.seasonal.plot(figsize=(10, 6))
plt.title('Seasonal Component')
plt.show()

print("TREND PLOT REPRESENTATION:")
decomposition.trend.plot(figsize=(10, 6))
plt.title('Trend Component')
plt.show()

print("OVERALL REPRESENTATION:")
plt.figure(figsize=(12, 8))
decomposition.plot()
plt.show()

``` 

### OUTPUT:
FIRST FIVE ROWS:
![image](https://github.com/user-attachments/assets/45738249-ba8f-458a-9f2b-d4adacdaf0cf)


PLOTTING THE DATA:
![image](https://github.com/user-attachments/assets/d6e5a8f2-7ac7-4a61-854b-29ec47ba58e6)


SEASONAL PLOT REPRESENTATION :
![image](https://github.com/user-attachments/assets/ef340a27-c166-4218-978e-63c322798323)


TREND PLOT REPRESENTATION :
![image](https://github.com/user-attachments/assets/1096dd87-b455-4ad1-8b82-91afdcaf7fe9)


OVERAL REPRESENTATION:
![image](https://github.com/user-attachments/assets/df23f176-5cb5-409b-803a-11e717c2c280)

### RESULT:
Thus we have created the python code for the time series analysis and decomposition.
