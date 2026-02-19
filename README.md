# Functional-Connectivity-in-Glioblastoma
Spatially Restricted Immature Neuronal Programs Drive Functional Connectivity in Glioblastoma

<img width="851" height="895" alt="image" src="https://github.com/user-attachments/assets/ee3c1d0a-b2e3-433b-a729-17ff13ce91e9" />


## Repository structure

- `scripts/`
  - `Preprocessing.Rmd` — import + harmonize inputs (spatial, single-cell, MEA, graph edges/nodes) and create analysis-ready objects
  - `Analysis_Part1.Rmd` — core analyses (SPATA objects, kNN mapping, cell–network correlations, WGCNA preparation)
  - `Analysis_Microglia.Rmd` — focused myeloid/microglia analyses (latent space, differential expression, enrichment, reference mapping)
  - `Analysis_Figure1.Rmd` — code used to generate **Figure 1** panels
  - `Analysis_Figure2.Rmd` — code used to generate **Figure 2** panels
- `data/` — **not tracked**; place input data here (see “Inputs”)
- `results/` — generated outputs (tables, intermediate objects, figures)
- `docs/` — documentation assets (including the workflow figure)

## Recommended execution order

1. `scripts/Preprocessing.Rmd`
2. `scripts/Analysis_Part1.Rmd`
3. `scripts/Analysis_Microglia.Rmd`
4. `scripts/Analysis_Figure1.Rmd`
5. `scripts/Analysis_Figure2.Rmd`

## Quickstart (reproducible rendering)

From R (R >= 4.2 recommended):

```r
# install.packages("rmarkdown")
rmarkdown::render("scripts/Preprocessing.Rmd")
rmarkdown::render("scripts/Analysis_Part1.Rmd")
rmarkdown::render("scripts/Analysis_Microglia.Rmd")
rmarkdown::render("scripts/Analysis_Figure1.Rmd")
rmarkdown::render("scripts/Analysis_Figure2.Rmd")
```

> Tip: for clean, portable paths, prefer relative paths and/or `here::here()` in all scripts.

## Inputs

The scripts expect project data to be available locally (not committed to Git). Typical inputs include:
- spatial transcriptomics objects (e.g., Visium/SPATA-compatible inputs)
- single-cell objects (e.g., Seurat/AnnData exports)
- electrophysiology / MEA-derived summaries (if applicable)
- graph node/edge tables (CSV/TSV) used for spatial network construction

Place inputs under `data/` and update the path variables at the top of each script as needed.

## Outputs

Outputs are written to `results/` (figures, tables, and intermediate objects). The figure scripts are intended to be the final step and should reproduce the manuscript panels given the required inputs.

## Privacy / portability notes

All scripts in this repository have been sanitized to remove personal identifiers and machine-specific absolute paths.
You may still need to adjust:
- file locations (use `data/` and `results/` or `here::here()`)
- computing backends (optional Python via `reticulate`, if used)

## Citation

If you use these scripts, please cite the associated manuscript (details to be added upon publication).

## License

Add a license file (e.g., MIT, BSD-3, or CC BY 4.0) appropriate for your project.


