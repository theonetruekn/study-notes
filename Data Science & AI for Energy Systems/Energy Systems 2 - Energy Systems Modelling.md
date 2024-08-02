# Energy Systems Modelling
- Energy Systems Modelling is a multi-objective constrained optimization problem
- Energy Systems Modelling looks at the energy system at an hour-by-hour to decade-by-decade resolution, while Stability Analysis looks at the energy system at a second-by-second resolution
### Energy Trilemma
- one categorization of the objectives is the following:
	- sustainability
	- reliability
	- affordability
- these cause a *trilemma* because they are many times counter to each other
___
### Electricity Demand & Resolution 
- load varies around as much as renewable generation varies
	- this must be matched, but due to the variability it is difficult
- if we decrease time resolution, we can see a more predictable variability regarding load
	- for example, on an hour-by-hour time scale, we see that the electricity consumption of private households peaks in the morning and the evening, while there is almost none during the night
- if we decrease spatial resolution, i.e. we look at entire countries or continents, then renewable generation varies less!
	- wind speeds are correlated locally, so if there is no wind in some location, there is probably also not enough wind to power a wind turbine nearby
	- thus, we need to space out our wind turbines to not depend on there being wind at a special place!
	- we can do the same with solar across latitudes
___
### On the mismatch of load and renewables
- the *residual load* at time $t$ is given by $m_t = d_t - Ww_t - Ss_t$ where
	- $d_t$ is the demand at time $t$
	- $Ww_t$ is the wind power generated at time $t$
	- $Ss_t$ is the solar power generated at time $t$
- naturally, the residual load needs to be handled
	- if we have a surplus, we store the excess energy
	- if we have a deficit, we dispatch back-up power
- hence, $m_t = b_t - c_t$, where 
	- $m_t$ is the residual load at time $t$
	- $b_t$ is the back-up power at time $t$
	- $c_t$ is the curtailment at time $t$
### Balancing variations
#### Daily variations
- short-term storage (pumped hydro, batteries)
- demand-management
	- charging EVs with excess power
#### Weekly variations
- medium-term storage (hydro reservoirs, chemically with hydrogen)
#### Seasonal variations
- long-term storage (chemically with hydrogen or methane, long-term thermal storage)
- north-south grids over multiple latitudes
### The benefit of cooperation
- curtailment is a waste of energy
	- we do not have perfect energy conversion efficiency, so when storing energy, we  lose some from our system (or at least it becomes less useful to perform work)
- we can prevent curtailment by cooperating with other countries, where the excess energy can be transmitted to, to be consumed
- a further benefit to cooperation is that each cooperating party can get away with building less storage capabilities themselves
- BUT: this increases the interdependence and reduces sovereignty