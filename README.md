# Prediction of flow and polymeric stresses  in a viscoelastic turbulent channel flow using convolutional neural networks

This repository contains the code and supplementary material for the prediction of flow and polymeric stresses using a fully convolutional neural network (FCN). The viscoelastic turbulent channel flow simulation is performed using in-house code based on CaNS to generate the required dataset for training the FCN networks. The network models are implemented and trained using TensorFlow (an open-source software library developed by Google for ML applications), with the code written in Python.

## Publication

This work has been published in the xyz. If you use this code, extend it, or draw inspiration from its contents in your research, please consider citing it as follows:

```bibtex
@article{balasubramanian2024bursting, 
    title={Bursting bubble in an elastoviscoplastic medium},
    journal={arXiv Preprint arXiv:2404.14121},
    year={2024}
}
```

The article can be found at: 

[![](https://img.shields.io/badge/arXiv-4b4b4b?style=flat&logo=arxiv&link=https://arxiv.org/pdf/2404.14121.pdf)](https://arxiv.org/pdf/2404.14121.pdf)

## Background

The physics includes:
- Single-phase turbulent flow
- Viscoelastic rheology (FENE-P model)
- Channel geometry
- Log-conformation formulation for numerical stability
- Second-order central finite-difference scheme
- RK-3 for time-step integration
- Adam-Bashforth for conformation tensor evolution
- WENO-5 for advection terms in conformation tensor evolution equation
[![](https://img.shields.io/badge/Journal%20of%20Fluid%20Mechanics-10.1017/jfm.2021.789-blue)](https://doi.org/10.1017/jfm.2021.789)

## Implementation

### Key Files
- `01`: 

### Key Parameters
- `Bond`: Bond number (ratio of gravitational to surface tension forces)
- `J`: Dimensionless yield stress
- `Deb`: Deborah number (ratio of relaxation time to observation time)
- `B`: Solvent to total viscosity ratio
- `tmax`: Maximum simulation time
- `DT_MAX`: Maximum time step

### Numerical Methods
- Grid: Adaptive mesh refinement with levels from `LEVEL` (8) to `MAXlevel` (11)
- Time integration: Centered Navier-Stokes solver
- Interface tracking: Volume-of-Fluid method with tension
- Error tolerances:
  - Fraction error (fErr): 1e-3
  - Curvature error (KErr): 1e-4
  - Velocity error (VelErr): 1e-2
  - Vorticity error (OmegaErr): 1e-3

## Getting Started

### Prerequisites
- Install the [Basilisk framework](http://basilisk.fr/src/INSTALL)
- Ensure you have a C compiler with OpenMP support
- Python 3.x for post-processing

### Initial Configuration
The simulation requires an initial shape file that defines the bubble geometry:
- `Bo0.0010.dat`: Initial bubble shape for Bond number 0.001
- Place this file in the same directory as `burst_evp.c`
- For details of how this shape is obtained, please refer to repo: [VatsalSy/Bursting-Bubble-In-a-Viscoplastic-Medium](https://github.com/VatsalSy/Bursting-Bubble-In-a-Viscoplastic-Medium). 

### Running Simulations

1. Compile the code with OpenMP support:
```bash
# Compile the code
qcc -O2 -Wall -disable-dimensions -fopenmp burst_evp.c -o burst_evp -lm

# Set the number of OpenMP threads
export OMP_NUM_THREADS=4

# Run the executable with Plastocapillary (J) and Deborah (Deb) numbers
./burst_evp 1.0 0.5  # Example: J=1.0, Deb=0.5
```

## Outputs

### Output Files

The simulation generates several output files:
- `intermediate/snapshot-*.dat`: Simulation state at regular intervals
- `timestep.txt`: Time stepping information
- `log`: Contains kinetic energy and other diagnostic data
- `01_pp/png/`: Directory for PNG output files
- `01_pp/pdf/`: Directory for PDF output files

## Visualization and Post-processing

The repository includes supplementary materials:
- `02_videos/`: Contains 66 videos showing bubble dynamics
- `03_supplementary_plots/`: 79 plots analyzing various aspects
- `04_graphical_abstract/`: Visual summary of key findings


## Contact

If you need some additional data that might be of interest to you, please don't hesitate to contact us at:\
``Arivazhagan G B`` [![](https://img.shields.io/badge/Mail-blue?style=flat&logo=microsoftoutlook&link=mailto:argb@mech.kth.se)](mailto:argb@mech.kth.se) [![](https://img.shields.io/badge/Scholar-4b4b4b?style=flat&logo=googlescholar&link=https://scholar.google.com/citations?user=xyheRZ8AAAAJ&hl=en)](https://scholar.google.com/citations?user=xyheRZ8AAAAJ&hl=en) [![](https://img.shields.io/badge/LinkedIn-blue?style=flat&logo=linkedin&link=https://www.linkedin.com/in/arivazhagan-geetha-balasubramanian-648b8567/)](https://www.linkedin.com/in/arivazhagan-geetha-balasubramanian-648b8567/)\
``Vatsal Sanjay`` [![](https://img.shields.io/badge/Mail-blue?style=flat&logo=microsoftoutlook&link=mailto:vatsalsanjay@gmail.com)](mailto:vatsalsanjay@gmail.com) [![](https://img.shields.io/badge/Scholar-4b4b4b?style=flat&logo=googlescholar&link=https://scholar.google.com/citations?user=67aQviYAAAAJ&hl=en&oi=ao)](https://scholar.google.com/citations?user=67aQviYAAAAJ&hl=en&oi=ao) [![](https://img.shields.io/badge/LinkedIn-blue?style=flat&logo=linkedin&link=https://www.linkedin.com/in/vatsalsanjay/)](https://www.linkedin.com/in/vatsalsanjay/)\
``Outi Tammisola`` [![](https://img.shields.io/badge/Mail-blue?style=flat&logo=microsoftoutlook&link=mailto:outi@mech.kth.se)](mailto:outi@mech.kth.se) [![](https://img.shields.io/badge/Scholar-4b4b4b?style=flat&logo=googlescholar&link=https://scholar.google.com/citations?user=XSKb9YAAAAAJ&hl=en&oi=ao)](https://scholar.google.com/citations?user=XSKb9YAAAAAJ&hl=en&oi=ao) [![](https://img.shields.io/badge/LinkedIn-blue?style=flat&logo=linkedin&link=https://www.linkedin.com/in/outi-tammisola-8b2b6511/)](https://www.linkedin.com/in/outi-tammisola-8b2b6511/)
