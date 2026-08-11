# Recovering the Unrecoverable — Yamborano Fresco Damage Mapping Notebook

**Author:** Desislava S. Georgieva, PhD in Art History  
**Status:** Independent Researcher  
**Year:** 2026

This repository contains the computational research notebook accompanying the article *Recovering the Unrecoverable: Documenting and Interpreting a Vanishing Bulgarian National Revival Fresco Cycle*.

The notebook documents and quantitatively analyses visible surface loss in a nineteenth-century Bulgarian National Revival fresco cycle preserved in the Church of the Dormition of the Mother of God in the village of Yamborano, Kyustendil province, Bulgaria.

The computational analysis is based on an archival photograph taken by the author in 2005.

![Per-scene segmentation results](outputs/per_scene_masks.png)

## Research objective

The principal objective of this notebook is to provide a transparent and reproducible computational estimate of visible surface loss within the four analysed scenes of the mural cycle.

The workflow distinguishes between two visually observable categories:

- preserved painted surface;
- exposed plaster interpreted as visible surface loss.

The analysis does not attempt to reconstruct missing painting, diagnose conservation conditions, or replace direct physical examination of the mural.

Instead, it uses computational image analysis to transform the visible evidence preserved in the archival photograph into scene-level and aggregate quantitative measurements.

## Computational workflow

The notebook documents a complete workflow consisting of:

1. preparation of the archival photograph;
2. identification and separation of the four analysed scenes;
3. image preprocessing and colour-space transformation;
4. development and evaluation of alternative segmentation approaches;
5. scene-specific segmentation of visible surface loss;
6. visual inspection and verification of the resulting masks;
7. calculation of detected surface loss for each scene;
8. calculation of aggregate detected surface loss across the four analysed scene regions;
9. graphical visualisation of the quantitative results.

The workflow is designed to make the computational decisions, intermediate results and limitations of the analysis explicitly inspectable.

## Development of the segmentation strategy

The mural presents a particularly difficult segmentation problem because exposed plaster shares visual characteristics with preserved light-coloured pictorial elements.

This spectral overlap is especially evident in white garments, halos, facial highlights, flesh tones, architectural details and other illuminated passages. Consequently, both false-positive and false-negative classifications can occur when image characteristics alone are used to distinguish exposed plaster from preserved painting.

During methodological development, several computer-vision approaches were implemented and evaluated:

### Global brightness and grayscale thresholding

Global brightness and luminance thresholding frequently classified preserved light-coloured pictorial elements as surface loss, while darker or unevenly illuminated areas of exposed plaster could remain undetected.

### Global RGB thresholding

RGB thresholding produced substantial overlap between exposed plaster and preserved pale pictorial elements, resulting in over-segmentation in several areas.

### HSV colour thresholding

HSV-based segmentation allowed saturation and brightness to be considered separately, but preserved white and pale pictorial elements continued to overlap with exposed plaster in colour space. No single parameter combination provided consistent results across all four scenes.

### CIE Lab colour-distance analysis

A colour-distance approach based on a representative plaster colour was also evaluated. It failed to account adequately for the non-uniform appearance of exposed plaster caused by deterioration, staining, surface deposits, uneven illumination and local material variation.

### Fixed binary thresholds

Different fixed threshold combinations were tested. Their performance varied substantially between scenes because illumination, pigment appearance and plaster characteristics were not uniform throughout the mural cycle.

### Morphological refinement

Morphological opening and closing operations were tested to remove isolated pixels and improve the coherence of segmentation regions. Although useful for post-processing, morphology could not correct the fundamental classification errors introduced by an unsuitable preceding segmentation step.

### Unsupervised K-Means clustering

K-Means colour clustering provided partial separation in some areas but operated primarily on spectral similarity without sufficient spatial or semantic information. Preserved light-coloured elements were therefore frequently grouped together with exposed plaster.

### Edge-based segmentation

Canny and related gradient-based approaches were affected by the large number of high-frequency structures present in the historical photograph, including craquelure, cracks, painted contour lines, figures and architectural details. Detected edges therefore did not correspond consistently to the boundaries of surface loss.

### Supervised deep-learning approaches

Supervised segmentation approaches, including U-Net-type architectures, were considered but were not adopted because the case study is based on a single archival photograph and does not provide a sufficiently large, diverse and independently annotated training dataset. Under these conditions, a supervised model would be highly susceptible to overfitting to the particular image and its illumination and visual characteristics.

## Final segmentation strategy

The experiments demonstrated that no single fully automatic segmentation technique provided sufficiently reliable results for every scene.

The final workflow therefore uses **scene-specific segmentation**.

The four compositions are analysed individually, with thresholds and spatial constraints adjusted according to their respective visual and chromatic characteristics, followed by manual visual verification.

The final procedure combines:

- Gaussian smoothing;
- conversion to the CIE Lab colour space;
- threshold-based segmentation;
- scene-specific parameters;
- manually defined regions of interest and protective masks where required;
- morphological refinement.

Otsu thresholding is used for *The Transfiguration* and *The Ascension*, while fixed thresholds combined with manually defined spatial constraints are used for *Pentecost* and *The Entry into Jerusalem*.

This approach was adopted because the visual characteristics of exposed plaster vary substantially between scenes and cannot be represented adequately by a single global segmentation rule.

## Quantitative results

The final workflow produced the following estimates of detected surface loss within the analysed scene regions:

| Scene | Detected surface loss |
|---|---:|
| *The Transfiguration* | 31.21% |
| *The Ascension* | 32.43% |
| *Pentecost* | 0.75% |
| *The Entry into Jerusalem* | 2.60% |
| **Overall detected surface loss** | **16.66%** |

The overall value is calculated from the total number of detected surface-loss pixels relative to the total number of analysed pixels across the four scene regions. It is therefore not the arithmetic mean of the four scene-level percentages.

The quantitative results are estimates of **detected** surface loss within the analysed image regions. They should not be interpreted as conservation-grade measurements of physically lost material.

## Limitations

The analysis is based on a single archival photograph and therefore reflects only the visual information preserved in that photographic record.

The segmentation procedure does not capture every visually identifiable area of surface loss. This limitation is particularly apparent where exposed plaster exhibits visual characteristics similar to those of preserved pictorial elements.

The resulting masks may therefore contain both false-positive and false-negative classifications.

The reported percentages should consequently be understood as conservative computational estimates of the surface loss detected by the implemented procedure within the analysed image regions.

The notebook does not attempt to reconstruct missing pictorial content or provide a conservation diagnosis. Direct physical examination of the mural would be required for such purposes.

## Repository structure

```text
.
├── data/
│   └── yamborano_fresco.jpg
│
├── notebook/
│   └── Recovering_the_Unrecoverable_Yamborano_Fresco_Damage_Mapping_Notebook.ipynb
│
├── outputs/
│   ├── per_scene_masks.png
│   └── yamborano_surface_loss_quantification.csv
│
├── requirements.txt
├── LICENSE
├── CITATION.cff
└── README.md
