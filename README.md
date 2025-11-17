Euler-Bernoulli Beam FEM Simulator

  This project implements a Finite Element Method (FEM) solver in Python to simulate the static deflection of an Euler-Bernoulli beam.
  The code calculates the nodal deflections and slopes for a beam under a point load with clamped boundary conditions.
  The implementation is based on the symmetric variational form of the beam equation, using piecewise cubic Hermite splines as basis functions.
  This approach ensures C1 continuity (continuous slopes) at the element nodes.

Problem Background
  The simulation solves the Euler-Bernoulli beam governing equation:
    (EIu'')'' = f
  Where:
    E is Young's Modulus
    I is the moment of intertia
    u is the beam's deflection
    f is the distributed load
  This project uses the symmetric variational (weak) form, derived from integration by parts.
  The specific problem solved in the notebook is for a fully clamped beam at both ends (x=0 and x=L), meaning the deflection u and slope u' are zero at both boundaries.

Features
  FEM Solver: Implements a complete FEM workflow:
    Calculates elemental stiffness matrices for cubic Hermite elements.
    Maps local element DOFs (deflection and slope) to the global system.
    Assembles the sparse global stiffness matrix (K_global) using scipy.sparse.
    Generates the global load vector (F_global) for a point load.
    Applies clamped boundary conditions by partitioning the system.
  Visualization: Plots the final beam deflection using Hermite shape functions to interpolate a smooth, continuous curve between nodes.
  Parameterized: Key parameters (beam length, number of elements, material properties, and load) can be easily modified in the main execution block of the notebook.

Repository Contents
  project-final.ipynb: The main Jupyter Notebook containing all Python code for the FEM solver, the specific simulation setup, and the final visualization.
  mini-project-topic-1.pdf: A project report outlining the problem statement, the numerical method (variational form, basis functions), the assembly process, and the final results.
  README.md: This file.

Dependencies
  The project is built in Python and relies on the following libraries:
    numpy
    scipy 
    matplotlib

How to Run
  1. Clone the repository:
    git clone [your-repository-url]
    cd euler-bernoulli-beam-simulation
  2. Install dependencies:
    pip install numpy scipy matplotlib jupyter
  3. Launch Jupyter Notebook:
    jupyter notebook
  4. Open project-final.ipynb in your browser.
  5. Run all cells in the notebook (Cell > Run All). The code will execute the simulation, print the matrices and nodal results to the console, and display the final deflection plot.

Example Result
  The notebook is pre-configured to solve the following problem:
  Beam: 3.0 m steel beam (E = 200 GPa)
  Cross-Section: 10cm x 10cm square
  Boundary Conditions: Clamped-clamped
  Load: 10 kN point load at the center (x = 1.5 m)
  Mesh: 6 cubic Hermite elements (7 nodes)
  This simulation correctly calculates the nodal deflections and slopes and produces a maximum deflection of 0.8437 mm at the center of the beam.
