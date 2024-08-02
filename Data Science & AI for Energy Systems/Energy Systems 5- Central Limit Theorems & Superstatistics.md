### Central Limit Theorem
- Say you have a random variable $X$ that we sample many times
- Let's denote realization $i$ by $X_i$ and define the sample average $\bar{X}_N=\frac{1}{n}\sum_{i=1}^NX_i$
- For $N \rightarrow \infty$, we get $\bar{X_N} = \mu$, i.e. the true mean of $X$
- But what about the distribution of $\bar{X}_N$?
- Well, the *Central Limit Theorem* claims that, for any sum $S_N=\sum_{i=1}^NX_i$ of i.i.d. random variables $X_i$, $S_N$ converges *in distribution* to $N(n\mu, n\sigma)$.
	- This only works if we have finite variance!
	- Note that the convergence is slower for fat-tailed distributions, so you need more data to get an accurate Gaussian approximation
- Working with Gaussian distributions is nice
	- they naturally occur in nature very often
	- the convolution of a Gaussian over another Gaussian is another Gaussian
	- in Bayesian Inference, if we have a Gaussian prior and a Gaussian likelihood, we get a Gaussian posterior
	- our life is easy!
- Alas, for energy systems, we could theoretically get infinite variance, so we need something more general, that is still nice to deal with
=> Stable distributions!
### Stable Distributions
- stable distributions are a rich class of probability distributions
- a distribution $X$ is stable if and only if the sum of $n$ i.i.d. copies of $X$ can be rescaled and recentered to have the same distribution as $X$
	- remember how Gaussians can be added and we get another Gaussian?
	- the same is true for Cauchy distributions, the infinite-variance cousin of the Gaussian
	- the stable distributions generalize over that self-similarity property, to include all distributions where that is true!
- we can now drop the finite variance requirement from our Central Limit Theorem, to get a Generalized Central Limit Theorem, which says that $S_N$ converges in distribution to a stable distribution!
___
- sadly, most lack an analytic probability distribution function
	- exceptions are the Gaussian, Levy and Cauchy distributions
- we thus express their pdf through their characteristic function
	- think of the characteristic function of a random variable as its Fourier Transform (with sign reversal)  $\phi_X(t) = \mathbb{E}[e^{itX}]$
	- if we invert the characteristic function, we get the pdf of $X$
- there are multiple parameters that we can choose to get an instance of a stable distribution
	- $\alpha \in (0,2]$, which indicates how fat the tails are
		- this is related to the fourth moment of a distribution and tells us about how likely extreme events are
		- the Gaussian distribution has $\alpha = 2$
		- As $\alpha \rightarrow 0$ we get fatter tails, as $P(X > x) \xrightarrow{x \to \infty} x^{-\alpha}$
	- $\beta \in [-1, 1]$, which indicates the skewness
	- $c \in (0, \infty)$, which indicates the scale of the distribution
		- in the Gaussian sense, this is strongly related to the standard deviation
		- if $c=0$, then we get a degenerate distribution
	- $\mu \in (-\infty, \infty)$, which is the location parameter
		- in the Gaussian setting, this is the mean
### Superstatistics
- central idea:
	- superimpose simple (e.g. Gaussian) distributions to explain the apparent complexity in observed statistics
	- each (simple) distribution is applicable to one time scale
- so we basically want to look in our data whether something is locally Gaussian, i.e. at some time scale
- we do this by computing the local kurtosis $k$ for different time scales and solving $\Delta t$ for $k(\Delta t) = 3$
- then, as soon as we have identified the time scale for which we do get a Gaussian, for example if we look at daily intervals, we go through every day of our entire signal and find out the variance $\sigma^2$ of the Gaussian of the day. For some reason unbeknownst to me, we collect $\beta_{t_0} = \frac{1}{\sigma^2}$ for all time steps $t_0$ and fit a distribution $f(\beta)$
- lastly, we construct our superstatistical distribution $P(E) = \int_0^\infty P(E|\beta)f(\beta)d\beta$
- apparently, $P(E)$ is often *q-Gaussian*, which seems to be nice?