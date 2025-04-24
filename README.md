# MDM2 Inhibitor Discovery Pipeline

This repository contains a comprehensive pipeline for identifying potential MDM2 inhibitors using machine learning (ML) and molecular simulations. It integrates data preprocessing, virtual screening, docking studies, and molecular dynamics simulations to predict and evaluate bioactive compounds.

## Overview

1. **Training Dataset Preparation (D1_prep)**
2. **Machine Learning Selection & Optimization (ML_opt)**:
3. **Repurposing Dataset Preparation (D2_prep)**:
4. **ML-Based Virtual Screening (MLVS)**:
5. **Structure-Based Virtual Screening (SBVS)**:
   - Docking score results from molecular docking simulations of D2 compounds against MDM2 protein.
6. **Redocking Analysis (redocking)**:   
7. **Molecular Dynamics Simulations (md)**:
   - MePPEP (MP), Atorvastatin (AT), and Otenabant (OT) QM/MM-optimized structures for MD inputs.

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
