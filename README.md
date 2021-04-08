# Predicting-financial-recessions-based-on-macroeconomic-indicators

### Data collection
For the macroeconomic indicator data, the most used website is world bank followed by FRED(Federal Reserve Bank Of St.Louis). The website has categories to choose indicators from as decribed above. The free API needs symbol of each indicator to collect data, the list of which is compiled here manually.

Stock market data is collected from yahoo finance and quandl.com as FRED api function in this notebook collects default option of daily stock market data.

Time frame is selected from 1996 to Aug 2020 according to available data.

Consistent with the previous works in the literature, we use business cycle dating chronology provided by NBER which involves dates when recession began and ended in US economy. According to NBER's statistics we have 8 recession periods in our dataset where duration is changing from 6 to 18 months. We represent regimes as "Normal" and "Recession" in our dataset. NBER mentions in chronology dating Aug 2020 update that the peak period in February 2020 is 128 months from previous trough. This it is assumed that March 2020 is a trough, i.e. Recession label and so are following three months.

### Modelling
As the dataset is too small and recessions are in continuous in time series, we cannot use cross validation functions as folds with only one class will be formed.

![image](https://user-images.githubusercontent.com/66875776/113957799-8c2d0e00-97e5-11eb-8628-6df621e541a9.png)

Thus, the blue line graph past 2014 is the predicted probabilities of our model. One can see it does not predict recession for continuous two months until 2020 when the actual recession started. Limitation of this model is the period range of data selected is shorter, as in the online course data was selected for 1960-2018. Thus, with more sophistication this model can be used to predict market recession in one month prior.

### Feature Importance
Feature importance is obtained using the shap library. The results are somewhat intuitive with the Nasdaq lag feature, US exchange rate, federal funds rate and AAA bonnd rate being prominent features that influence the model results.

![image](https://user-images.githubusercontent.com/66875776/113957904-bf6f9d00-97e5-11eb-9e04-b2234f97fca2.png)


### Limitations and Future Scope
Some limitations for this model are described and can be regarded as future scope/tasks for Kaggle and GitHub users:

1. Range of time periods:
The shorter time period was selected for two main reasons:

To consider more number of features such as exchange rates(EXUSUK,etc), Consumer goods demand(ACOGNO) and business inventories(BUSINV), data for which is not available in past.

In addition, it is discussed in the online course that recent data holds more importance to predict future trends.

However, user can experiment with time period to obtain a optimal range with minimal noise.

2. Modern potential indicators are not used such as
(a)cryptocurrency rates,

(b)news sentiment analysis,

(c)Research and innovation indices(especially important going forward owing to public health and climate crisis)

(d)Political and geopolitical stability indices
