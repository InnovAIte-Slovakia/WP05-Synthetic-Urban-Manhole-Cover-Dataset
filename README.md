# Synthetic Urban Manhole Cover Dataset

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.21291309.svg)](https://doi.org/10.5281/zenodo.21291309)
[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)

A synthetic multi-camera urban street dataset for detecting and segmenting **open and closed manhole covers**.

The dataset is hosted on Zenodo: **https://zenodo.org/records/21291309**

## Overview

The dataset provides varied camera viewpoints, lighting, weather, and road-surface conditions (dry and wet asphalt, cobblestone pavement, puddles after rainfall). For every frame it includes a photorealistic rendered RGB image, a semantic class mask, an instance mask, an RGB segmentation map, and bounding-box annotations generated from the masks.

| | |
| --- | --- |
| Version | 1.0.0 |
| Camera folders | 12 (`cam01` – `cam12`) |
| RGB frames | 1,184 (+ 199 brightness-adjusted frames in `ImgsNew` for `cam03` and `cam11`) |
| Resolution | 1920 × 1080 |
| Bounding-box annotations | 120,264 |
| Splits (camera-disjoint) | train: 794 frames (`cam01`–`cam08`), val: 191 (`cam09`–`cam10`), test: 199 (`cam11`–`cam12`) |

The ratio of open to closed manholes is approximately **50:50** at the generated scenario level; per-frame counts may differ due to viewpoint, occlusion, and truncation.

### Semantic classes

| ID | Class |
| ---: | --- |
| 0 | `background_or_unlabeled` |
| 1 | `road` |
| 2 | `open_manhole` |
| 3 | `closed_manhole` |
| 4 | `cars` |
| 5 | `traffic_signs` |
| 6 | `sidewalks` |
| 7 | `buildings` |
| 8 | `props` |
| 9 | `vegetation` |

## Structure

Each camera folder (`camXX.zip` on Zenodo) contains:

- `Imgs/ImgXXXX.png` – rendered RGB image
- `ClassID/SegmClassIDXXXX.png` – per-pixel semantic class ID
- `InstID/SegmInstIDXXXX.png` – per-pixel object instance ID
- `Segm/SegmRGBXXXX.png` – RGB segmentation map (unique color per class/instance combination)
- `Bboxes/SegmInstIDXXXX.txt` – bounding boxes, one per line:

  ```
  <class_name> <instance_id> <xmin> <ymin> <xmax> <ymax>
  ```

  Coordinates are normalized to `[0, 1]`, with the origin in the top-left image corner.

The record also includes metadata and helper files: `manifest.csv`, `classes.json`, `dataset_metadata.json`, `splits.zip`, `checksums.sha256`, `ANNOTATION_SCHEMA.md`, `DATASET_REPORT.md`, `CHANGELOG.md`, and the utility scripts `batch_masks_to_bboxes.py` and `show_bboxes_over_objects.py` (with `requirements.txt`).

See the README, `ANNOTATION_SCHEMA.md`, and `DATASET_REPORT.md` on Zenodo for full details, including the list of known missing frames.

## Download

Download individual files from the Zenodo record, e.g.:

```bash
wget "https://zenodo.org/records/21291309/files/cam01.zip?download=1" -O cam01.zip
```

The total size of all camera archives is approximately 14 GB.

## Project context

The data was created by VSB-TUO, IT4Innovations within the project InnovAIte Slovakia (call 09I02-03-V2 Transformation and Innovation Consortia), Work Package 5 "AI-Video driven Building and Road Safety: Guarding the Future", task T5.3 "Development of the 3D virtual environments, generation of synthetic datasets", as part of milestone M5.1 "Synthetic datasets - #1".

Funded by the European Union – NextGenerationEU through the Recovery and Resilience Plan for Slovakia.

## License

The dataset is released under the [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/) license.

You may use, share, and adapt the dataset for any purpose, including commercial, as long as you give appropriate credit.

## Citation

```bibtex
@dataset{strakos_2026_synthetic_manhole,
  author    = {Strakos, Petr and Zurkova, Leona and Topic, Daniel},
  title     = {Synthetic Urban Manhole Cover Dataset},
  year      = {2026},
  version   = {1.0.0},
  publisher = {Zenodo},
  doi       = {10.5281/zenodo.21291309},
  url       = {https://doi.org/10.5281/zenodo.21291309}
}
```

Authors: Petr Strakos, Leona Zurkova, Daniel Topic – IT4Innovations, VSB – Technical University of Ostrava.
