# cv-simulation-pipeline

A finite-difference cyclic voltammetry (CV) simulator in Python, validated against MECSim, with automated tooling to generate MECSim inputs and run it in Docker. Built for the SALT Group at UC Berkeley.

## Overview

This project simulates cyclic voltammograms by solving Fick's second law with Butler-Volmer electrode kinetics, with optional coupled chemical steps (EC mechanism). To check correctness, the pipeline also generates MECSim input files and runs MECSim in a containerized workflow, so Python and MECSim results can be compared directly.

## Features

- **Finite-difference solver** for diffusion (Fick's second law) with Butler-Volmer boundary conditions
- **EC mechanism support** (electrochemical step followed by a homogeneous chemical step)
- **MECSim bridge:** generates `Master.inp` files from the same parameters used by the Python solver
- **Dockerized MECSim workflow**, including on Apple Silicon
- [Optional: temperature dependence via Nernst/Arrhenius corrections, if it's in the current version]

## Validation

Python results were compared against MECSim for two cases:

| Case | Agreement with MECSim |
|---|---|
| Ferrocene (reversible) | ~4-5% |
| EC mechanism | ~4-5% |


**Sign convention:** the Python solver and MECSim use different current sign conventions.


## Setup

```bash
git clone [repo-url]
cd [repo-name]
pip install -r requirements.txt
```

**Run a simulation:**
```bash
python [script].py [args]
```

**Run MECSim comparison (requires Docker):**
```bash
[docker build/run command or helper script]
```

## Usage Example

```python
[short snippet: define parameters (E0, ks, alpha, D, C0, scan rate), run the solver, plot the voltammogram]
```


## References

- Bard & Faulkner, *Electrochemical Methods: Fundamentals and Applications*, 2nd ed.


## Acknowledgments

Developed as part of research with the SALT Group at UC Berkeley.
## Author

Kurtis Bauman, UC Berkeley (EECS & Nuclear Engineering)
