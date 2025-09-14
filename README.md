# Compound Lens Modeling

This repository contains code and resources for modeling compound gravitational lenses, with a focus on the analysis performed in the notebook `composite_F140W_5_2_original.ipynb`.

## Project Overview

The goal of this project is to model and analyze compound lens systems using astronomical imaging data. The main workflow involves preprocessing images, fitting lens models, and visualizing results.

## Getting Started

### Prerequisites

- Python 3.8+
- Jupyter Notebook
- Lenstronomy
- Required Python packages (see below)

### Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/<your-username>/Compound_Lens_Modeling.git
   cd Compound_Lens_Modeling
   ```

2. **Install dependencies:**
   You can install required packages using pip:
   ```bash
   pip install -r requirements.txt
   ```
   If `requirements.txt` is not present, manually install packages as needed (e.g., `numpy`, `matplotlib`, `astropy`, `scipy`, `lenstronomy`, `seaborn`, `joblib`, `h5py`, etc.).

### Data

Place your astronomical imaging data (e.g., FITS or HDF5 files) in the appropriate data directory. Update paths in the notebook as needed.

## Usage

### Main Notebook: `composite_F140W_5_2_original.ipynb`

This notebook demonstrates the full workflow for modeling a compound lens system using F140W filter data.

#### Workflow Steps:

1. **Open the notebook:**
   ```bash
   jupyter notebook composite_F140W_5_2_original.ipynb
   ```

2. **Data Import and Preprocessing:**
   - Loads imaging and PSF data from HDF5 files.
   - Applies coordinate transformations and visualizes image cutouts.
   - Identifies lens and source positions, and overlays them on the data.

3. **Masking and Supersampling:**
   - Creates masks for the lens and sources to focus the modeling region.
   - Generates supersampling masks for accurate flux modeling.

4. **Cosmology Setup:**
   - Defines cosmological parameters and computes angular diameter distances.
   - Calculates scaling factors for lensing deflections.

5. **Model Parameter Initialization:**
   - Sets up lens, lens light, and source models with initial guesses, bounds, and fixed parameters.
   - Supports multi-plane lensing and joint constraints between model components.

6. **Likelihood Functions:**
   - Implements custom likelihood functions for parameter constraints and image position matching.

7. **Fitting Sequence:**
   - Configures fitting routines (PSO, MCMC) and runs the optimization.
   - Saves and loads fitting results for further analysis.

8. **Output Analysis and Visualization:**
   - Extracts best-fit parameters and uncertainties.
   - Plots model fits, residuals, source reconstructions, and parameter distributions (corner plots).
   - Computes physical properties (e.g., NFW halo parameters, mass, concentration).

9. **Iterative Modeling:**
   - The notebook is structured to allow chaining: best-fit parameters from one run can be used to update inputs and run further chains for refinement.

### Additional Notebooks and Scripts

Other notebooks and scripts in the repository provide alternative modeling approaches, additional analysis, or utility functions. Refer to their headers and comments for usage instructions.

## Repository Structure

- `composite_F140W_5_2_original.ipynb` — Main analysis notebook.
- `data/` — Directory for input imaging data.
- `models/` — Lens model definitions and fitting routines.
- `utils/` — Utility scripts for preprocessing and visualization.
- `requirements.txt` — List of required Python packages.

## Contributing

Feel free to open issues or submit pull requests for improvements, bug fixes, or new features.

## License

This project is licensed under the MIT License.

## Contact

For questions or collaboration, please contact [nsahu.astro@gmail.com].

# Compound_Lens_Modeling

The notebooks provided here perform modeling and analyse the results.

How to perform compound lens modeling

1- Position modeling: Using only positions
    Notebook: Position_modelingF140W_mp.ipynb

3- Obtain Initial parameters for the Chameleon light profile.
    Notebook:Sersic_to_Chameleon_F140W_conversion_for_initial_parameters.ipynb

2- Extended Modeling (with fixed Distance Ratio)
   Substep1- Notebook: composite_F140W_5_2_original.ipynb
   Initiallt use optimizer PSO only untill you get the desired result/model

   Substep2- Notebook: composite_F140W_5_2.ipynb
   After getting a good enough model, run mcmc using best parameter from last chain.
   Stop when the parallel mcmc chains converge and provide a physical/sensible model.

3- Free Distance Ratio 
   Notebook: composite_F140W_5_2_DistRatio_3_Original.ipynb
   Add Beta (distance ratio parameter and it's bounds).
   When first chain provides physical result, run next chain with previous best fit.

   Notebook: composite_F140W_5_2_DistRatio_3.ipynb
   Run chain until convergence !

Save mcmc file and go infer cosmological parameters.

Notes: This code uses Lenstronomy Package version=1.12.0. Install Lenstronomy and other required packages from requirements.txt. Do not forget to change paths to yout input files.

Citations: if you are using data or code from this project please cite Sahu et al. (2025, https://arxiv.org/abs/2504.00656)



