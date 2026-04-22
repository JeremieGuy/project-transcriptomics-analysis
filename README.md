# Transcriptomic Analysis of Breast Cancer Gene Expression

## Project Overview

This project explores transcriptomic differences between tumor and normal breast tissue using gene expression data. The objective is to identify global expression patterns and detect genes that are significantly deregulated in cancer.

The analysis follows a standard bioinformatics workflow including data preprocessing, exploratory analysis, differential expression testing, and visualization.

## Dataset

The dataset consists of gene expression measurements from 151 breast tissue samples, including multiple cancer subtypes and normal tissue.

After preprocessing:
- Cell line samples were removed as they represent in vitro systems not directly comparable to primary tissue
- Samples were grouped into two conditions: tumor vs normal

Final dataset:
- ~137 samples
- ~54,000 genes
- Log-transformed expression values (microarray data)

## Methodology

The analysis was conducted in several steps:

### 1. Data preprocessing
- Removal of non-relevant samples (cell lines)
- Creation of binary labels (tumor vs normal)
- Validation of data structure and distribution

### 2. Exploratory analysis (PCA)
- Principal Component Analysis (PCA) was used to visualize global structure
- Samples were projected onto the first two principal components
- Additional visualization by cancer subtype revealed internal tumor heterogeneity

### 3. Differential expression analysis
- Gene-wise comparison between tumor and normal samples
- Welch t-test used due to unequal sample sizes
- Multiple testing correction performed using Benjamini-Hochberg (FDR)
- Significant genes defined as:
  - adjusted p-value < 0.05
  - |log2 fold change| > 1

### 4. Visualization
- Volcano plot to display significance vs effect size
- Heatmap of top differentially expressed genes

## Key Results

### PCA
- Clear separation between tumor and normal samples
- Tumor samples show higher heterogeneity
- Subtype-level structure is visible within tumor samples

### Differential Expression
- ~5600 genes significantly deregulated
- More genes are upregulated in tumor than downregulated
- Indicates strong transcriptional differences associated with cancer

### Volcano Plot
- Large number of highly significant genes
- Clear distribution of upregulated and downregulated genes

### Heatmap
- Top genes clearly separate tumor and normal samples
- Normal samples cluster tightly
- Tumor samples show more variability

## Interpretation

The results confirm that tumor and normal breast tissues have distinct gene expression profiles. A large number of genes are differentially expressed, reflecting widespread molecular changes in cancer.

The analysis also highlights the heterogeneity of tumor samples, which is consistent with the presence of multiple cancer subtypes. Overall, the dataset contains a strong and biologically meaningful signal.

## Limitations

- The number of normal samples is relatively small (~7), which may affect statistical power and variance estimation
- Gene identifiers correspond to microarray probe IDs rather than gene symbols
- The analysis is limited to transcriptomic data and does not include pathway-level interpretation

## Project Setup and Usage

### Repository Structure

```text
project-transcriptomics-analysis/
│
├── data/
│ ├── raw/
│ └── processed/
│
├── notebooks/
│ ├── 01_data_loading_and_qc.ipynb
│ ├── 02_exploratory_analysis.ipynb
│ ├── 03_differential_expression.ipynb
│ └── 04_visualization_volcano_heatmap.ipynb
│
├── results/
│ ├── figures/
│ └── tables/
│
├── README.md
└── requirements.txt
```

### How to run

1. Install dependencies:
   pip install -r requirements.txt

2. Run notebooks in order:
   - Data loading and preprocessing
   - Exploratory analysis (PCA)
   - Differential expression
   - Visualization

### Tools and Libraries

- Python
- pandas, numpy
- matplotlib, seaborn
- scikit-learn
- scipy, statsmodels

## Conclusion

This project demonstrates a complete transcriptomic analysis workflow, from raw data exploration to statistical testing and visualization. It highlights how gene expression data can be used to uncover meaningful biological differences between healthy and diseased tissue.