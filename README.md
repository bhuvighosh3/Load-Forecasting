# **Load Prediction and Missing Value Imputation using ARIMA**

## **Overview**
This project focuses on forecasting and imputing missing values for electricity load prediction using **ARIMA** and its variants. Both **univariate** and **multivariate** approaches were explored, incorporating **exogenous variables** such as weather conditions and holidays to improve predictive accuracy.

## **Approach**

### **1. Data Preparation**
- Converted `datetime` to a proper format and set it as the index.
- Handled missing values in weather-related features.
- Extracted time-based features such as **hour, day of the week**.
- Created **lag features and rolling averages** to capture historical trends.
- **Holiday mapping**: Created a binary column (**Is_Holiday**) to indicate holiday timestamps.
- **Weather data**: Included factors such as **humidity, temperature, dew point, and wind speed** as exogenous variables.

### **2. Stationarity and Seasonality Checks**
- Used the **Augmented Dickey-Fuller (ADF) test** to check stationarity.
  - The p-value (~5 * 10^-7) indicated that the data is stationary.
- Performed **seasonal decomposition** to analyze seasonality.
  - Results indicated **no strong seasonality**, making ARIMA a suitable choice.

### **3. ARIMA Model Selection**
- **ACF (Autocorrelation Function)** and **PACF (Partial Autocorrelation Function)** were used to determine the appropriate values for p (AR term) and q (MA term).
- **Akaike Information Criterion (AIC)** was used to select the optimal ARIMA parameters.

### **4. Model Implementation**
- **Univariate ARIMA**: Used only past `load` values for forecasting.
- **Multivariate ARIMA (ARIMA with Exogenous Variables)**: Included external factors like weather and holidays.

### **5. Forecasting & Imputation**
- Trained the model on historical data up to **December 13, 2020**.
- Forecasted load values for **December 14, 2020**, at 15-minute intervals.
- Used the model to fill missing `load` values in the dataset.

### **6. Model Evaluation**
- Evaluated forecast accuracy using **Mean Absolute Percentage Error (MAPE)**.
- Achieved a **MAPE of 18%**, indicating strong predictive performance.

## **Results**
- The **ARIMA model** (both univariate and multivariate) effectively forecasted and imputed missing load values.
- Incorporating exogenous variables **(weather and holidays)** improved model performance.
- The model successfully predicted known values (December 12, 2020) with **reasonable accuracy**.

## **Cloning and Setup**
To get started, clone the repository and set up the environment:

```bash
git clone https://github.com/bhuvighosh3/Load-Forecasting.git
