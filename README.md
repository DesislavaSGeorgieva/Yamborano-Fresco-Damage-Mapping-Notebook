# Recovering the Unrecoverable — Yamborano Fresco Damage Mapping Notebook

A computational research companion to the article **“Recovering the Unrecoverable: Documenting and Interpreting a Vanishing Bulgarian National Revival Fresco Cycle.”**

This repository contains the computational notebook, source image, quantitative results, and selected visual output supporting the computer-vision analysis of visible surface loss in the Yamborano fresco cycle.

## Repository Structure

```text
.
├── data/
│   └── yamborano_fresco.jpg
├── outputs/
│   ├── per_scene_masks.png
│   └── yamborano_surface_loss_quantification.csv
├── Recovering_the_Unrecoverable_Yamborano_Fresco_Damage_Mapping_Notebook.ipynb
├── requirements.txt
├── LICENSE
├── CITATION.cff
└── README.md
```

## Research Context

The Yamborano fresco cycle is a previously unpublished example of Bulgarian National Revival ecclesiastical painting in the Church of the Dormition of the Mother of God, Yamborano, Kyustendil province, Bulgaria.

Severe paint loss affects substantial portions of the cycle, making direct visual interpretation difficult. The computational analysis was developed to move beyond a purely impressionistic assessment of damage and to provide a quantitative description of the surface loss visible in the photographic record made by the author in 2005.

The notebook accompanies the article:

Recovering the Unrecoverable: Documenting and Interpreting a Vanishing Bulgarian National Revival Fresco Cycle

and provides the computational methodology underlying the quantitative estimates reported in the study.

## Computational Approach

The analysis uses classical computer-vision techniques implemented in Python.

The workflow includes:

- image preparation;
- scene-specific cropping;
- colour-based segmentation;
- morphological processing;
- binary mask generation;
- visual inspection;
- quantitative calculation of detected surface loss; and
- graphical visualization of the results.

A major methodological difficulty is the visual similarity between exposed plaster and preserved light-coloured pictorial elements, including white garments, halos, facial highlights, and other illuminated passages.

No single global segmentation rule produced satisfactory results across all four scenes. The final procedure therefore uses scene-specific segmentation, with thresholds and spatial constraints adjusted according to the visual and chromatic characteristics of each composition, followed by manual visual verification.

The notebook also documents the alternative computer-vision approaches tested during methodological development and their failure modes in this particular case. These experiments record the trial-and-error process through which the final scene-specific strategy was established.

## Quantitative Results

The final analysis produced the following estimates of detected surface loss within the analysed regions:

| Scene                             | Detected surface loss |
| --------------------------------- | --------------------: |
| The Transfiguration               |                31.21% |
| The Ascension                     |                32.43% |
| Pentecost                         |                 0.75% |
| The Entry into Jerusalem          |                 2.60% |
| **Overall detected surface loss** |            **16.66%** |

These values represent computational estimates of detected surface loss within the analysed photographic regions, rather than conservation-grade measurements of the physical condition of the murals.

The segmentation masks do not capture every visually identifiable area of surface loss. In particular, false-negative results occur where exposed plaster has visual characteristics similar to preserved pictorial elements. The reported percentages should therefore be interpreted as conservative computational estimates of the surface loss detected by the implemented procedure.

## Per-Scene Segmentation

The following visualization presents the detected surface-loss overlays and corresponding binary masks for the four analysed scenes.

## Reproducibility and Interpretation

The notebook is intended as a transparent and reproducible computational research companion to the accompanying art-historical study.

The workflow records the image-processing procedures, scene-specific segmentation decisions, quantitative calculations, and visual outputs used to obtain the reported estimates.

Reproducibility in this context does not imply that the computational segmentation constitutes an exhaustive or conservation-grade reconstruction of physical paint loss. The analysis quantifies the surface loss detected in the available photographic record using the implemented image-processing procedure.

The source photograph represents the condition of the mural as documented in 2005 and may itself already represent a stage of deterioration. Subsequent physical changes to the monument are outside the scope of the present computational analysis.

## Relation to the Accompanying Research

The notebook is designed to complement, rather than replace, traditional art-historical and conservation approaches.

The computational analysis provides a quantitative description of visible surface loss, while the accompanying article addresses the art-historical identification of the mural cycle, its iconographic and stylistic context, and the broader implications of documenting a severely damaged monument through a combination of traditional art-historical research and computational methods.

Computer vision is used here as an analytical instrument within art-historical research. It does not reconstruct missing imagery or substitute computational inference for direct historical or material evidence.

## Data and Image Rights

The source photograph analysed in this repository was taken by the author in 2005 in the Church of the Dormition of the Mother of God, Yamborano, Kyustendil province, Bulgaria.

Permission to photograph the church interior was obtained from the local representatives of the Bulgarian Orthodox Church.

## Software

The computational workflow is implemented in Python using open-source scientific and computer-vision libraries. The computational environment and package dependencies are documented in requirements.txt.

## Author

Desislava S. Georgieva, PhD in Art History

Independent Researcher

## Citation

If you use this notebook, its code, methodology, or quantitative results in your research, please cite the archived version of this repository.

Citation metadata are provided in CITATION.cff.

## License

The code and associated software materials in this repository are released under the MIT License.

Copyright © 2026 Desislava S. Georgieva, PhD in Art History.
