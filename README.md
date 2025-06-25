flowchart TD

  %% Data sources
  LS[Landsat 8/9]
  S2[Sentinel-2]

  %% Preprocessing for Landsat
  LS --> LS_CM[Cloud Masking - Landsat (pixel_qa)]
  LS_CM --> LS_IDX[NDVI & NDWI Calculation - Landsat]

  %% Preprocessing for Sentinel
  S2 --> S2_CM[Cloud Masking - Sentinel-2 (QA60)]
  S2_CM --> S2_IDX[NDVI & NDWI Calculation - Sentinel]

  %% Merge path
  LS_IDX --> MRG[Merge or Stack Indices]
  S2_IDX --> MRG

  %% Classification
  MRG --> CLSF[Classification using RF and SVM]
