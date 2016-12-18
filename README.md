# PredictingStockReturns
This project inspired by a recent acquisition activity is Bass Pro to acquire Cabela’s. I would like to look at the revenues and the market share of Cabela’s and one of its competitors, Dick’s Sporting Goods, prior to acquisition and see if there are any features/signals that can be seen in the last few months prior to acquisition. To test this effect with anterior data,  I used both stock market and social media datasets to predict stock returns for Cabela’s and its main competitors. The test RMSE for my model is around 0.019.

## Dataset

Based on the assumptions, I used two main datasets:

● Daily stock price and corporate action for CAB, DKS, HIBB and S&P 500 Index from 2011-10-11 to 2016-10-07. The data was obtained from Yahoo! Finance and amigobulls, which includes the P/E ratio, P/S ratio and stock price for a given day.

● Historical twitter data sent by these companies from 2011-10-11 to 2016-10-07. The data was gathered using Twitter’s API. It contains the timestamp, tweet messages, number of retweets and favorites. Since my analysis is on a daily basis, I aggregate the tweets by date. In addition, more than 160 million public tweets are used to do sentiment analysis. The data can be downloaded from  this website .


## Approach

Daily stock returns are calculated by using adjusted close price and dividends (according to historical corporate action). Twitter data is aggregated to count daily retweets and favorites. The time series data are preprocessed using independent component analysis, window methods and lead-lag correlation, before being fed into the final three models. At the same time, the tweets are converted to numerical features as more positive (+1) or negative (-1) by using doc2vec. Then the mood data and other data are fed to the final model, which blends an AR model, ridge regression and LSTM neural network. Here is a flow diagram of the approach and the illustration of the cross validation process:
