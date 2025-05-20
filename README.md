# Data Analysis: Linear Mixed Models in Python and R

This repository contains two notebooks demonstrating how to fit linear mixed models using both Python and R.

## Contents
- `Modelos_Lineales_Mixtos_en_Python.ipynb` – examples in Python with `statsmodels` and visualization libraries.
- `Modelos_Lineales_Mixtos_en_R (1).ipynb` – examples in R using packages such as `lme4`, `glmmTMB` and others.

## Installation
1. Clone this repository.
2. Install the Python dependencies with:
   ```bash
   pip install -r requirements.txt
   ```
3. Install the R dependencies by running the following in an R console:
   ```R
   install.packages(c(
       "lme4", "nlme", "glmmTMB", "emmeans",
       "multcomp", "MASS", "ggplot2", "patchwork", "TMB"
   ))
   ```
   These are the packages used in the R notebook.

## Running the notebooks
Launch Jupyter Notebook or JupyterLab in the repository directory:
```bash
jupyter notebook
```
Open the notebook you want to explore and execute the cells sequentially.

### Using the devcontainer
The `.devcontainer` folder provides a configuration to run the notebooks in a preconfigured Docker environment. If you use VS Code with the Remote Containers extension, the container will build automatically and start Jupyter on port 8888.
