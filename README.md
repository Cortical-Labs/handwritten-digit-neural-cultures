# Electrophysiological Recordings for Biological Reservoir Computing

## Overview

This dataset contains approximately 85 GB of time-series electrophysiological data and associated metadata from experimental recordings (MNIST runs). The data captures the activity of human iPSC-derived neuronal networks interfaced with the CL1 biocomputing platform while actively engaged in a spatio-temporal handwritten digit recognition task.

> **Recording-count discrepancy:** The source documentation describes 53 experimental recordings, but the supplied CSV manifest contains 52 data rows. This discrepancy is unresolved and should be corrected before publication by either adding the missing manifest row or updating the documented count.

## Data Index and Metadata

The core structural organization, experimental conditions, and directory references for the computational runs are detailed in the primary manifest file:

`ael3906_Suppl. Excel_seq1_v1_2.csv`

The CSV manifest contains the metadata required to map results and experimental conditions to specific recordings.

### Manifest fields

The manifest contains the following fields for each recording run:

| Field | Description |
| --- | --- |
| `Sys-ID` | System identifier for the specific experimental run (for example, `sys-000`). |
| `Chip ID` | Identifier for the specific Micro-Electrode Array chip utilized (for example, `MCS_1_43609_00001`). |
| `Date` | Date the recording was captured. |
| `Cell Type` | Specifies both the physical architecture and cellular lineage (for example, `Organoid` or `Organoid (Hippo)`). |
| `Num Spikes` | Total number of neuronal spikes detected during the recording. |
| `Real` | Classification accuracy for the spatio-temporal MNIST task under the corresponding evaluation paradigm. |
| `Random` | Control classification accuracy for randomized data, used as a baseline. |
| `Real with Stim` | Classification accuracy for the spatio-temporal MNIST task under the corresponding evaluation paradigm. |
| `Time Bin Accuracy Holdout over Trials` | Temporal decoding accuracy using the corresponding holdout validation set. |
| `Time Bin Accuracy Holdout over Time` | Temporal decoding accuracy using the corresponding holdout validation set. |
| `Real One Shot` | Classification accuracy for the spatio-temporal MNIST task under the corresponding evaluation paradigm. |
| `Time Bin Random` | Supplementary control metric and decoder baseline performance measurement. |
| `Random with Stim` | Control classification accuracy for randomized data, used as a baseline. |
| `Biased Decoder` | Supplementary control metric and decoder baseline performance measurement. |
| `Biased Decoder Random` | Supplementary control metric and decoder baseline performance measurement. |

> **Manifest filename and header note:** The source documentation names the manifest `ael3906_Suppl. Excel_seq1_v1_2.csv`, while the supplied file inspected during README preparation is named `ael3906_Suppl. Excel_seq1_v1.csv`. That supplied file also contains trailing spaces in the raw headers `Chip ID ` and `Time Bin Accuracy Holdout over Time `. Confirm the publication filename and remove unintended header whitespace if appropriate before release.

## Directory Structure

The cloud storage bucket uses the flat hierarchical structure described in the source documentation. The root directory contains the master metadata index, followed by subdirectories for each recording: a parent folder identified by `Chip ID` and a child folder identified by `Date`.

Each recording directory contains exactly 1,000 chunked `.h5` files associated with that MNIST run.

```text
/dataset_root/
|
|-- ael3906_Suppl. Excel_seq1_v1_2.csv  # Master index and metadata
|
|-- [Chip_ID_1]/[Date_1]/               # Recording / MNIST Run 1
|   |-- 0001.h5
|   |-- 0002.h5
|   |-- ...
|   `-- 1000.h5
|
`-- [Chip_ID_N]/[Date_N]/               # Recording / MNIST Run N
    |-- 0001.h5
    |-- ...
    `-- 1000.h5
```

## Access and Usage

Public AWS Open Data access details will be added here when the dataset's S3 resource is available.

To navigate the dataset:

1. Start with the CSV manifest to identify a recording and review its experimental conditions and classification results.
2. Use the recording's `Chip ID` and `Date` values to locate its directory.
3. Retrieve the numbered `.h5` chunks for that recording as required for analysis.

The supplied documentation does not define the internal HDF5 schema, dataset keys, units, sampling rate, or a reference loading API. Those details should be documented separately before users are given schema-specific code examples.

## Citation and Publication

If you use this dataset, please cite the associated preprint:

> Loeffler, A., Habibollahi, F., Abu-Bonsrah, K. D., Azadi, A., Desouza, C., Chan, H. W., Nishi, Y., Zhou, J., Doensen, F., Yamamoto, H., Watmuff, B., & Kagan, B. J. (2026). *Handwritten Digit classification with neural cultures is influenced by neural architecture, network dynamics, and decoding methods*. bioRxiv, 2026.08.10.743829. https://doi.org/10.64898/2026.08.10.743829

- [bioRxiv publication page](https://www.biorxiv.org/content/10.64898/2026.08.10.743829v1)
- [DOI](https://doi.org/10.64898/2026.08.10.743829)

## License

This dataset is licensed under the [Creative Commons Attribution-NonCommercial 4.0 International License (CC BY-NC 4.0)](https://creativecommons.org/licenses/by-nc/4.0/).

Under this license, users may share and adapt the material with appropriate attribution for non-commercial purposes. See the linked license for the complete terms.
