# Monte Carlo Simulation in Comparison to Black-Scholes Model

## Overview

The Black-Scholes model utilizes the concept of Brownian motion to calculate the expected future value of a stock price. Alternatively, we can calculate this expected value using monte carlo simulation; simulating a large number of price paths and averaging them. By doing so, we can observe the convergence of the monte carlo method to the true Black-Scholes value over an increasing number of simulations. The purpose of this project was to execute this monte carlo simulation and price call options using the expected price.

## Black Swan Events

In addition to running standard price path simulations, we can modify our simulations to add a predictive component lacking in the Black-Scholes Model: that of Black Swan events. To implement this, a small probability of a 10% price shock in either direction was added to each day of the simulation. This alternative feature allowed for further insight into the modeling of future prices.
