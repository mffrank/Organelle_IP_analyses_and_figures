# Global organelle profiling defines a sub-cellular map of the human proteome

This repository serves as a comprehensive resource for exploring and understanding our manuscript, [Global Organelle Profiling Defines a Sub-Cellular Map of the Human Proteome](https://www.biorxiv.org/content/10.1101/2023.12.18.572249v1). Inside, you'll find detailed Jupyter notebooks and scripts that were pivotal in our data analysis process and in generating the figures.

Our aim is to provide an in-depth, transparent view into our research methods and findings. Dive into our notebooks to see how we transformed raw data into meaningful insights, or explore our scripts to understand the technical underpinnings of our figure generation. We hope this repository will be a useful tool in your own research and learning journey.

## Usage
### Set up code, data and environment
```sh
git clone https://github.com/czbiohub-sf/Organelle_IP_analyses_and_figures.git --depth=1
cd Organelle_IP_analyses_and_figures
```

To run the notebooks (except supplementary figure 3 panel E) use the provided [conda](https://docs.conda.io/en/latest/) environment:
```sh
conda env create -n OrgIP -f environment.yml
conda activate OrgIP
```
For a distinct run, the run timestamp has to be set first by running the `0.Set_timestamp.ipynb` (and, for figure 5, `0.Set_fig5_timestamp.ipynb`) notebook.  The default setting is  to look for the frozen imputed tables used to generate our figures.

If reproducing figures from frozen imputed tables, skip the `enrichment` notebooks and start with `Fig1` and proceed in order.

### Supplementary figure 3 panel E
Supplementary figure 3 panel E uses a separate conda environment specification.
```sh
conda env create -n xgb2 -f notebooks/Supplementary_figures/Suppl_fig3/panel_E/environment.yml
conda activate xgb2
```

## What's in this repo
### `data/`
This directory contains various external and processed datasets required to make the figures. Note that some of these datasets are from external sources; these are found in the `data/external/` subdirectory. The remaining datasets are all original datasets generated by or derived from this project. Note that some datasets, including the MaxQuant output is too large to host on GitHub. Please email the corresponding authors to obtain larget datasets. We are in the process of making large datasets available on FigShare. 


### `notebooks/`
This directory includes a series of Jupyter notebooks that detail the analytical processes and methodologies used in the creation of each figure. These notebooks serve as the principal guide for understanding the application of the scripts and Python modules located in the scripts/ directory, specifically focusing on their roles in analysis and figure generation.

We provide a structured tree diagram (below) representing the organization of the notebooks directory. This diagram delineates the specific notebooks responsible for generating each panel of the figures.

It is important to execute the notebooks sequentially, following the top-to-bottom order presented in the tree diagram. This ensures a smooth workflow, as many notebooks requires the output of their predecessors.

```
notebooks
|
├── 0.Set_timestamp.ipynb
├── enrichment
|   ├── 1.QC_filter_and_impute.ipynb
|   ├── 2.Batch_selection.ipynb
|   ├── 3.correlation_filter.ipynb
|   ├── 4.NOC_processing.ipynb
|   └── output
|       ├── correlation_tables
|       |   └── ..
|       ├── enrichment_and_volcano_tables
|       |   └── ..
|       └── preprocessing
|           └── ..
├── Fig1
│   └── panel_L
│       ├── Fig1_L_heatmap.ipynb
│       └── output
|           └── ..
├── Fig2
│   ├── panel_B
│   │   ├── Fig2_B_heatmap.ipynb
│   │   └── output
|   |       └── ..
│   ├── panel_C
│   │   ├── Fig2_C_consensus_annotation.ipynb
│   │   └── output
|   |       └── ..
│   └── panel_D
│       ├── Fig2_D_umap.ipynb
│       └── output
|           └── ..
├── Fig3
│   ├── panels_A_B_F
│   │   ├── Fig3_A_B_F_local_k-NN_network.ipynb
│   │   └── output
|   |       └── ..
│   └── panels_C_D
│      ├── Fig3_C_D_cluster_connectivity_and_Jaccard_coeff.ipynb
│      └── output
|          └── ..
├── Fig4
│   └── panel_D
│       └── Please_read.txt
├── Fig5
|   ├── 0.Set_fig5_timestamp.ipynb
│   ├── panel_A
│   │   ├── 1.infected_enrichment
|   |   |   ├── 1.QC_filter_and_impute.ipynb
|   |   |   ├── 2.Batch_selection.ipynb
|   |   |   ├── 3.correlation_filter.ipynb
|   |   |   ├── 4.NOC_processing.ipynb
|   |   |   └── output
|   |   |       └── ..
│   │   ├── 2.control_enrichment
|   |   |   ├── 1.QC_filter_and_impute.ipynb
|   |   |   ├── 2.Batch_selection.ipynb
|   |   |   ├── 3.correlation_filter.ipynb
|   |   |   ├── 4.NOC_processing.ipynb
|   |   |   └── output
|   |   |       └── ..
│   │   └── 3.aligned_umap
│   │       ├── Fig5_A_aligned_umap.ipynb
│   │       └── output
|   |           └── ..
│   ├── panel_B
│   │   ├── Fig5_B_remodeling_score.ipynb
│   │   └── output
|   |       └── ..
│   ├── panel_C
│   │   ├── Fig5_C_umap_with_leiden_labels.ipynb
│   │   └── output
|   |       └── ..
│   ├── panel_D
│   │   ├── Fig5_D_trajectory.ipynb
│   │   └── output
|   |       └── ..
│   └── panel_E
│       ├── Fig5_E_Sankey_plot.ipynb
│       └── output
|           └── ..
├── Fig6
│   └── ..
|
└── Supplementary_figures
    ├── Suppl_fig1
    |   └── ..
    ├── Suppl_fig2
    |   ├── Suppl_fig2.ipynb
    │   └── output
    |       └── ..
    ├── Suppl_fig3
    |   ├── panel_A
    |   |   ├── Suppl_fig3_A_IP_correlation_vs_interaction_stoi.ipynb
    |   |   └── output
    |   |       └── ..
    |   └── panel_B
    |       ├── Suppl_fig3_B_tenary_plots.ipynb
    |       └── output
    |           └── ..
    ├── Suppl_fig4
    |   └── panel_B
    |       ├── Suppl_fig4_B_XGBoost_classifier.ipynb
    |       └── output
    |           └── ..
```


### `scripts/`
These are Python modules that contain the bulk of the code used for data analysis and figure generation. They are used directly by the Jupyter notebooks discussed above. Please note that these scripts are explicitly written for, and specific to this project and/or the OpenCell project. They are __not__ intended to form a stand-alone or general-purpose Python package.



# License
This project is licensed under the BSD 3-Clause license - see the LICENSE file for details.
