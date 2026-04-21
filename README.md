# DeepONet for the stabilization of stochastic PDE-ODE systems

A Python implementation of a numerical solver for coupled Stochastic PDEs-ODEs with Markov chain mode switching. System parameters switch between multiple modes according to a continuous-time Markov chain with time-dependent transition rates. The solver implements a Neural Operator(NO)-based feedback control to stabilize the system.

The code reproduces the experiment in the paper [K. Lyu, U. Biccari, J. Wang - Robust stabilization of hyperbolic PDE-ODE systems via Neural Operator-approximated gain kernels](https://arxiv.org/abs/2508.03242)

# Code Structure

The implementation follows a modular design with clear separation of concerns:

## Core Components
- **Kernel Estimator**: Computes feedback gain functions for the control system  
- **Markov Chain Handler**: Manages mode transitions and probability evolution  
- **PDE Solver**: Implements finite difference schemes for the coupled system  
- **Visualization Suite**: Creates comprehensive plots for analysis  
