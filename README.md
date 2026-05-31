# Generative MRI

Gateway repository for controllable 3D brain MRI synthesis with BrainScape and Wavelet-Fusion Diffusion Models (WFDM).

This repository is the public entry point for resources associated with our work on multimodal brain MRI synthesis. It links to the WFDM paper, BrainScape, medmetric, the WFDM source code, trained checkpoints, and planned inference resources.

> **Resource availability:** BrainScape and medmetric are already public. The WFDM source code, trained checkpoints, and inference resources will be linked here after the WFDM preprint/paper is public.

## Overview

WFDM is a controllable 3D latent diffusion model for synthesizing anatomical brain MRI volumes across multiple contrasts:

- T1-weighted MRI (`T1w`)
- T2-weighted MRI (`T2w`)
- gadolinium-enhanced T1-weighted MRI (`T1Gd` / `T1ce`)
- fluid-attenuated inversion recovery MRI (`FLAIR`)

WFDM performs diffusion in the latent space of a Wavelet-Fusion VAE compressor and conditions generation on the requested MRI modality. The reported model also supports demographic and clinical metadata conditioning using an explicit metadata availability mask, so unavailable fields are distinguishable from observed values.

The study is built on [BrainScape](https://github.com/yasinzaii/BrainScape), an open-source framework and curated data resource for integrating and preprocessing public anatomical MRI datasets.



## Resource Map

| Resource | Purpose | Status |
|---|---|---|
| WFDM paper | Manuscript/preprint describing the WFDM method, experiments, evaluation, and results | TODO: add link after public release |
| BrainScape | Public framework and curated data resource used to build the WFDM study dataset | Available: <https://github.com/yasinzaii/BrainScape> |
| medmetric | Public Python package for standardized evaluation of 3D synthetic medical images | Available: <https://github.com/yasinzaii/medmetric> |
| WFDM source code | Training, sampling, configuration files, evaluation scripts, and experiment utilities for WFDM | TODO: add source-code link after preprint is released |
| WFDM checkpoints | WFDM generator checkpoint and Wavelet-Fusion VAE compressor checkpoint | TODO: release after WFDM paper is released |
| WFDM inference package | Lightweight Python package for generating MRI volumes from released WFDM checkpoints | Planned |



## Planned WFDM Release

The planned WFDM release will include:

- WFDM source-code repository
- Wavelet-Fusion VAE / WF-SA-VAE compressor checkpoint used by the reported WFDM model
- WFDM generator checkpoint, including the diffusion U-Net and associated conditioning components
- model and experiment configuration files matching the reported experiments
- inference scripts and example configuration files in the source-code repository
- lightweight Python package for checkpoint-based inference (Planned)
- checkpoint download links and checksums
- environment and installation notes
- evaluation scripts based on medmetric

## Main Components

### WFDM

WFDM combines:

- a Wavelet-Fusion VAE compressor for compact 3D MRI latent representations
- a conditional 3D diffusion model trained in the learned latent space
- target-modality conditioning for `T1w`, `T2w`, `T1Gd/T1ce`, and `FLAIR` generation
- demographic and clinical metadata conditioning

### BrainScape Data Handling

The WFDM source-code repository uses BrainScape-preprocessed MRI records and includes project-specific data modules and transforms for preparing these records for training, sampling, and evaluation.

These components include:

- BrainScape JSON record loading
- train/validation/test split handling
- modality-label conditioning
- demographic and clinical metadata conditioning
- intensity normalization for training, inference, and evaluation workflows

The WFDM paper uses a fixed earlier BrainScape snapshot containing **157 datasets and 45,880 preprocessed MRI scans** across `T1w`, `T2w`, `T1Gd`, and `FLAIR`. This differs slightly from the full published BrainScape release, which contains **160 datasets and 46,583 scans** after quality control.

### Evaluation

Synthetic MRI evaluation is performed using [medmetric](https://github.com/yasinzaii/medmetric), which provides standardized metric implementations for 3D medical image synthesis evaluation.

In the WFDM paper, generator evaluation focuses on:

- MedicalNet feature-space Fréchet distance (FID)
- MedicalNet feature-space Maximum Mean Discrepancy (MMD)
- MS-SSIM between generated samples as a diversity proxy
- inference latency and peak GPU memory usage

The autoencoder/compressor evaluation additionally reports reconstruction metrics, including:

- LPIPS
- SSIM
- MS-SSIM
- PSNR
- MSE

## Model Weights

WFDM model weights will be linked here after the WFDM paper is public.

Planned checkpoint release items:

- WFDM generator checkpoint
- WF-SA-VAE / Wavelet-Fusion VAE compressor checkpoint used by the reported WFDM model
- matching model and inference configuration files
- checkpoint download links and checksums


## Inference

The WFDM source-code repository contains Hydra-based inference configurations and scripts for research use, including sampling and synthetic-dataset generation workflows. These workflows are intended for reproducing paper experiments and running the full project pipeline.

For wider reuse, we plan to provide a separate lightweight Python package so users can generate MRI volumes from released WFDM checkpoints esily.



## Source Code

The WFDM source-code repository will be linked here after the preprint is public. The current internal research snapshot includes:

- configuration-driven experiments using Hydra
- training pipelines for Wavelet-Fusion VAE / WF-SA-VAE compression models
- WFDM training and sampling scripts
- model definitions and wrappers
- BrainScape data modules and transforms
- modality and metadata conditioning utilities
- baseline generator integrations used for benchmarking
- metric and reporting scripts
- visualization utilities
- environment specification
- tests for core model, data-handling, metric, and training components


## Data

BrainScape aggregates public MRI datasets through dataset-specific configuration files while preserving the access conditions, ethics, and licensing requirements of the original sources. Users should use the BrainScape workflow for MRI collation and preprocessing.

Useful links:

- BrainScape repository: <https://github.com/yasinzaii/BrainScape>
- BrainScape paper: <https://doi.org/10.1162/IMAG.a.944>

## Reproducibility

The WFDM research code is organized around configuration-driven experiments. The public release is planned to include the exact resources needed to reproduce the reported workflows.

Planned reproducibility resources:

- source-code release tag or commit hash
- environment file
- training configuration files
- inference configuration files
- metric/evaluation configuration files
- checkpoint download links and checksums



## Citation

If you use this project, please cite the WFDM paper. Please also cite BrainScape and medmetric when using the corresponding resources.

### WFDM

```bibtex
TODO
```

### BrainScape

```bibtex
@article{Yasinzai-BrainScape-2025,
  title   = {BrainScape: An open-source framework for integrating and preprocessing anatomical MRI datasets},
  author  = {Yasinzai, Muhammad Nabi and Mito, Remika and Pedersen, Mangor},
  journal = {Imaging Neuroscience},
  volume  = {3},
  year    = {2025},
  doi     = {10.1162/IMAG.a.944}
}
```



### medmetric

```bibtex
@software{Yasinzai-MedMetricGitHub,
  title   = {medmetric: Metrics for Synthetic MRI Generation},
  author  = {Yasinzai, Muhammad Nabi},
  year    = {2026},
  version = {v0.1.1},
  url     = {https://github.com/yasinzaii/medmetric},
}
```

## Release Checklist

- [x] ~~Add BrainScape repository link~~
- [x] ~~Add BrainScape paper citation~~
- [x] ~~Add medmetric repository link~~
- [ ] Add WFDM paper/preprint link
- [ ] Add WFDM source-code repository link
- [ ] Add source-code release tag or commit hash
- [ ] Add WFDM checkpoint link
- [ ] Add WF-SA-VAE compressor checkpoint link
- [ ] Add checkpoint checksums
- [ ] Add minimal inference example using released checkpoints
- [ ] Add lightweight Python inference-package link, if released
- [ ] Add final WFDM citation
- [ ] Add license information


## License

Linked resources may have their own licenses and usage conditions. Users are responsible for following the licenses of BrainScape, medmetric, WFDM checkpoints, source datasets, and any external baseline generators or dependencies.

## Contact

For questions about this project, please open an issue in the relevant linked repositories.
