# Boxes-on-Shelves
# Multi-Objective Box-on-Shelves Optimization using Evolutionary Algorithms

This project applies a **Multi-Objective Genetic Algorithm (MOGA)** to solve a 3D bin packing problem: placing various products (boxes) on shelves inside bays with the aim of optimizing three conflicting objectives:

1. **Minimize the number of shelves used**
2. **Minimize weight imbalance across shelves**
3. **Minimize height overhang**

The algorithm uses the DEAP evolutionary framework to search for Pareto-optimal solutions under spatial and stacking constraints.

## Dataset Files

This project expects the following input files in the same directory:

- `baytp1.txt` and `baytp2.txt`: Describe bay dimensions and available vertical space.
- `shelves.txt`: Contains shelf thickness and gap configurations.
- `products.txt`: Contains product dimensions and quantities to be packed.

> Note: Only the first 100 product instances are used for computational tractability.

## ⚙️ Features

- Reads and parses shelf, bay, and product information.
- MOGA Implementation: Uses the DEAP library to implement NSGA-II, a multi-objective genetic algorithm. It optimizes three objectives:
     - Minimize the number of shelves (unique bay-shelf pairs).
     - Minimize weight imbalance (variance of shelf volumes, calculated as product length × width × height).
     - Minimize height overhang (difference between shelf position and the maximum product height on that shelf). The MOGA runs with a population size of 50, 100 generations, crossover probability of 0.8, and mutation probability of 0.2. Constraints like no-overlap, shelf gaps (top=15, left/right=10, inter=10), and bay dimensions are enforced using a bottom-left packing heuristic.

## Output

The algorithm generates:

- pareto_tp1.png: 3D scatter plot of the Pareto front for baytp1.
- pareto_tp2.png: 3D scatter plot of the Pareto front for baytp2.
- shelf_layout_tp1.png: 2D layout of Bay 248 in baytp1, showing product placement.
- shelf_layout_tp2.png: 2D layout of Bay 299 in baytp2, showing product placement.
These outputs are already included in the repository for reference, so you can view them without running the code.

##  How to Run

1. Install dependencies (DEAP and matplotlib):

    ```bash
    pip install deap matplotlib
    ```

2. Place `baytp1.txt`, `baytp2.txt`, `shelves.txt`, and `products.txt` in the project folder.

3. Run the script (in Jupyter Notebook)




## Requirements

- Jupyter Notebook
- DEAP (Distributed Evolutionary Algorithms in Python)
- NumPy
- Matplotlib


