# Soil Intactness Mapping & Sediment Source Prioritisation — Tasman District, New Zealand

> **Status: Manuscript under review — Remote Sensing of Environment**
> Full code, data, and derived rasters will be released upon acceptance.

---

## Overview

This project presents a reproducible, spatially explicit framework for catchment-scale sediment risk screening by combining deep learning land-cover segmentation with LiDAR-derived terrain and hydrological connectivity analysis.

The framework produces three operational outputs:

- **Soil Intactness Index (SII)** — a composite indicator of surface protection and erosion susceptibility across the catchment
- **Delivery Potential** — a connectivity surface quantifying how readily exposed sediment sources are linked to waterways
- **Sediment Source Priority** — an integrated prioritisation layer for targeting catchment management interventions

The study area covers the full extent of Tasman District, New Zealand, processed across sub-catchment reporting units.

---

## Key methods

| Component | Approach |
|---|---|
| Land cover mapping | Deep learning semantic segmentation (DeepLabV3+) on very-high-resolution RGB aerial imagery |
| Terrain analysis | LiDAR-derived DEM — slope, TWI, flow accumulation, flow path proximity |
| Index construction | Weighted linear combination MCDA — transparent, interpretable composite scoring |
| Prioritisation | Integrated bare soil exposure × delivery connectivity × disturbance pressure |
| Validation | Accuracy comparison across DeepLabV3+, ResUNet-a, Random Forest, and SVM baselines |

---

## Why deep learning over pixel-based classification

Standard pixel-based classifiers (Random Forest, SVM) fragment land-cover boundaries and introduce spatial noise that propagates through every downstream index layer. DeepLabV3+ preserves object geometry and patch coherence, which is not cosmetic — it directly reduces error propagation into the SII and delivery surfaces. The improvement in bare land detection is the most decision-critical finding, as bare land functions as the primary disturbance proxy in soil intactness frameworks.

---

## Tools & environment

- **ArcGIS Pro** — spatial data management, geoprocessing, raster analysis
- **Python** — arcpy, rasterio, geopandas, numpy
- **Deep learning** — DeepLabV3+ semantic segmentation
- **Data sources** — LINZ LiDAR (Tasman District), LINZ aerial RGB imagery, Tasman District Council catchment boundaries

---

## Repository structure (upon publication)

```
tasman-soil-intactness/
├── README.md
├── scripts/
│   ├── 01_preprocessing.py       # DEM derivatives and raster alignment
│   ├── 02_deeplab_inference.py   # Land cover segmentation pipeline
│   ├── 03_sii_calculation.py     # Soil Intactness Index construction
│   ├── 04_delivery_potential.py  # Connectivity surface generation
│   └── 05_prioritisation.py     # Integrated priority ranking
├── outputs/
│   ├── figures/                  # Map outputs and accuracy charts
│   └── tables/                   # Zonal statistics by region
└── requirements.txt
```

---

## Results snapshot

- DeepLabV3+ achieved the highest overall accuracy, Macro-F1, and Macro-IoU across all candidate models
- Bare land detection — the most management-critical class — showed the largest performance gap between deep learning and pixel-based approaches
- SII and Delivery Potential surfaces produced coherent, spatially interpretable outputs across all Tasman sub-catchments
- Integrated priority ranking provides ready-to-use intervention targets differentiated by steep-slope exposure and near-stream connectivity

Full quantitative results, accuracy tables, and mapped outputs are reported in the manuscript.

---

## Citation

> Wisaksono, M.A. et al. A Deep Learning and LiDAR-Derived Framework for Soil Intactness Mapping and Sediment Source Prioritisation: A Case Study in Tasman District, New Zealand. *Remote Sensing of Environment* (under review).

*DOI and full citation will be updated upon publication.*

---

## Contact

**Muaffan Alfaiz Wisaksono**
GIS Specialist · Precision Agriculture · Remote Sensing
Lincoln University, New Zealand — M.PrecAg (High Distinction)
muaffanw@gmail.com · [muaffanalfaiz.github.io](https://muaffanalfaiz.github.io)
