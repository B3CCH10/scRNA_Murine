# scRNA_Murine
scRNA: Lung Cell DE, CD45+ &amp; CD45-, Influenza A and Control
<br>[Single-Cell RNA-Sequencing Analysis of Influenza Infection in Murine Immune Cells]

## Introduction
Influenza virus, despite its significant impact on global health, has complex and yet not fully understood interactions with the host immune system. One of the major challenges in studying influenza virus is dissecting the diversity of cellular responses to viral infection. Recent advancements in single-cell RNA-sequencing (scRNA-seq) provide a powerful tool for exploring the cellular heterogeneity and understanding the host response to influenza infection. The original study by <i>Steuerman et al. (2018)</i> utilized massively parallel single-cell RNA-sequencing (MARS-seq) to map the host lung response to in-vivo influenza infection in wild-type and Irf7-knockout mice across nine immune and non-immune cell types. 

This study revealed unexpected infection prevalence across all cell types and demonstrated a robust generic transcriptional response irrespective of cell type and type-I interferon activity. In this project, we further analyze the raw count data from immune cell samples of both control and influenza-inoculated mice. Our objective is to gain deeper insights into the specific immune cellular responses, in this case, and identify key biomarkers that can lead to targeted therapeutic strategies.

## Methods
To further analyze the raw count data from immune cell samples, we employed an assortment of Python libraries such as Scanpy, Pandas, NumPy, and Matplotlib. The data, obtained 72 hours post-inoculation, was subjected to clustering analysis to identify distinct cellular responses to influenza infection.
- <b>Initially, </b>we loaded the data using the the Scanpy library. Then, we conducted a preliminary check for mitochondrial and ribosomal genes. For this purpose, we utilized a list of ribosomal genes downloaded from the Broad Institute's Molecular Signatures Database (MSigDB). We then calculated quality control metrics, including the number of genes, total counts, and percentage of mitochondrial and ribosomal counts for each cell.

- <b>Next, we filtered</b> out cells and genes that fell below a certain threshold, thereby ensuring a clean dataset for downstream analyses. We also performed normalization and log transformation of the data to account for differences in sequencing depth across cells.

- Following data normalization, we used principal component analysis (PCA) for <b>dimensionality reduction</b>. The variance explained by each principal component was then plotted. We constructed a shared nearest neighbor <b>(SNN)</b> graph based on the top 9 principal components. We then applied the <b>UMAP </b>algorithm to visualize the data in two dimensions .
We then applied the Leiden algorithm for community detection on our SNN
  graph. This allowed us to partition cells into clusters based on their gene expression profiles. To further our intention of identifying the major cell types of each cluster, we initiated a process to identify the top 20 genes from each identified cluster. To accomplish this, we employed differential gene expression analysis with scanpy’s ‘rank_gene_groups’ method, which helps to identify genes based on their expression across the identified leiden clusters.

## Results and Discussion
The analysis revealed distinct cell clusters, each potentially representing a unique cellular response to influenza infection. The identities of these clusters, however, are yet to be determined. The next steps will involve conducting differential gene expression analysis within and between these clusters to identify key genes and pathways involved immune response to influenza infection. This can lead to the identification of specific cell types involved in the immune response and possibly the discovery of novel biomarkers. The differences in gene expression profiles between infected and uninfected cells can also shed light on the molecular mechanisms involved in the immune response to influenza infection and could potentially identify targets for therapeutic intervention.

## Conclusion
Our preliminary analysis using single-cell RNA sequencing data has revealed a complex and diverse immune response to influenza infection. Further investigation of the identified cell clusters and their gene expression profiles promises to enhance our understanding of the host-virus interaction dynamics and might open new avenues for influenza therapy targeting specific cell types.

 
