<p align="center">
  <img src="https://github.com/B3CCH10/scRNA_Murine/blob/main/sized_dna.png?raw=true">
</p>


scRNA: Lung Cell DE, CD45+ &amp; CD45-, Influenza A and Control
<br>[Single-Cell RNA-Sequencing Analysis of Influenza Infection in Murine Immune Cells]

## Introduction
Influenza virus, despite its significant impact on global health, has complex and yet not fully understood interactions with the host immune system. One of the major challenges in studying influenza virus is dissecting the diversity of cellular responses to viral infection. Recent advancements in single-cell RNA-sequencing (scRNA-seq) provide a powerful tool for exploring the cellular heterogeneity and understanding the host response to influenza infection. The original study by <i>Steuerman et al. (2018)</i> utilized massively parallel single-cell RNA-sequencing (MARS-seq) to map the host lung response to in-vivo influenza infection in wild-type and Irf7-knockout mice across nine immune and non-immune cell types. 

This study revealed unexpected infection prevalence across all cell types and demonstrated a robust generic transcriptional response irrespective of cell type and type-I interferon activity. In this project, we further analyze the raw count data from immune cell samples of both control and influenza-inoculated mice. Our objective is to gain deeper insights into the specific immune cellular responses, in this case, and identify key biomarkers that can lead to targeted therapeutic strategies.

## Methods
To further analyze the raw count data from immune cell samples, we employed an assortment of Python libraries such as Scanpy, Pandas, NumPy, and Matplotlib. The data, obtained 72 hours post-inoculation, was subjected to clustering analysis to identify distinct cellular responses to influenza infection.
- <b>Initially, </b>we loaded the data using the the Scanpy library. Then, we conducted a preliminary check for mitochondrial and ribosomal genes. For this purpose, we utilized a list of ribosomal genes downloaded from the Broad Institute's Molecular Signatures Database (MSigDB). We then calculated quality control metrics, including the number of genes, total counts, and percentage of mitochondrial and ribosomal counts for each cell.

- <b>Next, we filtered</b> out cells and genes that fell below a certain threshold, thereby ensuring a clean dataset for downstream analyses. We also performed normalization and log transformation of the data to account for differences in sequencing depth across cells.

- Following data normalization, we used principal component analysis (PCA) for <b>dimensionality reduction</b>. The variance explained by each principal component was then plotted. 
- We constructed a shared nearest neighbor <b>(SNN)</b> graph based on the top 9 principal components. We then applied: <br>
<b>UMAP </b>algorithm to visualize the data in two dimensions . <br>
<b> Leiden </b> algorithm for community detection on our SNN graph. <br>
<br>This allowed us to partition cells into clusters based on their gene expression profiles. To further our intention of identifying the major cell types of each cluster, we initiated a process to identify the <b>top 20 genes</b> from each identified cluster. To accomplish this, we employed differential gene expression analysis with scanpy’s ‘rank_gene_groups’ method, which helps to identify genes based on their expression across the identified leiden clusters.

## Results 
Analyzed single-cell RNA sequencing (scRNA-seq) data from murine lung tissue to study the immune response to Influenza A infection, focusing on CD45+ leukocytes and CD45- epithelial cells. Lung tissue was chosen for its critical role in respiratory responses. scRNA-seq captured the heterogeneity of cell populations, revealing significant upregulation of immune cell types, including <b> T cells, B cells, macrophages, and dendritic cells, </b> in infected samples compared to controls. Further analysis identified specific gene expression changes within these subsets, particularly genes involved in antiviral defense (e.g.,<b> Ifit1, Oas1, Mx1</b>) and inflammation (e.g.,<b> Il6, Tnf, Ccl2 </b>), highlighting the specific roles these genes play in the immune response. This detailed examination provided a comprehensive view of the immune landscape during influenza infection, enhancing understanding of host-pathogen interactions at a single-cell level.
    
## Discussion
Our preliminary analysis using single-cell RNA sequencing data has revealed a complex and diverse immune response to influenza infection. Further investigation of the identified cell clusters and their gene expression profiles promises to enhance our understanding of the host-virus interaction dynamics and might open new avenues for influenza therapy targeting specific cell, and gene types:

 <i><b> Genes and Their Functions:</i></b>

- **Ifit1 (Interferon-Induced Protein with Tetratricopeptide Repeats 1)**: Produces a protein that helps inhibit viral replication by binding viral RNA.
- **Oas1 (2'-5'-Oligoadenylate Synthetase 1)**: Produces an enzyme that activates RNase L, leading to degradation of viral RNA.
- **Mx1 (Myxovirus Resistance 1)**: Produces a GTPase that inhibits the replication of influenza viruses and other RNA viruses.
- **Il6 (Interleukin 6)**: Produces a cytokine involved in inflammation and immune response, promoting the activation of immune cells.
- **Tnf (Tumor Necrosis Factor)**: Produces a cytokine that plays a key role in inflammation and apoptosis, helping to control infection.
- **Ccl2 (Chemokine (C-C motif) Ligand 2)**: Produces a chemokine that recruits monocytes, memory T cells, and dendritic cells to sites of infection and inflammation.
 
