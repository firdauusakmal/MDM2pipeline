# MDM2 Inhibitor Discovery Pipeline

This repository contains a comprehensive pipeline for identifying potential MDM2 inhibitors using machine learning (ML) and molecular simulations. It integrates data preprocessing, virtual screening, docking studies, and molecular dynamics simulations to predict and evaluate bioactive compounds.

## Overview

### Key Features:
1. **Training Dataset Preparation**:
   - Curated a diverse dataset of known MDM2 inhibitors with IC50 potency from ChEMBL.
   - Utilized Pandas for data cleaning and preprocessing.
   - Split the dataset into training (90%) and testing (10%) using molecular scaffold splitting.

2. **Data Standardization and Selective Cleaning**:
   - Standardized SMILES representation using MolVS and RDKit.
   - Implemented a selective cleaning (SC) pipeline to prioritize the highest bioactivity for each molecule.

3. **Machine Learning Pipeline**:
   - Trained multiple ML models using Scikit-learn and ChemProp.
   - Evaluated and optimized models using hyperparameter tuning.
   - Predicted pIC50 values for a repurposing dataset of over 24,000 drug molecules.

4. **Structure-Based Virtual Screening**:
   - Docked compounds to the MDM2 protein using MOE 2022.02.
   - Conducted re-docking analysis and off-target docking for validation.

5. **Molecular Dynamics Simulations**:
   - Explored stability and interactions of MDM2-hit compounds using MD simulations in MOE.

6. **ONIOM Simulations**:
   - Analyzed dynamic interactions and binding energies of hit compounds at multiple computational levels.

## Repository Contents

- **Data Preparation**:
  - Scripts for dataset collection, cleaning, and standardization.
  - SC pipeline implementation using Pandas and pandasql.

- **Machine Learning**:
  - ML model training and evaluation scripts.
  - ChemProp integration for deep learning.

- **Docking and Simulations**:
  - Scripts for docking studies and molecular dynamics simulations.
  - Conversion of SMILES to SDF format using RDKit.

- **Supporting Information**:
  - Detailed protocols and algorithms in Supporting Information S2 and S3.

## How to Use

1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/your-repository-name.git
   ```
2. Install the required dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Follow the step-by-step instructions in the Jupyter Notebooks for data preparation, ML training, and docking studies.

## Tools and Libraries

- **Data Processing**: Pandas, pandasql, RDKit, MolVS
- **Machine Learning**: Scikit-learn, ChemProp
- **Docking and Simulations**: MOE 2022.02, Autodock Vina, GOLD
- **Molecular Dynamics**: MOE with AMBER10 forcefield

## License
This project is licensed under the [MIT License](LICENSE). Feel free to use, modify, and distribute the code as per the terms of the license.

## Acknowledgments

- ChEMBL, PubChem, DrugCentral, and DrugBank for providing bioactive molecule datasets.
- Developers of Scikit-learn, RDKit, ChemProp, and MOE for their excellent tools and frameworks.

## Contact
For questions or collaborations, please contact [Your Name](mailto:your.email@example.com).

