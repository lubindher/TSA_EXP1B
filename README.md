# Ex.No: 1B                     CONVERSION OF NON STATIONARY TO STATIONARY DATA

## Developed by : LUBINDHER S
## Register number : 212222240056
## Date: 23/08/24

## AIM:
To perform regular differncing,seasonal adjustment and log transformatio on international airline passenger data
## ALGORITHM:
1. Import necessary libraries (pandas, numpy, matplotlib, statsmodels).
2. Load the international airline passenger data from a CSV file.
3. Perform regular differencing by shifting the data and calculating the difference.
4. Drop any NaN values from the dataset.
5. Decompose the time series data to separate and remove the seasonal component.
6. Apply a logarithmic transformation to stabilize variance.
7. Plot the original, differenced, seasonally adjusted, and log-transformed data.
8. Analyze the plots to confirm the data is stationary.
## PROGRAM:

### REGULAR DIFFERENCING
```
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd
data=pd.read_csv("/content/airline-passengers.csv",parse_dates=['Month'],index_col='Month')
data.head()
passengers = pd.DataFrame(data)
passengers['shifted_value']=passengers['Passengers'].shift(1)
passengers['difference_value']=passengers['Passengers']-passengers['shifted_value']
passengers.dropna(inplace=True)
print(passengers)
passengers.plot(kind='line')
```
### SEASONAL ADJUSTMENT
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose
data=pd.read_csv("/content/airline-passengers.csv",parse_dates=['Month'],index_col='Month')
passengers=pd.DataFrame(data)
result=seasonal_decompose(passengers['Passengers'],model='additive',period=1)
seasonal=result.seasonal
passengers['Seasonal_value']=passengers['Passengers']-seasonal
passengers.dropna(inplace=True)
print(passengers)
passengers.plot(kind='line')
```
### LOG TRANSFORMATIONS
```
import numpy as np
import pandas as pd
data= pd.read_csv('/content/airline-passengers.csv')
data.head()
data.dropna(inplace=True)
x=data['Month']
y=data['Passengers']
data_log=np.log(data['Passengers'])
X=data['Month']
Y=data_log
import matplotlib.pyplot as plt
plt.plot(x,y)
plt.xlabel('Original Data')
plt.plot(X,Y)
plt.xlabel('Log- Transformed data')
```

## OUTPUT:
### REGULAR DIFFERENCING:
![Screenshot 2024-03-06 202154](https://github.com/Yamunaasri/TSA_EXP1B/assets/115707860/907c96c3-9db8-4e90-9bc0-f8b8d3356440)

### SEASONAL ADJUSTMENT:
![image](https://github.com/Yamunaasri/TSA_EXP1B/assets/115707860/e1553866-2b14-473b-9847-bac2bb04ab56)

### LOG TRANSFORMATION:
![image](https://github.com/Yamunaasri/TSA_EXP1B/assets/115707860/76e7ae9b-1487-4e33-a119-2f67e925f218)

## RESULT:
Thus I have created the python code for the conversion of non stationary to stationary data on international airline passenger
data.
