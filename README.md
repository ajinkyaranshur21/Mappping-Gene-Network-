# Mapping Gene Networks Using Correlation Schemes

**Author:** Ajinkya Ranshur  
**Date:** August 2023

## Methods

### Attempt 1

In this attempt, I aimed to analyze correlations within the TCGAvsGTEX pancreas dataset, readily available on the Xena Browser website.

My objective was to identify relationships between different genes within the dataset by computing their covariance based on respective logFC (logarithm of fold change) values. This was achieved by plugging these values into the covariance formula, yielding a numerical result:


A significant limitation arose from this approach. While the covariance is foundational to calculating correlation, the Pearson's correlation coefficient requires division by the standard deviations of both variables:


Since correlation calculations demand multiple values to understand their deviation from the mean, utilizing only one value caused an issue. This approach resulted in working with a dimensionless quantity due to the denominator in the covariance formula (N-1) becoming zero.

To illustrate, consider the following table:

| GENE1 | GENE2 |
|-------|-------|
| 1.23  | 3.05  |

Recognizing the limitations of this method, I will now present a more comprehensive approach in the subsequent section.

### Attempt 2

In this approach, I will be acquiring the TCGA gene expression dataset for the pancreas. This dataset employs the FPKM normalization method for its raw data collection. I will then proceed to compare this dataset with the GTEX dataset, which also employs the FPKM normalization method. However, the GTEX dataset contains gene expression data from pancreatic tissue of unaffected patients.

The key distinction of this approach compared to the previous one lies in the fact that we will possess a collection of values in the form of gene expression data for each specific gene. By computing the correlation between different genes in the context of pancreatic tissue, we can achieve statistically meaningful results. Importantly, this approach resolves the dimensionless problem that was encountered in the earlier method.

For illustrative purposes, consider the following gene expression values:

| GENE1 | GENE2 |
|-------|-------|
| 1.23  | 3.05  |
| 2.23  | 4.05  |
| 4.23  | 5.05  |
| 6.23  | 1.05  |

In this attempt, I will not be calculating the fold change value. The computational time required for this operation is substantial, even when employing parallel computing techniques. Additionally, I am omitting the fold change calculation to observe the extent of disparity in the gene network when correlation is based solely on gene expression data, as opposed to correlations derived from fold change values.
