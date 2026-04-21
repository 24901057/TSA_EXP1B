# Ex.No: 1B                     CONVERSION OF NON STATIONARY TO STATIONARY DATA
# Date: 21-04-2026

### AIM:
To perform regular differncing,seasonal adjustment and log transformatio on international airline passenger data
### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the data preprocessing if needed and apply regular differncing,seasonal adjustment,log transformation.
4. Plot the data according to need, before and after regular differncing,seasonal adjustment,log transformation.
5. Display the overall results.
### PROGRAM:
```py
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose
data=pd.read_csv("/content/Walmart_Sales.csv")
data=data.head(1000)
data.head()
data['Date']=pd.to_datetime(data['Date'],dayfirst=True)

data.set_index('Date',inplace=True)
data['Weekly_Sales_diff']=data['Weekly_Sales']-data['Weekly_Sales'].shift(1)
result=seasonal_decompose(data['Weekly_Sales'],model='additive',period=12)
data['weekly_sales_sea_diff']=result.resid

data['Weekly_Sales_log']=np.log(data['Weekly_Sales'])
data['Weekly_Sales_log_diff']=data['Weekly_Sales']-data['Weekly_Sales'].shift(1)

result=seasonal_decompose(data['Weekly_Sales'],model='additive',period=12)
data['weeklysales_log_sea_diff']=result.resid
plt.figure(figsize=(16,16))

plt.subplot(6,1,1)
plt.plot(data['Weekly_Sales'],label="Original")
plt.legend(loc="best")
plt.title('Original data')
plt.xlabel('Date')
plt.ylabel('Weekly Sales')

plt.subplot(6,1,2)
plt.plot(data['Weekly_Sales_diff'],label="Regular Difference")
plt.legend(loc="best")
plt.title('Regular Difference')
plt.xlabel('Date')
plt.ylabel('Weekly Sales')

plt.subplot(6,1,3)
plt.plot(data['weekly_sales_sea_diff'],label="Seasonal Adjustment")
plt.legend(loc="best")
plt.title('Seasonal Adjustment')
plt.xlabel('Date')
plt.ylabel('Weekly Sales')

plt.subplot(6,1,4)
plt.plot(data['Weekly_Sales_log'],label="Log Transformation")
plt.legend(loc="best")
plt.title('Log Transformation')
plt.xlabel('Date')
plt.ylabel('log(Weekly Sales)')

plt.subplot(6,1,5)
plt.plot(data['Weekly_Sales_log_diff'],label="Log Transformation and Regular Difference")
plt.legend(loc="best")
plt.title('Log Transformation and regular Difference')
plt.xlabel('Date')
plt.ylabel('RDiff(log(Weekly Sales))')

plt.subplot(6,1,6)
plt.plot(data['weeklysales_log_sea_diff'],label="Log Transformation and Regular Difference and Seasonal Difference")
plt.legend(loc="best")
plt.title('Log Transformation and  Regular Difference and Seasonal Difference')
plt.xlabel('Date')
plt.ylabel('SDiff(RDiff(log(Weekly Sales)))')
plt.tight_layout()
plt.show()

```

### OUTPUT:
<img width="1086" height="262" alt="image" src="https://github.com/user-attachments/assets/a845a519-f1df-4f1a-b4f7-223148c5b2f6" />

ORIGINAL DATA:

<img width="1662" height="291" alt="image" src="https://github.com/user-attachments/assets/0d0cedeb-04cd-4f80-8122-faaa7117df5f" />

REGULAR DIFFERENCING:

<img width="1648" height="276" alt="image" src="https://github.com/user-attachments/assets/e35f462b-2dbc-4459-abec-4846bca6e745" />

SEASONAL ADJUSTMENT:

<img width="1669" height="281" alt="image" src="https://github.com/user-attachments/assets/572f60b8-fcd9-4021-af8c-fd066ca8e3f5" />

LOG TRANSFORMATION:

<img width="1723" height="799" alt="image" src="https://github.com/user-attachments/assets/0decb116-2764-46cf-b31e-06456a2a417a" />


### RESULT:
Thus we have created the python code for the conversion of non stationary to stationary data on international airline passenger
data.
