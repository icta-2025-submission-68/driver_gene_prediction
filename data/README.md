## Data

1. Coexpression Graphs

We constructed gene co-expression networks (Coexpression Graphs) for each cancer type based on gene expression profiles.

- Source: Processed from TCGA RNA-Seq data (TPM normalized, log₂(TPM+1)).
- Method: 
  - Computed Pearson correlation coefficients (PCC) between each pair of genes.
  - Transformed correlation into distances:  
    `distance(gᵢ, gⱼ) = 1 - PCC(gᵢ, gⱼ)`
  - For each gene, connected to its top-k nearest neighbors using k-NN (e.g., `k = 3`).
- File format: Each file (e.g., `ppi_BRCA_plus_knn3.csv`) contains undirected gene–gene edges:
  ```csv
  gene1,gene2
  TP53,BRCA1
  EGFR,KRAS
  ...
  Usage: These graphs define the structure (edge_index) for the GCN model.
2. Node Features

Each node is assigned a feature vector that integrates multiple biological signals. Specifically, we adopt four multi-omics features: somatic mutation rate, copy number alteration (CNA), DNA methylation, and gene expression, following the design of EMOGI. In addition, we incorporate pathway-derived features encoded as binary indicators, reflecting gene membership in curated pathways from databases such as KEGG and Reactome.


