A Python implementation of a numerical solver for coupled stochastic partial differential equations (PDEs) and ordinary differential equations (ODEs) with Markov chain mode switching. The feature is that system parameters switch between five different modes according to a continuous-time Markov chain with time-dependent transition rates. The solver implements neural operator(NO)-based feedback control to stabilize the system.


# Code Structure

The implementation follows a modular design with clear separation of concerns:

## Core Components
- **Kernel Estimator**: Computes feedback gain functions for the control system  
- **Markov Chain Handler**: Manages mode transitions and probability evolution  
- **PDE Solver**: Implements finite difference schemes for the coupled system  
- **Visualization Suite**: Creates comprehensive plots for analysis  

## Parameter Organization
Parameters are organized into structured dictionaries covering:
- **Grid Parameters**: Spatial and temporal discretization settings  
- **System Parameters**: Physical coefficients and matrices  
- **Initial Conditions**: Starting values for all state variables  
- **Markov Parameters**: Transition rate settings and mode configurations  


---

# Installation

To get started, clone this repository and install the required dependencies. We recommend using a virtual environment. The required packages are listed in `requirements.txt`:

```bash
pip install -r requirements.txt
