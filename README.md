# Analysis of the human healthy airways at single-cell level.
The code is structured in 6 steps each with specific inputs and outputs (available in the data section).

### 1. Primary data analysis
Example code of the individual exploratory analysis performed on each of the 35 samples composing the atlas, with use of the Seurat v3 R package. From this initial analysis, repeated on the 35 samples, we obtained a rough estimate of the cell type composition of the atlas (to be refined later in the code) and a list of robust marker genes found expressed in the each cell types identified across all 35 samples.

Output from this step : Robust_marker_genes.tsv

### 2. Preprocessing of the data
In this section of the workflow, the data was pre-processed in paralle in 3 different scripts: 

   - Consensus cells and genes filtering across the 35 samples, normalisation of all the cell counts to 10000 UMIs and merging of all the datasets in a single one to produce a large and preliminary processed count table. [`Pre-processing_preliminary_dataset.ipynb`] 

   - Iterative preliminary analysis of the dataset, includes progressive cell filtering of small clusters composed of 'low quality'/'peculiar' cells (high mitochondrial cluster-cells, ...). (preliminary analysis script - v1 ...v3)
    
   - Consensus cells and genes filtering across the 35 samples (without normalisation) and merging of all the datasets in a single one to produce a large and unique raw count table. [`Pre-processing_raw_dataset.ipynb`]

   - Identification/Inference of doublet cells across all the 35 samples independantly, and further analysis of the dataset to estimate the proportion of inferred doublet cells in the resulting clusters and corresponding cell filtering. [`Pre-processing_doublets.ipynb`; `Pre-analysis_doublets.ipynb`; `Summary_dounlets_analysis.Rmd`]   
    
   - Pre-processing of the background in gene expression across all samples to produce a 'background free' raw count table. [`Pre-processing_gene-background_soupX.Rmd`]
   
**Input files for this step**
All the 10x output files from the 35 samples (available for download on ...)
RB_genes.txt (list of the filtered out ribosomal genes)
   
**Output files from this step:**
  - raw_countTable.
  - high_quality cells object
  - raw_countTable_soupX



