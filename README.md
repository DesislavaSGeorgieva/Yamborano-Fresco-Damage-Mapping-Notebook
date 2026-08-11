🖼️ Recovering the Unrecoverable — Yamborano Fresco Damage Mapping Notebook

A computational research companion to the article
Recovering the Unrecoverable: Documenting and Interpreting a Vanishing Bulgarian National Revival Fresco Cycle

This repository contains the computational notebook, source photograph, quantitative results, and selected visual outputs supporting the computer-vision analysis of visible surface loss in the Yamborano fresco cycle.

📁 Repository Structure
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
📂 Contents
data/ — source photographic material used in the computational analysis.
outputs/ — selected visual and quantitative results produced by the notebook.
Recovering_the_Unrecoverable_Yamborano_Fresco_Damage_Mapping_Notebook.ipynb — complete computational research workflow.
requirements.txt — Python dependencies required to run the notebook.
LICENSE — MIT License.
CITATION.cff — machine-readable citation metadata.
README.md — documentation of the research companion.
🏛️ Research Context

The Yamborano fresco cycle is a previously unpublished nineteenth-century Bulgarian National Revival mural ensemble in the Church of the Dormition of the Mother of God, Yamborano, Kyustendil province, Bulgaria.

Photographed by the author in 2005, the cycle was already in an advanced state of material deterioration, with extensive areas of painted surface lost and exposed plaster visible across the four surviving photographic compartments.

The accompanying research article provides the art-historical identification and interpretation of the cycle. This notebook complements that research by applying computational image analysis to the photographic record in order to quantify the visible extent of surface loss.

🔬 Computational Method

The notebook implements a transparent computer-vision workflow using classical image-processing techniques in Python.

The workflow comprises:

Image preparation → Scene separation → Colour-space analysis → Segmentation → Morphological processing → Visual verification → Quantification → Graphical analysis

A central methodological difficulty is the spectral overlap between exposed plaster and preserved light-coloured pictorial elements. White garments, halos, facial highlights, architectural details, flesh tones, and other illuminated passages can exhibit visual characteristics similar to the exposed substrate.

Several alternative approaches were therefore tested, including:

Global brightness and grayscale thresholding
Global RGB thresholding
HSV colour thresholding
CIE Lab colour-distance analysis
Fixed binary thresholds
Morphological refinement
Unsupervised K-Means colour clustering
Edge-based segmentation
Supervised deep-learning approaches

The notebook documents the methodological reasons why these approaches were insufficient for the present case study.

The final procedure employs scene-specific segmentation, with thresholds and spatial constraints adjusted individually for the four compositions, followed by manual visual verification.

🖼️ Per-Scene Segmentation Results

The following image presents the detected surface-loss overlays and corresponding binary masks for the four analysed scenes.

📊 Quantitative Results
Scene	Detected Surface Loss
The Transfiguration	31.21%
The Ascension	32.43%
Pentecost	0.75%
The Entry into Jerusalem	2.60%
Overall	16.66%

The overall value is calculated from the combined number of pixels classified as detected surface loss relative to the total number of analysed pixels across the four scene regions.

The quantitative results represent computational estimates of detected surface loss within the analysed photographic regions, rather than conservation-grade measurements of physically lost material.

⚠️ Interpretation and Limitations

Visual inspection of the generated masks shows that the segmentation procedure does not capture every visually identifiable area of surface loss.

This limitation is particularly apparent where exposed plaster exhibits visual characteristics similar to preserved pictorial elements. It is especially noticeable in The Entry into Jerusalem, where some apparent areas of paint loss remain undetected.

These omissions represent false-negative segmentation results and demonstrate the difficulty of separating exposed plaster from preserved light-coloured pictorial passages using image characteristics alone.

The reported percentages should therefore be interpreted as conservative computational estimates of detected surface loss within the analysed image regions.

They should not be interpreted as exhaustive reconstructions of all physically lost material or as conservation-grade condition assessments.

🔁 Reproducibility

The notebook provides a transparent computational workflow in which the image-processing procedures, scene-specific segmentation decisions, quantitative calculations, and graphical outputs can be inspected and reproduced.

The analysis is based on the photographic record made by the author in 2005. The condition represented in that photograph may itself already reflect an earlier stage of deterioration, and subsequent physical changes to the monument fall outside the scope of this analysis.

🧰 Software and Dependencies

The notebook uses open-source Python libraries for image processing, numerical analysis, data handling, visualization, and interactive notebook functionality.

The requirements.txt file contains the following dependencies:

opencv-python
numpy
pandas
matplotlib
Pillow
ipywidgets
jupyter
ipykernel

The notebook was developed in a Python 3 / Jupyter environment.

🎨 Relation to Art-Historical Research

The computational workflow is intended to complement rather than replace traditional art-historical inquiry.

Computer vision is used as an analytical instrument for observing, documenting, comparing, and quantifying visual phenomena that may otherwise remain difficult to describe systematically.

The computational analysis does not reconstruct missing imagery and does not substitute computational inference for historical, iconographic, stylistic, or material evidence.

The project demonstrates how computational methods can extend the analytical possibilities of art history while remaining grounded in close visual observation and historical knowledge.

📚 Accompanying Article

This notebook accompanies:

Recovering the Unrecoverable: Documenting and Interpreting a Vanishing Bulgarian National Revival Fresco Cycle

The article provides the art-historical context, iconographic identification, stylistic interpretation, and broader methodological argument within which the computational damage mapping is situated.

🗂️ Output Files
per_scene_masks.png

A visual summary of the scene-specific segmentation results, showing the detected surface-loss regions and corresponding binary masks for the four analysed scenes.

yamborano_surface_loss_quantification.csv

A machine-readable table containing the quantitative results of the scene-level surface-loss analysis.

📷 Source Image

data/yamborano_fresco.jpg contains the photographic record of the Yamborano fresco cycle used as the source image for the computational analysis.

The photograph was taken by the author in 2005 in the Church of the Dormition of the Mother of God, Yamborano, Kyustendil province, Bulgaria.

Permission to photograph the mural painting was granted by the local representatives of the Bulgarian Orthodox Church.

👩‍🎨 Author

Desislava S. Georgieva, PhD in Art History

Independent Researcher
PhD Alumna, National Academy of Arts, Sofia, Bulgaria

Research interests: Art History · Digital Art History · Computer Vision · Cultural Heritage Documentation

📖 Citation

If you use this notebook, its methodology, code, or quantitative results in your research, please cite the archived version of the repository.

Citation metadata are provided in CITATION.cff.

📜 License

This repository is released under the MIT License.

Copyright © 2026 Desislava S. Georgieva, PhD in Art History.

⭐ This repository is intended as a transparent computational companion to the art-historical documentation of a mural cycle at risk of disappearing from the historical record.
