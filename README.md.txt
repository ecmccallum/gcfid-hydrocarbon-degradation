# GC-FID Hydrocarbon Degradation Kinetics

This project analyses hydrocarbon degradation kinetics using a GC-FID-style time series dataset for phenanthrene and hexadecane.

The workflow is based on the experimental design described in Gulumbe, Cravo-Laureau & Duran (2025), where a marine Actinomycetota consortium degraded a binary hydrocarbon mixture containing phenanthrene and hexadecane at 50 mg/L each.

## Scientific context

Phenanthrene is a polycyclic aromatic hydrocarbon (PAH), while hexadecane is a straight-chain alkane. Comparing these two compounds is useful because they represent two different hydrocarbon degradation pathways: aromatic hydrocarbon degradation and aliphatic alkane degradation. Alkanes are typically degraded rapidly via alkane monooxygenase systems, while PAHs require more complex enzymatic activation and tend to degrade more slowly.

In the published study, hexadecane was degraded rapidly, while phenanthrene showed slower degradation. This project uses a dataset anchored to the reported degradation trends from the paper. The dataset will later be expanded with experimental GC-FID measurements from my own experimental work.

## Project objective

The goal is to build a reusable Python pipeline for:

1. Organising GC-FID degradation data
2. Plotting concentration decline over time
3. Fitting first-order degradation kinetics
4. Estimating degradation rate constants
5. Estimating compound half-lives
6. Comparing degradation behaviour between an alkane and a PAH

## Methods

The analysis uses:

- pandas for structured data handling
- numpy for numerical calculations
- matplotlib for visualization
- scipy for linear regression and kinetic fitting

## Files

- 'gcfid_degradation_kinetics.ipynb': main analysis notebook
- 'data/synthetic_gulumbe_placeholder_data.csv': degradation dataset
- 'figures/degradation_curves.png': degradation kinetics visualisation
- 'requirements.txt': dependencies

## Important note on the dataset

Data source clarification

The dataset used in this project is reconstructed from published figures in Gulumbe, Cravo-Laureau and Duran (2025). It is not the original raw GC-FID dataset. Values were extracted and approximated from graphical data to enable kinetic modeling.

This approach is commonly used when raw data is not publicly available and allows independent verification of reported degradation trends.

## Relevance

This project demonstrates applied data analysis for environmental chemistry, hydrocarbon biodegradation, and analytical chemistry workflows. It is relevant to environmental monitoring, bioremediation, petroleum contamination studies, and analytical laboratory data processing.