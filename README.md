\# GC-FID Hydrocarbon Degradation Kinetics



A Python-based analysis pipeline for modeling and comparing hydrocarbon 

degradation kinetics using GC-FID time-series data. This project reproduces 

and analyses degradation trends for an aliphatic alkane (hexadecane) and a 

polycyclic aromatic hydrocarbon (phenanthrene), based on published 

experimental data from Gulumbe, Cravo-Laureau \& Duran (2025).



\---



\## Project Overview



This repository demonstrates an end-to-end analytical chemistry workflow:



\- Structured data handling of GC-FID time-series measurements

\- Scientific visualisation of degradation dynamics

\- First-order kinetic modelling

\- Parameter estimation — rate constants and half-lives

\- Interpretation of differential biodegradation behaviour



The goal is to simulate a realistic environmental chemistry data pipeline 

that can be extended directly to real experimental GC-FID datasets.



\---



\## Scientific Context



Hydrocarbon degradation depends strongly on molecular structure.



| Compound | Class | Degradation pathway | Expected rate |

|---|---|---|---|

| Hexadecane | Linear alkane (C16) | Alkane monooxygenase (alkB) | Rapid |

| Phenanthrene | 3-ring PAH | Dioxygenase activation | Slower |



The reference study (Gulumbe et al., 2025) used a synthetic marine 

\*Actinomycetota\* consortium comprising \*Rhodococcus\* sp. 1Y, \*Gordonia\* sp. 

BP1o, and two \*Janibacter indicus\* strains isolated from hydrocarbon-

contaminated marine sediments. Both compounds were supplied at \*\*50 mg/L\*\* 

as sole carbon sources.



\*\*Published outcomes over 12 days:\*\*

\- Hexadecane: \~97% degradation (residual 2.76%)

\- Phenanthrene: \~63% degradation (residual 36.56%)



This project reconstructs those degradation trends and applies first-order 

kinetic analysis to quantify and compare the two degradation pathways.



\---



\## Results



\### Degradation Dynamics



!\[Degradation curves](figures/degradation\_curves.png)



Hexadecane shows rapid early depletion within the first three days, 

while phenanthrene decreases more gradually — consistent with the 

metabolic complexity of aromatic ring activation compared to aliphatic 

chain oxidation.



\### First-Order Kinetic Transformation



!\[First order kinetics](figures/first\_order\_kinetics.png)



Linearisation of ln(C/C₀) versus time highlights the steeper slope for 

hexadecane, confirming a significantly higher degradation rate constant 

relative to phenanthrene.



\### Estimated Kinetic Parameters



| Compound | k (day⁻¹) | Half-life (days) | R² |

|---|---|---|---|

| Hexadecane | 0.256 | 2.71 | 0.658 |

| Phenanthrene | 0.085 | 8.18 | 0.987 |



> \*\*Note on hexadecane R²:\*\* The lower R² (0.658) reflects near-complete 

> degradation by day 3, after which residual concentrations approach the 

> detection limit. The first-order model captures the rapid initial phase 

> accurately but cannot describe the subsequent plateau. This is a 

> scientifically expected limitation of applying a single-phase model to 

> biphasic degradation data — not a modelling error.



\---



\## Methods



\*\*Python stack:\*\*



```python

pandas      # Structured data handling

numpy       # Numerical calculations

matplotlib  # Scientific visualisation

scipy       # Linear regression and kinetic fitting

```



\*\*First-order degradation model:\*\*



```

C(t) = C₀ · e^(−kt)



Linearised form used for fitting:

ln(C / C₀) = −kt



Derived parameter:

t½ = ln(2) / k



where:

&#x20; C(t)  = concentration at time t (mg/L)

&#x20; C₀    = initial concentration (mg/L)

&#x20; k     = first-order rate constant (day⁻¹)

&#x20; t½    = half-life (days)

```



Linear regression is applied to ln(C/C₀) versus time using 

`scipy.stats.linregress` to estimate k and assess goodness of fit (R²).



\---



\## Repository Structure



```

gcfid-hydrocarbon-degradation/

│

├── gcfid\_degradation\_kinetics.ipynb    # Main analysis notebook

├── kinetic\_summary.csv                 # Computed kinetic parameters

├── requirements.txt                    # Python dependencies

│

├── figures/

│   ├── degradation\_curves.png          # Concentration vs time

│   └── first\_order\_kinetics.png        # ln(C/C₀) linearisation

│

└── data/

&#x20;   └── synthetic\_gulumbe\_data.csv      # Reconstructed dataset

```



\---



\## Data Note



The dataset used here is \*\*reconstructed from published figures\*\* in 

Gulumbe et al. (2025) and is not raw GC-FID instrument output.



This is intentional. The objective is to demonstrate:



\- Data reconstruction from peer-reviewed literature

\- Reproducible analysis pipelines applicable to real instrument data

\- Kinetic modelling under realistic experimental constraints



\*\*The project will be updated with real experimental GC-FID measurements\*\* 

from ongoing work at IPREM CNRS UMR 5254 once analysis is complete. The 

pipeline is designed to accept real data with no structural changes.



\---



\## Why This Project Matters



This is not just curve-fitting. It demonstrates:



\- Translation of experimental chemistry into reproducible computational workflows

\- Understanding of hydrocarbon biodegradation mechanisms at the molecular level

\- Handling of imperfect real-world data with transparent methodological notes

\- Clear scientific communication of quantitative results



These skills are directly transferable to roles in environmental data 

analysis, analytical chemistry, oil and gas environmental monitoring, 

and sustainability consulting.



\---



\## Reference



Gulumbe, B.H., Cravo-Laureau, C. \& Duran, R. (2025). Integrative genomic 

and transcriptomic analyses reveal marine \*Actinomycetota\* adaptations for 

hydrocarbon degradation. \*Environmental Technology \& Innovation\*, \*\*40\*\*, 

104361\. https://doi.org/10.1016/j.etinno.2025.104361



\---



\## Author



\*\*Emma McCallum\*\*  

Environmental Analytical Chemistry \& Microbiology  

GREEN Graduate Programme — IPREM CNRS UMR 5254  

Université de Pau et des Pays de l'Adour, France



\[!\[LinkedIn](https://img.shields.io/badge/LinkedIn-ecmccallum-blue?logo=linkedin)](https://linkedin.com/in/ecmccallum)

\[!\[GitHub](https://img.shields.io/badge/GitHub-ecmccallum-black?logo=github)](https://github.com/ecmccallum)



\---



\*Part of ongoing research into hydrocarbon bioremediation and microbial 

ecology at IPREM CNRS. This repository will be updated with experimental 

data as the research progresses.\*

