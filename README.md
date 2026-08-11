# Generative MRI

Public gateway for our brain MRI synthesis and modality-completion research, linking the associated papers, data workflows, reusable software, experiment code, model releases, and evaluation resources.

> This repository is a landing page. Study-specific code, reusable software, model checkpoints, and dataset workflows are maintained in the linked resources.

## Resource Map

| Resource | Role | Availability |
| --- | --- | --- |
| BrainScape | Dataset integration and preprocessing framework used to reconstruct the study datasets from public MRI sources. | [GitHub](https://github.com/yasinzaii/BrainScape) · [Paper](https://doi.org/10.1162/IMAG.a.944) |
| WFDM | Cohort-level multimodal brain MRI synthesis using target-modality and metadata conditioning. | [arXiv](https://arxiv.org/abs/2606.00689) · [arXiv DOI](https://doi.org/10.48550/arXiv.2606.00689) |
| C-WFDM | Same-subject multimodal MRI translation and completion using ControlNet-guided image conditioning. | Manuscript in preparation |
| BrainMint | Reusable Python components for brain MRI synthesis, compression, conditioning, translation, inference, and evaluation. | [GitHub](https://github.com/yasinzaii/brainmint) · [PyPI](https://pypi.org/project/brainmint/) |
| medmetric | Metric implementations for evaluating synthetic 3D medical images. | [GitHub](https://github.com/yasinzaii/medmetric) · [PyPI](https://pypi.org/project/medmetric/) |
| Experiment workflows | Study-specific training, sampling, evaluation, configuration, and reproducibility workflows. | [brain-mri-synthesis](https://github.com/yasinzaii/brain-mri-synthesis) |

Reusable library code is maintained in BrainMint, while exact study configurations and experiment workflows are maintained in brain-mri-synthesis.

## Research

### BrainScape

**BrainScape: An open-source framework for integrating and preprocessing anatomical MRI datasets**

BrainScape is an open-source framework and curated resource for downloading, integrating, preprocessing, and organizing public anatomical MRI datasets.

The published BrainScape release contains **160 public datasets, 27,227 subjects, and 46,583 MRI scans** after quality control across `T1w`, `T2w`, `T1Gd` / `T1ce`, and `FLAIR` MRI.

- Repository: https://github.com/yasinzaii/BrainScape
- Paper: https://doi.org/10.1162/IMAG.a.944

### WFDM

**Wavelet-Fusion Diffusion Model for Multimodal Brain MRI Synthesis with Modality and Metadata Conditioning**

WFDM is a conditional 3D latent diffusion framework for cohort-level multimodal brain MRI synthesis. It combines a Wavelet-Fusion VAE compressor with a conditional 3D diffusion model and conditions generation on the requested MRI modality and available demographic and clinical metadata.

- Preprint: https://arxiv.org/abs/2606.00689
- arXiv DOI: https://doi.org/10.48550/arXiv.2606.00689

### C-WFDM

**C-WFDM: ControlNet-Guided Wavelet-Fusion Diffusion Model for Multimodal Brain MRI Translation and Completion**

C-WFDM extends the BrainScape-trained WFDM backbone from cohort-level synthesis to same-subject multimodal MRI translation and missing-modality completion using ControlNet-guided image conditioning.

**Status:** manuscript in preparation. A public manuscript link and citation will be added when available.

## Data

WFDM and C-WFDM use the same fixed earlier BrainScape study snapshot containing **157 datasets and 45,880 preprocessed MRI scans** across `T1w`, `T2w`, `T1Gd` / `T1ce`, and `FLAIR`.

This differs slightly from the final published BrainScape release, which contains **160 datasets, 27,227 subjects, and 46,583 scans** after quality control.

BrainScape does not redistribute preprocessed derivatives. Its public framework and dataset-specific configurations allow researchers to reconstruct the study data from the original public sources while retaining the access conditions and licensing requirements of those sources.

## Evaluation

Evaluation is study-specific.

**WFDM** evaluates synthetic MRI distributional alignment using MedicalNet feature-space Fréchet distance (FID) and Maximum Mean Discrepancy (MMD), with MS-SSIM between generated samples used as a diversity proxy. The compressor evaluation additionally reports LPIPS, SSIM, MS-SSIM, PSNR, and MSE. The FID, MMD, and MS-SSIM evaluation workflow uses [medmetric](https://github.com/yasinzaii/medmetric).

**C-WFDM** evaluates same-subject modality completion using paired SSIM, PSNR, and MAE, together with inference-efficiency measurements. The C-WFDM evaluation description will be updated when the manuscript and experiment workflows are publicly released.

## Model Releases

| Study | Planned model assets |
| --- | --- |
| WFDM | WF-SA-VAE compressor checkpoint and WFDM generator checkpoint |
| C-WFDM | Target-specific ControlNet adapter checkpoints for T2w, FLAIR, and T1Gd, together with references to the required WFDM backbone |

Released model assets will include matching configurations, checksums, and loading or inference instructions.

## Release Status

| Study | Manuscript | Experiment workflows | Model weights |
| --- | --- | --- | --- |
| WFDM | [Preprint available](https://arxiv.org/abs/2606.00689) | Planned | Planned |
| C-WFDM | In preparation | Planned | Planned |

## Citation

Please cite the paper corresponding to the study you use. Cite BrainScape, BrainMint, and medmetric when directly using those resources.

### Papers

#### BrainScape

```bibtex
@article{Yasinzai-BrainScape-2025,
  title     = {BrainScape: An open-source framework for integrating and preprocessing anatomical MRI datasets},
  author    = {Yasinzai, Muhammad Nabi and Mito, Remika and Pedersen, Mangor},
  journal   = {Imaging Neuroscience},
  volume    = {3},
  pages     = {IMAG.a.944},
  year      = {2025},
  publisher = {MIT Press},
  doi       = {10.1162/IMAG.a.944},
  url       = {https://direct.mit.edu/imag/article/doi/10.1162/IMAG.a.944/133386}
}
```

#### WFDM

```bibtex
@misc{Yasinzai-WFDM-2026,
  title         = {Wavelet-Fusion Diffusion Model for Multimodal Brain MRI Synthesis with Modality and Metadata Conditioning},
  author        = {Yasinzai, Muhammad Nabi and Mito, Remika and Pedersen, Mangor},
  year          = {2026},
  eprint        = {2606.00689},
  archivePrefix = {arXiv},
  primaryClass  = {cs.CV},
  doi           = {10.48550/arXiv.2606.00689},
  url           = {https://arxiv.org/abs/2606.00689}
}
```

#### C-WFDM

Citation will be added when the manuscript is publicly available.

### Software

#### BrainMint

```bibtex
@software{Yasinzai-BrainMint-2026,
  title   = {BrainMint: Brain MRI synthesis, compression, modality translation, and evaluation toolkit},
  author  = {Yasinzai, Muhammad Nabi},
  year    = {2026},
  version = {0.1.0},
  url     = {https://github.com/yasinzaii/brainmint/tree/v0.1.0}
}
```

#### medmetric

```bibtex
@software{Yasinzai-MedMetric-2025,
  title   = {medmetric: Medical image synthesis metrics with MedicalNet feature extraction},
  author  = {Yasinzai, Muhammad Nabi},
  year    = {2025},
  version = {0.1.1},
  url     = {https://github.com/yasinzaii/medmetric/tree/v0.1.1}
}
```

## License

Licensing is resource-specific. Please refer to each linked repository or model release for its applicable license and usage conditions. Source MRI datasets remain subject to the access conditions and licenses of their original repositories.

## Contact

For questions about a specific study or software component, please open an issue in the relevant linked repository.
