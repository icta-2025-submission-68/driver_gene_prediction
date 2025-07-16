We constructed gene co-expression networks (Coexpression Graphs) for each cancer type based on gene expression profiles.

- Source: Processed from TCGA RNA-Seq data (TPM normalized, log₂(TPM+1)).
- Method: 
  - Computed Pearson correlation coefficients (PCC) between each pair of genes.
  - Transformed correlation into distances:  
    `distance(gᵢ, gⱼ) = 1 - PCC(gᵢ, gⱼ)`
  - For each gene, connected to its top-k nearest neighbors using k-NN (e.g., `k = 3`).
  - The resulting graph represents a gene co-expression network that reflects functional associations between genes based on their expression patterns. These graphs are further combined with protein–protein interaction (PPI) data to enhance biological relevance.
