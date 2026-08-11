# Recovering the Unrecoverable — Yamborano Fresco Damage Mapping Notebook

A computational research companion to the study of the nineteenth-century Bulgarian National Revival fresco cycle preserved in the former Church of St George in Yamborano.

This repository contains the Jupyter Notebook used to document and quantitatively analyse visible surface loss recorded in an archival photograph of the mural cycle.

The computational workflow is designed to complement art-historical and visual analysis by transforming selected observations of visible paint loss into transparent, reproducible numerical measurements.

## Research objective

The notebook addresses a specific methodological question:

**How can visible surface loss in a historical mural photograph be documented and quantitatively estimated using computational image analysis?**

The workflow distinguishes between:

* preserved painted surface;
* exposed plaster interpreted as visible surface loss.

The purpose is not to reconstruct missing painting or to provide a conservation-grade diagnosis. The analysis is limited to the visual information contained in the available photographic record.

## Methodological approach

The workflow consists of the following principal stages:

1. loading and preprocessing the archival photograph;
2. identifying the four analysed scenes of the mural cycle;
3. separating the scenes into individual image regions;
4. evaluating alternative image-segmentation approaches;
5. applying a scene-specific segmentation strategy;
6. visually inspecting the resulting binary masks and overlays;
7. calculating detected surface loss for each analysed scene;
8. calculating the aggregate detected surface loss across the four analysed scene regions;
9. visualising the quantitative results.

Several segmentation approaches were evaluated during methodological development, including RGB thresholding, HSV colour thresholding, fixed binary thresholds, morphological refinement and unsupervised K-Means colour clustering. These experiments demonstrated that no single fully automatic approach provided sufficiently reliable results across all four scenes.

The final procedure is therefore **scene-specific**. Thresholds and spatial constraints are adjusted according to the visual and chromatic characteristics of each composition, followed by manual visual verification.

For *The Transfiguration* and *The Ascension*, the final procedure uses Gaussian smoothing, conversion to the LAB colour space, Otsu thresholding and morphological opening. For *Pentecost* and *The Entry into Jerusalem*, fixed thresholds are combined with manually defined regions of interest and protective masks, followed by morphological refinement.

## Quantitative results

The final workflow produces the following detected surface-loss estimates within the analysed scene regions:

| Scene                             | Detected surface loss |
| --------------------------------- | --------------------: |
| *The Transfiguration*             |                31.21% |
| *The Ascension*                   |                32.43% |
| *Pentecost*                       |                 0.75% |
| *The Entry into Jerusalem*        |                 2.60% |
| **Overall detected surface loss** |            **16.66%** |

The aggregate value is calculated from the total number of pixels classified as surface loss relative to the total number of analysed pixels. It is therefore not the arithmetic mean of the four scene-level percentages.

These values should be interpreted as **computational estimates of detected surface loss within the analysed image regions**, rather than as direct measurements of physically lost material.

The segmentation masks do not capture every visually identifiable area of surface loss. This limitation is particularly apparent in scenes where exposed plaster has visual characteristics similar to preserved pictorial elements. The quantitative results should therefore be understood as conservative estimates of the surface loss detected by the implemented procedure.

## Repository structure

```text
.
├── data/
│   └── yamborano_fresco.jpg
├── notebook/
│   └── Recovering_the_Unrecoverable_Yamborano_Fresco_Damage_Mapping_Notebook.ipynb
├── outputs/
│   └── yamborano_surface_loss_quantification.csv
├── requirements.txt
├── LICENSE
├── CITATION.cff
└── README.md
```

### `data/`

Contains the archival source photograph used as the input for the computational analysis.

### `notebook/`

Contains the complete Jupyter Notebook documenting the computational workflow, methodological experiments, final segmentation procedure, visual inspection, quantitative analysis and graphical presentation of the results.

### `outputs/`

Contains the quantitative results generated from the final analysis.

### `requirements.txt`

Lists the Python packages required to reproduce the computational workflow.

### `LICENSE`

Specifies the terms under which the repository contents may be used.

### `CITATION.cff`

Provides structured citation information for the repository and enables GitHub's citation functionality.

## Reproducibility and interpretation

The notebook is intended as a transparent computational record of the analysis performed for this case study.

The results depend on the characteristics of the archival photograph, the manually defined scene regions and the scene-specific segmentation parameters. Consequently, the workflow should not be interpreted as a universally applicable automatic detector of mural-painting deterioration.

Instead, it provides a reproducible and inspectable framework that can be adapted and tested on other historical mural photographs.

## Relation to the accompanying research article

The notebook is a computational companion to the accompanying research article *Recovering the Unrecoverable*.

The article provides the broader art-historical, historical and visual interpretation of the Yamborano mural cycle, while this repository documents the computational procedures used to quantify visible surface loss from the archival photographic record.

The two outputs are therefore complementary: the article provides the interpretative context, while the notebook provides the computational evidence and reproducible image-analysis workflow underlying the quantitative component of the study.

## Software and technologies

The workflow uses open-source Python libraries, including:

* Python
* OpenCV
* NumPy
* Pandas
* Matplotlib
* ipywidgets

The computational environment and software dependencies are documented in `requirements.txt`.

## Limitations

The analysis is based on a single archival photograph and therefore reflects only the visual information preserved in that photographic record.

The segmentation procedure is not intended to reconstruct missing painting, diagnose conservation conditions, or replace direct physical examination of the mural.

Because the visual characteristics of exposed plaster overlap with those of some preserved light-coloured pictorial elements, the segmentation masks may contain both false-positive and false-negative classifications.

The reported percentages should consequently be treated as computational estimates of **detected** surface loss within the analysed image regions.

## License

See the [`LICENSE`](LICENSE) file for the applicable license.

## Citation

If you use this notebook, its code, or its quantitative results in your research, please cite the repository using the information provided in `CITATION.cff`.

A DOI will be added following archival of the release through the GitHub–Zenodo integration.
