\# GC-FID Hydrocarbon Degradation Kinetics



!\[Python](https://img.shields.io/badge/Python-3.8+-blue)

!\[License](https://img.shields.io/badge/License-MIT-green)

!\[Status](https://img.shields.io/badge/Status-Active-brightgreen)



A Python pipeline for modelling and comparing the degradation kinetics of phenanthrene (PAH) and hexadecane (alkane) using GC-FID time series data, anchored to published experimental trends from Gulumbe, Cravo-Laureau \& Duran (2025).



\---



\## Scientific Context



Phenanthrene is a three-ring polycyclic aromatic hydrocarbon (PAH) and a priority pollutant listed by the US EPA. Hexadecane is a straight-chain alkane and a major component of crude oil and diesel fuel. Comparing both compounds is scientifically valuable because they represent two distinct microbial degradation pathways:



| Compound | Type | Pathway | Expected behaviour |

|---|---|---|---|

| Hexadecane | Aliphatic alkane | Alkane monooxygenase (alkB) | Rapid degradation |

| Phenanthrene | Polycyclic aromatic | Dioxygenase activation | Slower, more complex |



The reference study used a synthetic marine Actinomycetota consortium comprising \*Rhodococcus\* sp. 1Y, \*Gordonia\* sp. BP1o, and two \*Janibacter indicus\* strains. The consortium degraded both compounds simultaneously at 50 mg/L each over 12 days, achieving 97% hexadecane removal and 63% phenanthrene removal.



This project reproduces and analyses the degradation kinetics from that study, and will be updated with original experimental GC-FID data from ongoing research at IPREM CNRS UMR 5254 (Université de Pau).



\---



\## Results



\### Hydrocarbon Degradation Over Time

!\[Degradation curves](figures/degradation\_curves.png)



Hexadecane decreases rapidly within the first three days, while phenanthrene declines more gradually — reflecting the expected difference between an aliphatic alkane and a recalcitrant aromatic PAH.



\### First-Order Kinetic Transformation

!\[First order kinetics](figures/first\_order\_kinetics.png)



The steeper slope for hexadecane confirms a significantly higher first-order degradation rate constant compared to phenanthrene.



\### Kinetic Parameters



| Compound | k (day⁻¹) | Half-life (days) | R² |

|---|---|---|---|

| Hexadecane | 0.256 | 2.71 | 0.658 |

| Phenanthrene | 0.085 | 8.18 | 0.987 |



> \*\*Note on hexadecane R²:\*\* The lower R² (0.658) reflects near-complete degradation by day 3, after which residual concentrations approach the detection limit. The first-order model captures the rapid initial phase but not the plateau. This is a scientifically expected limitation, not a modelling error.



\---



\## Project Objectives



1\. Organise GC-FID time series degradation data in a structured format

2\. Plot concentration decline over time for both compounds

3\. Fit first-order degradation kinetics using linear regression on ln(C/C₀)

4\. Estimate degradation rate constants (k, day⁻¹)

5\. Estimate compound half-lives (t½ = ln(2)/k)

6\. Compare aliphatic versus aromatic hydrocarbon degradation behaviour



\---



\## Methods



\*\*Core dependencies:\*\*



```python

pandas       # Structured data handling

numpy        # Numerical calculations

matplotlib   # Scientific visualisation

scipy        # Linear regression and kinetic fitting

```



\*\*First-order kinetics model:\*\*



```

C(t) = C₀ · e^(-kt)



Linearised: ln(C/C₀) = -kt



where:

&#x20; C(t)  = concentration at time t (mg/L)

&#x20; C₀    = initial concentration (mg/L)

&#x20; k     = first-order rate constant (day⁻¹)

&#x20; t½    = ln(2) / k

```



\---



\## Repository Structure



```

gcfid-hydrocarbon-degradation/

│

├── gcfid\_degradation\_kinetics.ipynb    # Main analysis notebook

├── kinetic\_summary.csv                 # Computed rate constants and half-lives

├── requirements.txt                    # Python dependencies

│

├── figures/

│   ├── degradation\_curves.png          # Concentration vs time plot

│   └── first\_order\_kinetics.png        # ln(C/C₀) linearisation plot

│

└── data/

&#x20;   └── synthetic\_gulumbe\_data.csv      # Reconstructed dataset

```



\---



\## Important Note on the Dataset



The dataset used in this project is \*\*reconstructed from published figures\*\* in Gulumbe et al. (2025). It is not the original raw GC-FID output. Values were approximated from graphical data to enable independent kinetic modelling.



This approach is standard practice when raw data is not publicly available and allows verification of reported degradation trends. The dataset will be replaced with original experimental GC-FID measurements once analysis of ongoing experiments at IPREM CNRS is complete.



\---



\## Reference



Gulumbe, B.H., Cravo-Laureau, C. \& Duran, R. (2025). Integrative genomic and transcriptomic analyses reveal marine Actinomycetota adaptations for hydrocarbon degradation. \*Environmental Technology \& Innovation\*, 40, 104361. https://doi.org/10.1016/j.etinno.2025.104361



\---



\## Author



\*\*Emma McCallum\*\*

Environmental Analytical Chemistry \& Microbiology

GREEN — IPREM CNRS UMR 5254

Université de Pau et des Pays de l'Adour



\[linkedin.com/in/ecmccallum](https://linkedin.com/in/ecmccallum) · \[github.com/ecmccallum](https://github.com/ecmccallum)



\---



\*This project is part of ongoing research into hydrocarbon bioremediation and microbial ecology at IPREM CNRS. It will be updated with experimental data as the research progresses.\*

