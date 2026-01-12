# Wearable Physiological Processing Pipeline (TFM)

This repository contains the complete data processing pipeline developed for a Master’s Thesis (TFM) focused on the harmonization, preprocessing, and feature extraction of physiological signals acquired from wearable devices, specifically **Empatica E4** and **Empatica Embrace Plus**.

The pipeline addresses methodological challenges derived from differences in data architecture, temporal fragmentation, and signal formatting between both devices, enabling the reuse of consolidated analytical tools such as **FLIRT**.

---
## Repository Structure

The pipeline is organized into sequential processing stages, each implemented as an independent Jupyter notebook:

TFM-wearable-physiological-pipeline/
│
├── Leer y guardar/
│   ├── Leer_archivos_avro.ipynb
│   └── guardar_csv_embrace.ipynb
│
├── Emparejamiento/
│   └── emparejar_embrace_empatica.ipynb
│
├── Preprocesamiento/
│   └── preprocesamiento.ipynb
│
├── On Off Body/
│   └── Alg OnOffBody.ipynb
│
├── Van Hees/
│   └── Alg Van Hees.ipynb
│
├── FLIRT/
│   └── aplicacion mask + flirt.ipynb
│
└── README.md
---

## Pipeline Stages (Overview)

The pipeline is organized into sequential processing stages, each implemented as an independent Jupyter notebook:

- **Stage 1 — Leer y guardar**
  - Read and decode raw Embrace Plus AVRO exports and convert them to structured CSV signals.

- **Stage 2 — Emparejamiento**
  - Pair Embrace Plus recordings with Empatica E4 recordings at the subject level.

- **Stage 3 — Preprocesamiento**
  - Reconstruct time series, clean signals, and normalize formats to ensure temporal coherence across devices.

- **Stage 4 — On Off Body**
  - Detect and exclude non-wear periods (off-body) to improve signal reliability.

- **Stage 5 — Van Hees**
  - Identify sustained inactivity / stable segments using a Van Hees–based method as an additional quality-control layer.

- **Stage 6 — FLIRT**
  - Apply combined masks, select optimal continuous segments, reformat signals to FLIRT inputs, and extract physiological features from **EDA**, **ACC**, and **IBI**.

---

## Folder-to-Notebook Mapping

This section maps the repository folders to the notebooks you should execute.

### 1) `Leer y guardar/`

- `Leer_archivos_avro.ipynb`  
  Reads and parses Embrace Plus raw AVRO data.

- `guardar_csv_embrace.ipynb`  
  Converts the parsed outputs into structured CSV files with reconstructed timestamps.

### 2) `Emparejamiento/`

- `emparejar_embrace_empatica.ipynb`  
  Creates the subject-level pairing between Embrace Plus and Empatica E4 datasets.

### 3) `Preprocesamiento/`

- `preprocesamiento.ipynb`  
  Signal reconstruction and preprocessing (cleaning, normalization, alignment logic as implemented in the notebook).

### 4) `On Off Body/`

- `Alg OnOffBody.ipynb`  
  Implements on-body / off-body detection to exclude invalid wear-time intervals.

### 5) `Van Hees/`

- `Alg Van Hees.ipynb`  
  Implements a Van Hees–based inactivity detection to identify stable segments and generate a sleep/inactivity mask.

### 6) `FLIRT/`

- `aplicacion mask + flirt.ipynb`  
  Applies combined masks (On/Off-body + Van Hees), selects valid continuous segments, formats signals for FLIRT, and extracts features.

---

## How to Run (Recommended Order)

Run the notebooks in the following order:

1. `Leer y guardar/Leer_archivos_avro.ipynb`  
2. `Leer y guardar/guardar_csv_embrace.ipynb`  
3. `Emparejamiento/emparejar_embrace_empatica.ipynb`  
4. `Preprocesamiento/preprocesamiento.ipynb`  
5. `On Off Body/Alg OnOffBody.ipynb`  
6. `Van Hees/Alg Van Hees.ipynb`  
7. `FLIRT/aplicacion mask + flirt.ipynb`

---
