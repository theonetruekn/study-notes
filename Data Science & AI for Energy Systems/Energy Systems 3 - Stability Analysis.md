### Differential Equations
- differential equations are equations of the form $\frac{dy}{dx} = f(x,y)$
	- i.e. equations where we look for a function to solve an equation where that function and one of its derivatives occur
- sometimes, we are not just interested in solutions to a differential equation, but also properties thereof
	- in this case, we are talking about *qualitative analysis* of differential equations
- differential equations are, generally speaking, difficult to solve
- there are multiple strategies that can be used on different classes of differential equations
#### Separation of Variables 
- if the differential equations are *separable*, we are in luck and find a nice closed-form solution by using *separation of variables*
	- TODO: mathematically sound example
### Dynamical Systems
- the power system can be modeled well as a *dynamical system*
- *dynamical system* = a system that changes over time according to autonomous differential equations
	- differential equations are autonomous if the variable that we derive with respect to is not included in the equation!
	- For example, $\frac{dx}{dt} = f(x,t)$ is not autonomous, but $\frac{dx}{dt} = g(x)$ is
- dynamical systems are thus *time-invariant*
	- it is assumed that the dynamics of the system don't change over time
	- we model physical systems like this as we assume that the laws of nature hold in the past, in the present and in the future identically
- we call points $x^*$ where $\frac{dx^*}{dt}=0$ *fixed points* or *equilibrium points*, as the points do not change over time, if they reach that state
### Stability
- stability is a property of states of a system
- intuitively, a state $x^*$ is stable if small perturbations of $x^*$ relax back to the state $x(t)~\rightarrow~x^*$
- there are, however, multiple notions of stability that put some constraints on the above idea
	- for example, how quickly the relaxation to the stable state must happen 
- sometimes, we say that the entire system is stable, which means that all equilibrium points are stable
### Linear Systems
- a dynamical system is *linear* if we can formulate it as $\frac{d\mathbf{x}}{dt} = A\mathbf{x}$, where $A$ is a matrix and $\mathbf{x}$ is a vector describing the `coordinates` of the phase space
	- $A$ is often called the *system matrix*
- note that $A$ is either a rotation or translation (or both)
	- technically $A$ does not translate a vector, but scales it.
	- however, if we look at it in an iterative fashion, we get a translation
- if we have a linear system, we can use [[Energy Systems 3 - Stability Analysis#Separation of Variables|Separation of Variables]]!
- the stability of linear systems can be determined by the eigenvalues of $A$
	- if the real parts of the eigenvalues of $A$ are negative, we say that the system is stable
	- the complex parts of the eigenvalues of $A$ determine the oscillatory behavior of the system
### Non-Linear Systems
- Example: Lorenz equations
- not solvable with [[Energy Systems 3 - Stability Analysis#Separation of Variables|Separation of Variables]]
- idea: *linearize* non-linear system
	- basically a first-order Taylor expansion
	- this is fine if we want to analyze local stability, but the approximation error accumulates, so it is not sensible to make statements about the stability at further points
- we use the Jacobian $J$ as our system matrix $A$
	- the eigenvalues of the Jacobian $J$ determine the local (exponential) evolution of the system
	- these eigenvalues are called *Lyapunov Exponents*
- generally speaking, it is very difficult to analyze global stability of non-linear systems
### Bifurcations
- as of now, we asked, given parameters $p$, is the system $S$ stable?
- however, the question, for which set of parameters the system is stable and how the stability changes, is also interesting
- specifically, the question of whether these changes can easily be reverted, is of great interest
- an example of this are *tipping points*, after which there is a qualitative change in the dynamical system
- in general, qualitative changes are called *bifurcations*