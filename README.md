# Neural-Operator Stabilization of Stochastic PDE–ODE Systems

This repository accompanies the paper [*Robust stabilization of hyperbolic PDE-ODE systems via Neural Operator-approximated gain kernels*](https://arxiv.org/abs/2508.03242).
It implements the simulation and control of a coupled hyperbolic PDE–ODE system whose transport and coupling parameters 
switch randomly between modes according to a continuous-time Markov process. A DeepONet-based neural operator approximates 
the backstepping gain kernels needed by the boundary feedback controller, enabling rapid control evaluation under stochastic switching.

## Motivation

Coupled PDE–ODE models arise when distributed dynamics interact with finite-dimensional components, for example in traffic-flow, 
fluid-transport, and energy systems. In practice, their coefficients can change unpredictably because of disturbances, 
changing operating conditions, or uncertain physical parameters.

Backstepping provides a constructive way to stabilize these systems through boundary feedback, but it requires solving 
coupled kernel equations for every relevant parameter configuration. That cost limits its use in switching and real-time settings. 
The objective is to retain the robustness of backstepping control while replacing repeated kernel solves with a reusable, 
fast learned surrogate.

## Approach implemented

The nominal coupled PDE–ODE system is first stabilized with a backstepping boundary controller. Its gain kernels are 
computed by a numerical kernel solver and used to generate training data. A DeepONet then learns the map from the system 
parameters to these gain kernels.

During simulation, the controller evaluates the neural-operator approximation of the gain kernels and applies the 
resulting boundary input while the system parameters evolve through Markov modes. The notebook also evaluates a 
reference controller based on numerically computed kernels, solves the mode-probability evolution, and visualizes the 
PDE states, ODE state, control input, and switching probabilities.

## Repository contents

| File | Purpose |
| --- | --- |
| `s PDE_ODE.ipynb` | Complete workflow: kernel generation, DeepONet training and evaluation, Markov-chain simulation, finite-difference PDE–ODE solver, closed-loop control, and visualizations. |

When run, the notebook creates `Model/` for trained neural-operator artifacts and `img/` for generated figures.

## Requirements

Use Python 3.10 or newer with Jupyter and the following packages:

```bash
pip install jupyter numpy scipy matplotlib scikit-learn torch deepxde
```

DeepXDE is used by the notebook alongside PyTorch. CPU execution is supported; a compatible GPU-enabled PyTorch installation can reduce training time.

## Running the simulations

From this directory, launch Jupyter:

```bash
jupyter notebook
```

Open [`s PDE_ODE.ipynb`](s%20PDE_ODE.ipynb) and run all cells from top to bottom. The notebook generates reference kernels, 
prepares the training and test data, trains or evaluates the neural operator, then simulates the closed-loop system 
under Markov switching. Figures and model artifacts are saved in the directories created by the notebook.

The spatial and temporal resolution, switching rates, system parameters, and training configuration are defined near the 
beginning of the notebook. Increasing the grid resolution improves the reference simulation but increases the cost 
of numerical kernel computation.

## Reference

K. Lyu, U. Biccari, and J.-M. Wang, *Robust stabilization of hyperbolic PDE-ODE systems via Neural Operator-approximated gain kernels*, 2026. 
The manuscript is available on [arXiv:2508.03242](https://arxiv.org/abs/2508.03242). 

## Funding

This project has received funding from the European Research Council (ERC) under the European Union's Horizon 2030 
research and innovation programme (grant agreement No. 101096251, CoDeFeL). 
