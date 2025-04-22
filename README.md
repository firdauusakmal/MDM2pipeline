# MDM2 Inhibitor Discovery Pipeline

This repository contains a comprehensive pipeline for identifying potential MDM2 inhibitors using machine learning (ML) and molecular simulations. It integrates data preprocessing, virtual screening, docking studies, and molecular dynamics simulations to predict and evaluate bioactive compounds.

## Overview

1. **Training Dataset Preparation (D1_prep)**:
   - Collected known MDM2 inhibitors with IC50 values from the ChEMBL database to form the D1 dataset.
   - Used Pandas 2.1.4 in Python 3.11.4 for data cleaning and preprocessing.
   - Applied molecular scaffold splitting, setting aside 10% as an final testing set (D1_testing).
   - Standardized molecular SMILES using MolVS under the RDKit framework.
   - Applied the Selective Cleaning (SC) pipeline by:
     1. Grouping bioactivities by assay procedure (descending order of occurrence)
     2. Sorting values within each group
     3. Retaining the highest pIC50 value per molecule while removing redundant entries.

2. **Machine Learning Selection & Optimization (ML_opt)**:
   - Feature Extraction: Generated molecular fingerprints from SMILES.
   - Data Splitting: Split into training and validation sets (80:20 ratio).
   - Model Training:
     1. Trained multiple ML models via scikit-learn 1.4.0, including: kNN, Decision Tree, Random Forest, AdaBoost, XGBoost, Gradient Boosting, Histogram Gradient Boosting, SGD, and MLP.
     2. Trained deep learning models using ChemProp 1.6.1 (GCNN-based) on same data.
     3. Hyperparameter Tuning: Applied for all models, including epochs and Bayesian optimization.
   - Final Evaluation: Tested top models on D1_testing to assess generalization performance.
  
3. **Repurposing Dataset Preparation (D2_prep)**:
   - Collected compounds with therapeutic indications from: ChEMBL, PubChem, DrugCentral, and DrugBank.
   - Formed D2 dataset from curated bioactive libraries.
   - Standardized molecules using the same SMILES protocol as D1.

4. **ML-Based Virtual Screening (MLVS)**:
   - Predicted pIC50 values of D2 compounds using the best-performing ML model.
   - Selected top-ranked compounds based on predicted potency.

5. **Structure-Based Virtual Screening (SBVS)**:
   - Used MDM2 crystal structure (PDB ID: 6Q9L, 1.13 Å) from RCSB.
   - Protein preprocessing: removed water, adjusted protonation (pH 7.4).
   - Performed docking using MOE 2022.02, with:
     1. Triangle Matcher placement
     2. Fixed receptor conformation
   - Docked D2 compounds into the p53-binding site of MDM2.
   - Benchmarked docking results against known MDM2 inhibitors to select top candidates (H1 hits).

6. **Redocking Analysis (redocking)**:
   - Redocked H1 compounds to:
     1. Primary (p1) p53-binding pocket
     2. Secondary (p2) site detected in MOE.
   - Performed consensus docking using: MOE, AutoDock Vina, and GOLD.Validated site preference and ranking consistency.
   - Also docked H1 compounds against (off-target affinities):
     1. BCL2 (PDB ID: 8HTS, 1.25 Å)
     2. MDM4/MDMX (PDB ID: 6Q9Y, 1.2 Å)
   - Final hits (H2 compounds) were shortlisted based on docking outcomes.

7. **ONIOM Simulations (oniom)**:
   - Refined MDM2–H2 complexes using ONIOM in Gaussian 16 via MOE interface.
   - System partition:
     1. High-level (QM): Ligand layer using ωB97X-D/6-31G*.
     2. Low-level (MM): Receptor with AMBER10 force field.
   - Analyzed optimized geometries and binding modes
   - Calculated non-covalent interaction energies using Extended Hückel Theory (EHT) in MOE.
   
8. **Molecular Dynamics Simulations (md)**:
   - Simulated MDM2–H2 complexes using MOE’s MD module.
   - Applied Nosé–Poincaré–Andersen (NPA) integrator.
   - Simulation environment:
     1. Solvated in KCl 0.15 M, cell size: 50.5 × 40 × 40 Å³
     2. Density: ρ = 1.022 g/cm³.
   - Simulation stages: Heating (100 ps) → NVT (100 ps) → NPT (200 ps) at 310 K, 101.3 kPa.
   - Production run: 100 ns at 2 fs timestep to observe dynamic binding behavior.

## How to Use

1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/your-repository-name.git
   ```
2. Follow the step-by-step instructions in the Jupyter Notebooks for data preparation, ML training, and docking studies.

## Tools and Libraries

- **Data Processing**: Pandas, pandasql, RDKit, MolVS
- **Machine Learning**: Scikit-learn, ChemProp
- **Docking and Simulations**: MOE 2022.02, Autodock Vina, GOLD
- **Molecular Dynamics**: MOE with AMBER10 forcefield

## License
This project is licensed under the [Apache License 2.0](LICENSE). Feel free to use, modify, and distribute the code as per the terms of the license.

## Acknowledgments

- ChEMBL, PubChem, DrugCentral, and DrugBank for providing bioactive molecule datasets.
- Developers of Scikit-learn, RDKit, ChemProp, and MOE for their excellent tools and frameworks.

## Contact
For questions or collaborations, please send your mail to firdaus.akmal@u.nus.edu.
