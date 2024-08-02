### Why non-ML Data Analysis?
- (cost/compute) efficient
- ML sucks at extrapolation
	- but are classical methods provably better?
- Variance-Bias trade-off => use less complex model and design features ourselves, if data is limited
___
### Statistical Concepts for Data Analysis
Given a sequence $x_1,~x_2,~\ldots,~x_n$ , we can do some stuff with it.
- take the max or min of the sequence
- or some more complicated stuff, like moments!
#### Moments
- the $n$-th *raw moment* of $X$ is $\mathbb{E}[X^n]$
	- we usually only look at one raw moment, namely the first
	- this is also called the *mean* $\mu$ of $X$, i.e. $\mu = \mathbb{E}[X]$
- the $n$-th *centralized moment* of $X$ is $\mathbb{E}[(X-\mu)^n]$
	- we usually only look at one centralized moment, namely the second
	- this is also called the *variance* $\sigma^2$ of $X$, i.e. $\sigma^2 = \mathbb{E}[(X-\mu)^2]$
	- $\sigma$ is called the *standard-deviation*
- the $n$-th *standardized moment* of $X$ is $\mathbb{E}[(\frac{X-\mu}{\sigma})^n]$
	- we mostly focus on the third and fourth standardized moments
	- the third is the *skewness* of $X$, i.e. $\beta = \mathbb{E}[(\frac{X-\mu}{\sigma})^3] = \frac{\mathbb{E}[(X-\mu)^3]}{\sigma^3}$
	- note that 
		- if $\beta \gt 0$ => more probability-mass left of the mean (left-leaning, right skewed)
		- if $\beta = 0$ => no skew => symmetric distribution
		- if $\beta \lt 0$ => more probability-mass right of the mean (right-leaning, left skewed)\
	- the fourth moment is the *kurtosis* of $X$, i.e. $\mathcal{k} = \frac{\mathbb{E}[(X-\mu)^4]}{\sigma^4}$
		- $\mathcal{k} = 3$ for the Gaussian
		- sometimes, we talk about the *excess kurtosis*,, i.e. $\mathcal{k}_e = \mathcal{k} - 3$
		- quantifies the probability of extreme events, i.e. the fat-tailedness
##### Addendum (for deeper understanding)
- we use $(\cdot)^2$ for the variance to quantify mean deviation instead of the absolute value, because $(\cdot)^2$ is differentiable!
	- but its now scaled quadratically, which is why we need to take the square root to get something similar to mean deviation again, i.e. the standard deviation!
- we need an point-symmetric function to capture the asymmetry of our distribution.
- naturally, we could use the first moment, as the linear function is point-symmetric, but upon further consideration, we notice, that it would not be feasible, as it would always be $0$!
- hence, we use $(\cdot)^3$, as it's the next best thing
	- but now it's scaled to the power of three, so we need to standardize it by dividing by $\sigma^3$
- for a symmetric distribution, i.e. one with no skewness, mean = median
	- if it is further unimodal, mode = mean = median!
- lastly, want to examine the tails with the kurtosis, so we want to highlight extreme deviations from the mean, which is why we use $(\cdot)^4$ and renormalize it by dividing with $\sigma^4$
___
### Handling Periodicity
- sometimes, our sequence may be periodic
- one way to find out whether that is the case, we can use the Fourier Transform!
- the Fourier Transform of an infinite length signal tells us which frequencies occur in that signal
	- in the real world, we usually do not have infinite length signals, but we can still use the Fourier Transform to look at which frequencies are the most likely to occur!
- it decomposes our signal into its constituent frequencies
### Other Decompositions
- we can use Taylor series or Fourier series to decompose any function into a polynomial of (potentially) infinite order or into an infinite sum of sinusoids
	- so we take as input a potentially very complicated function and represent it using very simple functions instead
- what if we want to get something finite? => *Empirical Mode Decomposition* (EMD)
	- the elements of the decomposition are called *Intrinsic Mode Functions* (IMF)
	- downside: the constituents of this decomposition may be more complex
#### EMD
- We can extract the Intrinsic Mode Functions by *sifting*:
	1) identify all extrema
	2) connect all local maxima with cubic splines to form an upper envelope
	3) connect all local minima with cubic splines to form a lower envelope
	4) compute the mean function between the two envelopes
	5) subtract that mean from the original signal to get the first IMF
	6) repeat this process with the just obtained IMF until some stoppage criterion
		- stop if standard deviation is below a threshold
		- stop if the number of zero crossings and extrema doesn't change anymore
		- stop if the extracted IMF amplitudes would be smaller than some threshold
### Handling Trends
- often times real world sequences exhibit complex behavior
- it is a bad idea to use the Fourier Transform on a sequence that trends up- or downwards over time
- we should first *detrend* the sequence
	- we can use the Empirical Mode Decomposition for this, by only keeping low frequency modes
	- we can also apply a Gaussian filter as a convolution, which smooths away the noise