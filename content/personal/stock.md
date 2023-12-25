+++
title = "Stock Price Prediction"
date = "2023-12-16"
tags = [
    "python",
    "machine-learning",
]
+++
### Predicting stock prices using machine learning
<!--more-->
Collected historic stock data by webscrapping yahoo finance utilizing pandas and requests, this dataset includes open, high, low, close prices, and volume traded.

```python
import re
from io import StringIO
from datetime import datetime, timedelta
import requests
import pandas as pd
import requests 

#get the past historical prices of a stock
class YahooFinanceHistory:
    headers={'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/71.0.3578.98 Safari/537.36'}
    quote_link = 'https://query1.finance.yahoo.com/v7/finance/download/{quote}?period1={dfrom}&period2={dto}&interval=1d&events=history'
    def __init__(self, symbol, years_back=7):
        self.dt = timedelta(days=365*years_back)
        self.symbol = symbol
    def get_quote(self):
        now = datetime.utcnow()
        dateto = int(now.timestamp())
        datefrom = int((now - self.dt).timestamp())
        url = self.quote_link.format(quote=self.symbol, dfrom=datefrom, dto=dateto)
        response = requests.get(url, headers=self.headers)
        # print(response.text)
        df = pd.DataFrame([sub.split(",") for sub in StringIO(response.text)])
        df.to_csv("stocks.csv", index=False, header=False)
        return pd.read_csv(StringIO(response.text), parse_dates=['Date'])
```

Forecasting using a Long Short-Term Memory (LSTM) neural network. LSTM is a type of recurrent neural network (RNN) that can learn long-term dependencies between time steps of sequence data. It is a powerful tool for time series forecasting.

```python
import numpy as np
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_squared_error
import matplotlib.pyplot as plt
from datetime import datetime
from keras.layers import LSTM, Dense, Dropout
from keras.models import Sequential

from sklearn.preprocessing import MinMaxScaler
dec_2020 = '2020-12-31'
mask = (df['Date'] <= dec_2020)
data_20 = df.loc[mask]
mask = (df['Date'] > dec_2020)
data_23 = df.loc[mask]
```
Split the data into two sets based on the 'Date' column. data_20 includes rows with dates on or before December 31, 2020, and data_23 includes rows with dates after December 31, 2020.

```python
training_set = data_20.iloc[:, 4:5].values
scaler = MinMaxScaler(feature_range=(0, 1))
scaled_training_set = scaler.fit_transform(training_set)
```
Extracts a cloding price, and scales the values using MinMaxScaler to normalize them between 0 and 1.
    
```python
X_train = []
y_train = []
for i in range(60, 1795):
    X_train.append(scaled_training_set[i-60:i, 0])
    y_train.append(scaled_training_set[i, 0])
X_train, y_train = np.array(X_train), np.array(y_train)
X_train = np.reshape(X_train, (X_train.shape[0], X_train.shape[1], 1))
```
Creates sequences for training the LSTM model. It uses the past 60 days' data to predict the next value. X_train contains sequences of 60 days, and y_train contains the corresponding next-day values.

```python
model = Sequential()
model.add(LSTM(units=100, return_sequences=True, input_shape=(X_train.shape[1], 1)))
model.add(Dropout(0.2))
model.add(LSTM(units=100, return_sequences=True))
model.add(Dropout(0.2))
model.add(LSTM(units=100, return_sequences=True))
model.add(Dropout(0.2))
model.add(LSTM(units=100, return_sequences=False))
model.add(Dropout(0.2))
model.add(Dense(units=1))
model.compile(optimizer='adam', loss="mean_squared_error")
```
This section defines an LSTM model using Keras. The model has four LSTM layers with dropout regularization and a Dense output layer. It is compiled using the Adam optimizer and mean squared error as the loss function.

Training the Model:
```python
hist = model.fit(X_train, y_train, epochs=20, batch_size=32, verbose=2)
```
The model is trained using the training data (X_train and y_train) for 20 epochs with a batch size of 32.

Plotting Training History:
```python
plt.figure(figsize = (16, 8))
plt.plot(hist.history['loss'])
plt.title('model loss')
plt.ylabel('loss')
plt.xlabel('epoch')
plt.legend(['train'], loc='upper left')
plt.show()
```
![static](/img/stockL.svg)

```python
testing_set = data_23.iloc[:, 4:5]
y_test = testing_set.iloc[60:, 0:].values
testing_set = testing_set.iloc[:, 0:].values
scaled_testing_set = scaler.transform(testing_set)
scaled_testing_set.shape
```
Extracts the closing price from the testing set and scales it using the MinMaxScaler.

```python
X_test = []

for i in range(60, 720):
    X_test.append(scaled_testing_set[i-60:i, 0])

X_test = np.array(X_test)
X_test = np.reshape(X_test, (X_test.shape[0], X_test.shape[1], 1))
```
Creates sequences for testing the LSTM model. It uses the past 60 days' data to predict the next value. X_test contains sequences of 60 days.

```python
y_pred = model.predict(X_test)
predicted_price = scaler.inverse_transform(y_pred)
```
Predicts the closing price using the LSTM model and scales it back to the original scale using the MinMaxScaler.

```python
plt.figure(figsize=(16, 8))
plt.plot(y_test, color='blue', label='Actual Stock Price')
plt.plot(predicted_price, color='red', label='Predicted Stock Price')
plt.title('Stock Price Prediction')
plt.xlabel('Time')
plt.ylabel('Stock Price')
plt.legend()
plt.show()
```
Plots the actual and predicted stock prices.

![static](/img/stock.svg)

This shows the predicted and actual stock price of AAPL from January 1, 2021, to December 31, 2021. The model predicts the stock price with a high degree of accuracy.