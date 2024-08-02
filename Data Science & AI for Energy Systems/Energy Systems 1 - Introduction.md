### Changes in the Energy System
- centralized → decentralized
- increasing number of actors
- consumers also producing electricity for themselves or feeding excess electricity into the grid 
→ the power grid becomes harder to optimize, but if done correctly, could become more robust and cheap
- also, due to smart meters and self-made weather stations, there is more data that can be used for optimization
→ AI
___
AI can be used to improve and make sense of
- generation
- transmission
- consumption
### Energy vs. Power
- Energy is the ability of a system to do work
- Power is the derivative of Energy w.r.t. time
	- intuitively, it can be understood as a measure of how much energy is consumed by a system per time. This amount of energy needs to be provided to the system per time unit, to keep it running / to allow it to perform work
### Generation
- Generation generally happens through the following mechanisms:
	- **thermal**: heat is generated from the underlying source to produce steam (usually from water, sometimes from an organic Rankine cycle fluid), which is used to drive a turbine that is coupled to a generator, producing electrical energy
		- used in coal, nuclear, geothermal, biomass
	- **wind**: wind drives a turbine, which is coupled to a generator , directly, producing electrical energy
	- **photovoltaic**: photovoltaic solar power utilizes the photovoltaic effect to generate electricity directly
		- note that PV solar power is just a subset of solar power. Concentrated solar power works more similar to the thermal method
	- TODO hydropower, natural gas, oil (not relevant for the exam)
- note that there is a difference between the capacity for generation and the actualized generation
	- a country may have a lot of wind turbines, but if there is little wind, then the actual generation from wind power will naturally be lower
#### Synchronous generators
- are called synchronous because the frequency of the resulting (alternating) current is exactly the frequency of the underlying turbine  
- they produce AC because the rotor spins while the stator, the disk surrounding the rotor, is static
	- the magnetic north and south pole are situated on the rotor, which induce a current in the stator
	- hence, due to the rotation of the rotor, the orientation of the magnetic field changes with the frequency of the underlying turbine
- Since PV solar power does not use a generator, the 
#### Load
- the electrical demand / power consumption of all devices that are connected to the power grid
- **Load shedding**: the government or utility companies can disconnect areas or consumers temporarily to reduce the load
- TODO what happens if the load is too high on a physical level?
- TODO how does this happen
___
### Transmission
- We differentiate between synchronous and asynchronous areas
	- synchronous area = area with a balanced supply and demand + shared frequency
- Sometimes, we exchange power via HVDC (High Voltage Direct Current), because it is more efficient than using AC transmission, especially for asynchronous areas
- Note: the higher the voltage, the more efficient the transmission, because the energy losses are reduced, as there is less heat that is generated due to the resistance in the electrical wires. It is the resistors that are warming due to the transmission of electricity.
	- Think of Ohm's law: $R = V/I$. Hence, if we increase $V$, we can surpass the same resistance $R$ with a lower $I$!
	- Also, the equation for power $P = V * I$ and power lost as heat is $P = I^2*R$ might be helpful to see, why a reduction of $I$ is nice
- This is the reason that, after generation at the power plant, the first destination is often a *step-up substation* to increase the voltage even further, especially for transmission over long distances
- As the electricity nears the area where it is to be used, it goes through *step-down substations*, which reduce the voltage to safer and more usable levels
- The electricity is then routed through smaller, local power lines which are part of the distribution network, which handles the final delivery to consumers. These lines are often mounted on poles or underground. 
### Frequency Stability
- We have a base frequency of $50~\text{Hz}$.
- Frequency stability is very important, as appliances are made with a certain frequency in mind. If there is too large of a deviation, this can cause serious damage!
- We can quantify the frequency stability with the following metrics:
	- **Nadir**: Largest frequency deviation
	- **RoCoF** (Rate of Change of Frequency): largest frequency change
	- Integral: aggregated deviation
	- Mean Square Displacement: Mean frequency deviation
### Supply and Demand
- the frequency balances the supply and demand
- if the demand is greater than the supply, the generators slow down, as more kinetic energy is drawn out than is brought back into the rotor
- When the electrical demand exceeds the mechanical energy supply, the generators experience a reduction in rotational speed because the kinetic energy stored in the rotor is converted into electrical energy at a rate faster than it is being replenished.
- if the supply is greater than the demand, the generators speed up, as there is not enough load to absorb the produced energy