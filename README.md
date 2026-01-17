This repository contains the machine-learning pipeline used in the study:

Machine-learning prediction of antimicrobial peptides active against Klebsiella pneumoniae using physicochemical descriptors and ensemble classification
# AMPs-against-KP
The project focuses on identifying and interpreting antimicrobial peptides (AMPs) active against clinically important Gram-negative pathogens, with an emphasis on biological interpretability and real-world relevance.

*Clinically Significant Pathogens:
![image](https://github.com/user-attachments/assets/9d314034-8749-4d36-9a34-cbb8f335fb37)
These three bacteria are major causes of hospital- and community-acquired infections, including pneumonia, urinary tract infections, bloodstream infections, and wound infections.

Multi-Drug Resistance Concerns:

They are known for their increasing resistance to multiple antibiotics, making treatment difficult and highlighting the urgent need for new therapeutic options like AMPs.

Gram-Negative Bacteria:

All three are Gram-negative bacteria, which have a unique outer membrane structure that often makes them more resistant to antibiotics. Studying AMPs against these bacteria is crucial because they pose a significant challenge in antimicrobial therapy.

![image](https://github.com/user-attachments/assets/c3959db5-7060-4cac-ab3d-885486d2f0c2)
![image](https://github.com/user-attachments/assets/bae3975a-cd7f-4f96-9da1-0b4c6e24fd20)

Dataset Overview

Active peptides: 138 experimentally validated AMPs active against Klebsiella pneumoniae

Inactive peptides: 373 non-AMP peptide or protein fragments

Class distribution: Intentionally imbalanced to reflect real-world AMP availability

The dataset was curated from public databases and literature, prioritizing pathogen-specific and experimentally validated peptides rather than synthetic or purely predicted sequences.

📅 Description of Peptide Feature Calculations
Feature	Description
###Length	Number of amino acid residues in the peptide sequence.
###Charge	Net charge of the peptide, calculated by counting positively charged residues (Lysine, Arginine, Histidine) minus negatively charged residues (Aspartic acid, Glutamic acid).
###Hydrophobicity	Sum of hydrophobic residues (A, V, I, L, M, F, W, P) in the sequence based on Kyte-Doolittle scale.
###Molecular Weight	Total molecular weight of the peptide calculated from the amino acid sequence using Biopython’s molecular weight function.
###Number of Cysteines	Count of cysteine residues (C) in the peptide sequence.
###Number of Disulfide Bridges	Estimated as the integer division of cysteine count by 2, assuming cysteines form pairs to make disulfide bonds.
###Isoelectric Point (pI)	Simplified estimate of the peptide’s isoelectric point based on counts of acidic (D, E) and basic (K, R, H) residues weighted by their pKa values.
###Amino Acid Composition	Percentage of each standard amino acid (A, C, D, E, F, G, H, I, K, L, M, N, P, Q, R, S, T, V, W, Y) within the peptide.
###Secondary Structure Features	Counts of residues associated with secondary structures: Helix-forming (A, L, I, V, M, F, Y, W), Sheet-forming (F, Y, W), and Turn-forming (G, P). Flexibility is the proportion of ###helix residues to total length.

Example : 

![image](https://github.com/user-attachments/assets/b922e820-c8cf-4996-a0c9-503d5f8e9d25)

 Machine-Learning Framework
Three Modeling Techniques Used

This study applies three complementary machine-learning strategies:

Tree-based ensemble models

Random Forest

Gradient Boosting

AdaBoost
These models capture nonlinear relationships between physicochemical descriptors and AMP activity.

Kernel-based model

Support Vector Machine (RBF kernel)
Used as a strong baseline for nonlinear classification.

Boosted decision trees

XGBoost
Evaluated for performance comparison and robustness.

Model Evaluation

Models were evaluated using:

Accuracy

Precision

Sensitivity (Recall)

Specificity

F1 score

Matthews Correlation Coefficient (MCC)

ROC-AUC

PR-AUC (emphasized due to data imbalance)

Performance was assessed using stratified cross-validation and an independent external validation set consisting of experimentally confirmed anti-K. pneumoniae peptides.

Interpretability and Biological Insight

Random Forest was selected as the primary model due to:

Stable performance across folds

Strong PR-AUC under imbalanced conditions

Ability to model nonlinear interactions

High interpretability via:

Gini importance

Permutation importance

SHAP analysis

These features support biological interpretation and downstream AMP design, which are central goals of this study.

Reproducibility

Platform: Google Colab

Language: Python

Libraries: pandas, scikit-learn, Biopython, XGBoost, SHAP

Main notebook:

KP_imbalance.ipynb





