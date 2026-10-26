# nnUNet-Iceberg-Detection
Automated iceberg detection in Sentinel-1 SAR imagery using nnU-Net

This repository provides the source code for **automated iceberg detection and segmentation in Sentinel-1 Synthetic Aperture Radar (SAR) imagery using nnU-Net**.

The framework is designed to support large-scale iceberg mapping in Antarctic coastal waters under varying environmental and sea-ice conditions.

The code accompanies the manuscript: **Out-of-the-box iceberg detection in SAR imagery using nnU-Net**

## Overview

Accurate and large-scale iceberg detection is essential for monitoring ice-shelf calving, understanding iceberg dynamics, and investigating interactions between the Antarctic Ice Sheet and the Southern Ocean. This study applies the self-configuring nnU-Net framework to automated iceberg segmentation in Sentinel-1 SAR imagery. The model is trained using iceberg annotations derived from a circum-Antarctic iceberg dataset (Chen et al., 2026) and evaluated across different Antarctic regions and seasons.

The trained model is further applied to generate quarterly iceberg distribution maps across four representative iceberg aggregation regions from 2015 to 2025.

To facilitate reproducibility and practical application, this repository provides the trained nnU-Net model, allowing users to directly detect icebergs in Sentinel-1 SAR EW imagery without retraining. Users can download the pretrained model and run the provided inference scripts to generate georeferenced iceberg detection results.
## Key Features

- **Automated iceberg segmentation:** Pixel-level iceberg detection in Sentinel-1 SAR imagery using nnU-Net.
- **Spatial and temporal generalization:** Evaluation across different Antarctic regions and seasons.
- **Accuracy assessment:** Pixel-level and object-level evaluation against manually delineated iceberg annotations.
- **Large-scale application:** Quarterly iceberg mapping in four Antarctic regions during 2015–2025.

## Study Regions

The study focuses on four representative iceberg aggregation regions around Antarctica, each encompassing multiple glaciers and ice shelves:

| Region | Representative location |
|---|---|
| Region I | Totten region |
| Region II | Getz region |
| Region III | Thwaites region |
| Region IV | Prince Harald region |
## Software Requirements

The model was developed and evaluated using the following computational environment:

| Component | Specification |
|---|---|
| Operating system | Windows 10 |
| Python | 3.10.18 |
| PyTorch | 2.5.1 |
| CUDA | 12.1 |
| nnU-Net | v2.6.2 |
| GPU | NVIDIA RTX 4090 D (24 GB) |
| RAM | 128 GB |

Additional Python dependencies include Rasterio, GeoPandas, NumPy, Pandas, and other geospatial processing libraries.

## Workflow

The processing workflow consists of five main stages:

**1. Data preprocessing**

Sentinel-1 SAR imagery and iceberg annotation polygons are transformed into the Antarctic Polar Stereographic coordinate reference system (EPSG:3031).

**2. Training sample preparation**

Training samples are generated from SAR images and manually corrected iceberg annotations, including iceberg-containing patches and background samples.

**3. Model training**

The nnU-Net framework is used to automatically configure and train the iceberg segmentation model.

**4. Iceberg segmentation and postprocessing**

The trained model produces pixel-level iceberg predictions, which are subsequently processed to generate georeferenced iceberg polygons.

**5. Accuracy assessment and large-scale application**

Model predictions are evaluated against independent reference annotations using pixel-level and object-level accuracy metrics. The workflow is then applied to long-term quarterly iceberg mapping.

Detailed execution instructions and example commands will be added as the code is finalized.

## Model Performance

Independent testing across Antarctic regions and seasons yielded the following pixel-level and object-level F1 scores:

| Region | Test scene | Pixel-level F1 | Object-level F1 |
|---|---|---:|---:|
| Region I | 2015-04 | 0.790 | 0.822 |
| Region II | 2015-07 | 0.902 | 0.881 |
| Region III | 2015-04 | 0.971 | 0.863 |
| Region III | 2015-07 | 0.979 | 0.904 |
| Region III | 2015-10 | 0.981 | 0.870 |
| Region III | 2016-01 | 0.965 | 0.897 |
| Region IV | 2016-01 | 0.742 | 0.755 |
| **Mean** | — | **0.904** | **0.856** |
| **SD** | — | **0.099** | **0.052** |

The independent accuracy assessment included iceberg objects with areas of at least 0.1 km². Object-level F1 scores were calculated using an Intersection over Union (IoU) matching threshold of 0.5.

Using the trained model, a total of **574,511 icebergs** with areas of at least 0.04 km² were detected across four Antarctic study regions during 2015–2025.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Contact

For questions regarding the code and its application to iceberg detection, please open an issue in this GitHub repository.
