# BRCA Wide × Deep Network

## Project Overview

This project implements a **Wide × Deep Neural Network** using the **BRCA Multi-Omics (TCGA)** dataset to classify **breast cancer molecular subtypes** — *Luminal A, Luminal B, HER2-enriched, and Basal-like*.  

The goal is to integrate multiple omics data types — **gene expression, copy-number variation, mutation, and protein abundance** — and learn nonlinear genomic interactions that define these subtypes.

---

## Dataset

**Dataset:** [BRCA Multi-Omics (TCGA)](https://www.kaggle.com/datasets/rbabaei/brca-multiomics-tcga)  
**Samples:** 705 breast-tumor cases  
**Features:** 1,936 omics attributes  
**Label:** Molecular subtype (multi-class)  

| Modality | Prefix | Feature Type | Example |
|-----------|---------|--------------|----------|
| Copy Number Variation | `cn_` | Numeric | `cn_CDH1` |
| Mutation Status | `mu_` | Binary | `mu_PTEN` |
| RNA Expression | `rs_` | Continuous | `rs_FOXA1` |
| Protein Abundance | `pp_` | Continuous | `pp_AKT1` |

---

## Model Architecture

### **Wide Branch**
- Uses binned categorical features (e.g., high/medium/low gene expression).  
- Captures explicit feature interactions (e.g., `PTEN_loss × AKT_expression_bin`).

### **Deep Branch**
- Processes normalized continuous omics features through dense layers.  
- Learns latent nonlinear representations of molecular pathways.

### **Combined Output**
- Concatenates wide and deep outputs → final softmax layer for 4-class subtype prediction.

---

## Technologies

- **Language:** Python 3.11  
- **Frameworks:** TensorFlow / Keras, Scikit-learn, Pandas, NumPy  
- **Visualization:** Matplotlib, Seaborn, Plotly  

---

## Evaluation Metrics

- **Macro F1-score** – balances subtype class imbalance  
- **AUROC per class** – measures discrimination quality  
- **Confusion matrix** – shows subtype prediction distribution  
- **Training curves** – visualize convergence and generalization  

---

## Key Findings (Expected)

- Deep embeddings reveal latent clusters corresponding to biological subtypes.  
- Wide branch improves classification of HER2-enriched and Basal-like classes.  
- Feature interactions (e.g., *PTEN* × *AKT1*) enhance interpretability.

---

## Citation

**Source:**

> Babaei, R. *et al.* (2015). *The Molecular Taxonomy of Breast Cancer*. **Cell**, 163(7): 1660–1670.  
> [https://www.cell.com/cell/fulltext/S0092-8674(15)01195-2](https://www.cell.com/cell/fulltext/S0092-8674(15)01195-2)



