# Prediction of flow and polymeric stresses  in a viscoelastic turbulent channel flow using convolutional neural networks

This repository contains the code and supplementary material for the prediction of flow and polymeric stresses using a fully convolutional neural network (FCN). The viscoelastic turbulent channel flow simulation is performed using in-house code based on CaNS to generate the required dataset for training the FCN networks. The network models are implemented and trained using TensorFlow (an open-source software library developed by Google for ML applications), with the code written in Python.

## Publication

This work has been published in the Journal of Fluid Mechanics. If you use the data or code, or draw inspiration from the present work in your research, please consider citing it as follows:

```bibtex
@article{balasubramanian2025prediction,
  title={Prediction of flow and polymeric stresses in a viscoelastic turbulent channel flow using convolutional neural networks},
  author={Balasubramanian, Arivazhagan G and Vinuesa, Ricardo and Tammisola, Outi},
  journal={Journal of Fluid Mechanics},
  volume={1009},
  pages={A36},
  year={2025},
  publisher={Cambridge University Press}
}
```

The article can be found at: 
[![](https://img.shields.io/badge/Journal%20of%20Fluid%20Mechanics-10.1017/jfm.2025.240-blue)](https://doi.org/10.1017/jfm.2025.240)
[![](https://img.shields.io/badge/arXiv-4b4b4b?style=flat&logo=arxiv&link=https://arxiv.org/pdf/2404.14121.pdf)](https://arxiv.org/pdf/2404.14121.pdf)

## Background

The physics includes:
- Single-phase turbulent flow
- Viscoelastic rheology (FENE-P model)
- Channel geometry
- Log-conformation formulation for numerical stability

## Implementation

### Key Files
- `01_codes`: Train and Prediction scripts with corresponding tags added to file names. Also, contains the `config` file that outlines the parameter setup required for training/prediction of each case
- `02_weights`: Contains FCN model's weights for each prediction type at different target wall-normal positions. Contains about 15 hdf5 files amounting to roughly 244 MiB
- `03_graphical_abstract`: Outlining the visual summary of the work

### Key Parameters
- $Wi$: Weissenberg number (ratio of elastic to viscous forces)
- $Re_b$: Bulk-Reynolds number (ratio of inertial to viscous forces)
- $Re_\tau$: Friction Reynolds number (with friction velocity scale)

In this work, we consider $Wi = 8$ (which corresponds to a low-drag reduction regime) at $Re_b = 2800$ with Newtonian $Re_\tau$ corresponding to 180.

### Numerical Methods
- Grid: Uniform Cartesian grid
- Time integration: Third order Runge-Kutta (RK-3)
- Discretization: Second-order central finite-difference scheme
- Conformation tensor: Log-conformation formulation for numerical stability
- Conformation tensor: Adam-Bashforth for conformation tensor evolution
- Conformation tensor: WENO-5 for advection terms in conformation tensor evolution equation

For more details, please check the foll. articles:
[![](https://img.shields.io/badge/Journal%20of%20Fluid%20Mechanics-10.1017/jfm.2021.789-blue)](https://doi.org/10.1017/jfm.2021.789)
[![](https://img.shields.io/badge/Journal%20of%20Fluid%20Mechanics-10.1017/jfm.2018.591-blue)](https://doi.org/10.1017/jfm.2018.591)

## Getting Started

### Prerequisites
- Install [TensorFlow](https://www.tensorflow.org)
- Ensure you can run Python 3.x codes and can import tensorflow [Recommended to use GPUs]

## Outputs

### Output Files

The training and prediction script generate each of the below text file, respectively:
- `train.txt`: Contains model summary and loss incurred at each epoch
- `predict.txt`: Contains model summary and field sizes of the predictions

Apart from this, the code also creates several hidden folders:
- `.log`: Contains the model check-points
- `.epoch_log`: Contains details about the training curves
- `.saved_model`: Contains the FCN model with weights
- `.predictions`: Contains the predicted fields stored in `.npz` files


## Contact

If you need some additional data that might be of interest to you, please don't hesitate to contact us at:\
``Arivazhagan G B`` [![](https://img.shields.io/badge/Mail-blue?style=flat&logo=microsoftoutlook&link=mailto:argb@mech.kth.se)](mailto:argb@mech.kth.se) [![](https://img.shields.io/badge/Scholar-4b4b4b?style=flat&logo=googlescholar&link=https://scholar.google.com/citations?user=xyheRZ8AAAAJ&hl=en)](https://scholar.google.com/citations?user=xyheRZ8AAAAJ&hl=en) [![](https://img.shields.io/badge/LinkedIn-blue?style=flat&logo=linkedin&link=https://www.linkedin.com/in/arivazhagan-geetha-balasubramanian-648b8567/)](https://www.linkedin.com/in/arivazhagan-geetha-balasubramanian-648b8567/)\
``Ricardo Vinuesa`` [![](https://img.shields.io/badge/Mail-blue?style=flat&logo=microsoftoutlook&link=mailto:rvinuesa@mech.kth.se)](mailto:rvinuesa@mech.kth.se) [![](https://img.shields.io/badge/Scholar-4b4b4b?style=flat&logo=googlescholar&link=https://scholar.google.com/citations?user=UbyF8_oAAAAJ&hl=en&oi=ao)](https://scholar.google.com/citations?user=UbyF8_oAAAAJ&hl=en&oi=ao) [![](https://img.shields.io/badge/LinkedIn-blue?style=flat&logo=linkedin&link=https://www.linkedin.com/in/ricardo-vinuesa-91823918/)](https://www.linkedin.com/in/ricardo-vinuesa-91823918/)\
``Outi Tammisola`` [![](https://img.shields.io/badge/Mail-blue?style=flat&logo=microsoftoutlook&link=mailto:outi@mech.kth.se)](mailto:outi@mech.kth.se) [![](https://img.shields.io/badge/Scholar-4b4b4b?style=flat&logo=googlescholar&link=https://scholar.google.com/citations?user=XSKb9YAAAAAJ&hl=en&oi=ao)](https://scholar.google.com/citations?user=XSKb9YAAAAAJ&hl=en&oi=ao) [![](https://img.shields.io/badge/LinkedIn-blue?style=flat&logo=linkedin&link=https://www.linkedin.com/in/outi-tammisola-8b2b6511/)](https://www.linkedin.com/in/outi-tammisola-8b2b6511/)
