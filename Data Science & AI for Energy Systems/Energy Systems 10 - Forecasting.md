## Why Forecasting?
Well, forecasting is basically predicting the future. We are given some historic data, indexed over time, and then we want to get a model that helps us predict the future. It's basically a specialized form of regression.
#### Load Forecasting
- forecasting the future load is quite useful, actually
- if we know that the load will increase some time in the future to some extent, we can start ramping up slow generators or make sure that batteries that will be needed are charged
- we can even incentivize *load-shifting*, i.e. telling people to not use electricity to charge their car right now, if they can also do so later, when there is less demand
#### Price Forecasting
- we all love to save money and as a consumer, knowing when electricity will be expensive, might help you make better decisions about energy usage
- also, as a generator of energy, you surely wanna time when you enter the market to maximize your own profit
#### Generation Forecasting
- kinda similar to the ones before
### Baselines
TODO
### Classical Methods for Forecasting
Let's begin with some simple models that we can later combine into quite powerful stuff.
#### Autoregressive Models (AR)
- Key idea: use past values of the time series to predict the current value
- Generally: $y_t = \phi_1 y_{t-1} + \phi_2 y_{t-2} + ... + \phi_p y_{t-p} + \varepsilon_t$,
    - where $\varepsilon_t$ is i.i.d ~ (mean 0, std $\sigma$) (also called white noise)
- If we go back $p$ time steps, i.e., the oldest value is $y_{t-p}$, we call that an AR model of order $p$, often written as $AR(p)$
#### Moving Average Models (MA)
- Suppose we want random shocks to only affect our predictions for a finite time after they occur
- Then, we cannot use an AR model, as the shocks are embedded infinitely, though with exponentially decaying importance
- We can use an MA model of order $q$, where the prediction directly depends on the past $q$ shocks and each shock affects the predictions only for $q$ time steps into the future
- Generally, it looks like this: $y_t = \mu + \varepsilon_t + \theta_1 \varepsilon_{t-1} + \theta_2 \varepsilon_{t-2} + ... + \theta_q \varepsilon_{t-q}$
#### Integrated Models (I)
- For AR models to work well, we need stationarity for our time series
- There are multiple definitions for stationarity, but one that is quite simple is that the mean and standard deviation need to stay constant over time
- Thus, if there is a trend in any direction, we have a non-stationary time series
- Often, we can turn a non-stationary time series into a stationary one through *differencing*
- Instead of looking at the time series $y_t$, we define a new time series $z_t = y_t - y_{t-1}$
- We can also do this differencing for higher orders, but for now let's focus on differencing of order $1$
### ARIMA
- We can take these different parts and add them all together to get an $ARIMA(p,d,q)$ model, where $p$, $d$ and $q$ refer to the orders of the AR, I and MA parts respectively
- Note that time series enthusiasts love these acronyms and there are plenty of extensions to ARIMA
	- **S**ARIMA - Seasonal
		- similar to $I$, but adds a longer-term seasonal backshift
	- ARIMA**X** - eXogenous
		- this is where we add exogenous variables to our forecast
### Probabilistic Forecasts
TODO
### Forecasting with Deep Learning
- we can use RNNs, which are like NNs, but they keep a state and can thus handle sequences!
- however, as the hidden state of an RNN is updated with each new information, RNNs suffer from a short memory
- one solution is the LSTM, which also learns what to forget and what to add to the hidden state, allowing for a really long short-term memory
	- it's still just a short-term memory because, once some information is purged from the hidden state of the LSTM, it is forever forgotten
- so people came up with *attention*, which is a mechanism to visit all past data points, allowing a model to never forget anything!
- this worked so well that people ditched the RNN-like parts of the architecture and built an entirely new architecture around attention, called a *transformer*
- while there are foundation models for time series, e.g. Time-GPT, they are sadly closed source 🙁
	- the authors likely hope to make big bucks on the stock market with it
### Normalizing Flows?
TODO
- Not sure if its relevant tbh
## Addendum
- you can determine stationarity checking whether the characteristic function of an AR model has a *unit root*